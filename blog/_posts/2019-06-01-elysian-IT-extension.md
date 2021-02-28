---
layout: post
title: Elysian IT extension to integrate security hardened Windows image into Jenkins pipeline and assist with Azure migration
image: /assets/img/Jenkins-CD.png
description: >
  In March 2019 MPFE Consultancy were engaged by Elysian IT to further support the project with their Financial Technology client and to contribute to a separate Azure migration project. During this engagement we worked with Jenkins, Gradle, AWS and Azure.
sitemap: false
hide_last_modified: true
author: mark
---

In March 2019 MPFE were engaged by Elysian IT for a further 3 month period as part of a second phase for their Financial Technology client. We also provided assistance with an Azure migration, developing an Azure blueprint, ARM (Azure Resource Manager) templates and PowerShell scripts to deploy the infrastructure for a new customer cloud environment.

As part of the Financial Technology client engagement MPFE worked to understand the clients build and deployment strategy for the product utilizing the secure Windows Server 2016 image we developed in the previous engagement. We then worked with the end client to modify their Jenkins and Gradle scripts in order to implement the new image and ensure the product stack was successfully deployed. At the end of the engagement we travelled to the FT clients office in Germany and worked with them for 3 days to handover the solution.

In addition MPFE provided assistance with a separate Azure migration project. We created an Azure blueprint and ARM templates to deploy infrastructure and Virtual Machines and to secure and configure the Azure subscription. We then created PowerShell scripts that could be used to trigger deployments and infrastructure updates and also created a Proof of Concept for ARM template deployments via Azure DevOps pipelines, a solution being considered for the future.

## Technologies

### Jenkins

> Jenkins is a widely used automation server product used to build, test, and deploy software.
### Gradle

> Gradle is an open source build and automation tool that runs on JVM (Java Virtual Machine).

### AWS

> AWS (Amazon Web Services) is Amazon's cloud service, with a global presence and over 200 services that can be leveraged to create simple and complex infrastructure that is automated, scalable, and cost effective. 
### Azure

> Azure is Microsoft's cloud service. Similar to AWS it also has over 200 services and can be leveraged to build a variety of infrastructure that can be scaled to meet demand. Azure also offers tight integration with other Microsoft technologies such as Active Directory, SQL Server and Windows Server.