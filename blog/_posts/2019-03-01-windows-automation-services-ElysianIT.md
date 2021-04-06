---
layout: post
title: Working with Elysian IT to configure a security hardened Windows Server VM Image in AWS
image: /assets/img/DSC-Push.png
description: >
  In November 2018 MPFE Consultancy were engaged by Elysian IT to provide Windows Automation services in support of a fixed term project they had with a major Financial Technology client. This post describes that engagement and the technology we implemented together to successfully deliver the requirement on time.
sitemap: false
hide_last_modified: true
author: mark
---

In November 2018 MPFE Consultancy were engaged by [Elysian IT](https://www.elysianit.com/) who were in need of some additional Windows automation resource as part of a project they had with a major Financial Technology client. MPFE worked with Elysian IT to automate the routine creation of a security hardened Windows Server 2016 image in AWS. The image needed to be configured per the [CIS](https://www.cisecurity.org/cis-benchmarks/) (Center for Internet Security) Benchmark for Windows Server.

To meet the requirement MPFE created a PowerShell DSC (Desired State Configuration) script to configure each of the settings specified in the CIS benchmark for Windows Server 2016. We then developed a Pester test script that would be run after the DSC script had completed to validate that each of the security settings were successfully applied. Finally we modified the customers Packer template and performed end to end testing to confirm the image was successfully created and configured and was deployable and usable by the intended customer product. 

## Technologies

### PowerShell DSC

> Desired State Configuration (DSC) is a feature of PowerShell that provides a way to automatically configure Windows and Linux Operating Systems. You define one or more declarative configurations that specify settings that should be present or absent on a system and then the Local Configuration Manager (LCM) makes the required changes to ensure the system is aligned with the specification defined in your configuration.

DSC was a good choice for this project because its built in to Windows Server 2016 so requires no additional software or agent to be bootstrapped on to the machine. It was also a good choice for readability and ongoing maintenance of the security configuration because each security item is explicitly defined and easy to cross reference to the specific CIS benchmark item it satisfies.

### Pester

> Pester is the PowerShell testing framework. It's primary intent is for unit testing code, but it can also be leveraged to perform infrastructure or configuration testing. You create a Pester script which specifies each item you want to evaluate in an english-like way and Pester then performs the evaluations and creates an easy to review output.

While it shouldn't be strictly necessary to test the outcome of a DSC script because failures to apply configuration should be reported when DSC runs, the output of DSC can be very verbose. The Pester output allows the client to more quickly and easily identify what configuration may be missing. It also worked well as a final validation in the pipeline to ensure that the generated image met the expected configuration specification.

### Packer

> Packer is a product by Hashicorp for automating the creation of machine images. You create a Packer script which defines the source image you want to customize followed by a series of tasks for how to customize it. You then identify how you want the customized image to be published.

Packer was already being leveraged by the client for this project and was a good choice because it can be very easily used to customize images from a number of sources, including AWS. Packer was implemented as part of this project as a wrapper around the other automation that was developed to pull the base Windows 2016 Server image from AWS, customise it via DSC and validate it with Pester before publishing the completed image into the customers private image store. Packer was also used to generalise Windows so that when the image is used to create VMs (Virtual Machines) they are unique.