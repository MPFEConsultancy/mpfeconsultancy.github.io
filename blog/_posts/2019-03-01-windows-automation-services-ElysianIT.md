---
layout: post
title: Providing Windows Automation services for Elysian IT
description: >
  In November 2018 MPFE Consultancy were engaged by Elysian IT to provide Windows Automation services in support of a fixed term project they had with a major Financial Technology client. This post described that engagement and the services we were able to provide in order to successfully deliver the clients requirements on time.
sitemap: false
hide_last_modified: true
author: mark
---

In November 2018 MPFE Consultancy were engaged by [Elysian IT](https://www.elysianit.com/) who were in need of some additional Windows automation resource as part of a project they had with a major Financial Technology client. MPFE were engaged to automate the routine creation of a security hardened Windows 2016 Server image in AWS. The image needed to be configured per the CIS (Center for Internet Security) Benchmark for Windows Server.

To meet the requirement MPFE created a PowerShell DSC (Desired State Configuration) script to configure each of the settings specified in the CIS benchmark for Windows Server 2016. We then developed a Pester test script that would be run after the DSC script had completed to validate that each of the security settings were successfully applied. Finally we modified the customers Packer template and performed end to end testing to confirm the image was successfully created and configured and was deployable and usable by the intended product. 
