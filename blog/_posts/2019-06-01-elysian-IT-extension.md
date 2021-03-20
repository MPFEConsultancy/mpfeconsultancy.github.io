---
layout: post
title: Elysian IT extension to integrate security hardened Windows image into Jenkins pipeline and assist with Azure migration
image: /assets/img/Jenkins-CD.png
description: >
  In March 2019 MPFE Consultancy were engaged by Elysian IT to further support the project with their Financial Technology client and to contribute to a separate Azure migration project. During this engagement we worked with Jenkins, Gradle and AWS CloudFormation templates as well as Azure Blueprints and ARM templates for the migration project.
sitemap: false
hide_last_modified: true
author: mark
---

In March 2019 MPFE were engaged by Elysian IT for a further 3 month period as part of a second phase for their Financial Technology client. We also provided assistance with an Azure migration, developing an Azure blueprint, ARM (Azure Resource Manager) templates and PowerShell scripts to deploy the infrastructure for a customer's new cloud environment.

As part of the Financial Technology client engagement MPFE worked to understand the clients complexbuild and deployment strategy for the product utilizing the secure Windows Server 2016 image we developed in the previous engagement. We then worked with the end client to modify their Jenkins and Gradle scripts in order to implement the new image and ensure the product stack was successfully deployed. At the end of the engagement we travelled to the FT clients office in Germany and worked with them for 3 days to handover the solution.

In addition MPFE provided assistance with a separate Azure migration project. We created an Azure blueprint and ARM templates to deploy infrastructure and Virtual Machines and to secure and configure the Azure subscription. We then created PowerShell scripts that could be used to trigger deployments and infrastructure updates and also created a Proof of Concept for ARM template deployments via Azure DevOps pipelines, a solution being considered for the future.

## Technologies

### Jenkins

> Jenkins is a widely used automation server product used to build, test, and deploy software. It can be used for CI (continuous integration) and CD (continuous deployment) and is highly extensible via plugins.



### Gradle

> Gradle is an open source build and automation tool that runs on JVM (Java Virtual Machine).



### AWS CloudFormation Templates

> CloudFormation allows infrastructure as code deployments to AWS. A CloudFormation template can be written as either JSON or YAML and describes the AWS resources you want to deploy. AWS then takes care of provisioning and configuring the resources, ensuring that the resultant state matches the definition of the template.



### ARM (Azure Resource Manager) Templates

> ARM templates are the infrastructure as code technology for Azure. An ARM template is written in JSON and describes the Azure resources you want to deploy. When a template is executed Azure ensures that the resultant state matches what is defined in the template.



### Azure Blueprint

> Azure Blueprint allows an engineer or architect to define a repeatable set of resources that adhere to an organisations standards, patterns and requirements. It allows Azure Roles Assignments, Policy Assignments, ARM Templates and Resource Groups to be defined via code.