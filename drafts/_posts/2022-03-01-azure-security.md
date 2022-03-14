---
layout: post
title: Azure Security
image: /assets/img/azure-security-center.png
description: >
  Cloud security is a shared responsibility between the cloud provider and you: the customer. It is important to consider security throughout the lifecycle of your cloud deployments. This article explores some of the security tools and capabilities that are available within the Microsoft Azure platform.
hide_last_modified: true
author: mark
---

It is important to consider security throughout the lifecycle of your cloud deployments. The Microsoft Azure platform provides tools and capabilities that can be leveraged to create secure solutions, but these must be carefully considered and deliberately implemented. Azure also provides a number of security services and plans that can be leveraged for additional cost to monitor and manage threats and vulnerabilities. New attack vectors are discovered every day and it is not unusual for hackers to breach systems weeks or months before they leverage their unauthorised access for malicious means. Maintaining your security in the cloud needs to be an ongoing and equally evolving process.

# Getting started

A good starting point when considering security in Azure is to review the [Introduction to Azure security](https://docs.microsoft.com/en-us/azure/security/fundamentals/overview) Microsoft documentation page.

At a high level, this encourages you to consider:

- What operating systems, programming languages, frameworks, tools, database technologies and devices are you leveraging (or planning to leverage) on Azure?
- How will you monitor, detect, and respond to threats within your cloud resources?
- How will you manage the deployment of resources and control, manage, and monitor changes to your cloud infrastructure and applications?
- How will you detect vulnerabilities in your cloud applications?
- How will you control access to your cloud storage?
- How will you limit access between specific devices and subnets and ensure that the minimum required access is enabled?
- How will you detect and block malicious software on your Virtual Machines or other compute services?
- How will you recover your service should malicious activity or disruption occur?
- How will you limit, monitor, and control access to your Azure resources and manage access to your applications?

# Monitoring

Azure provides a number of services that enable you to monitor and respond to security threats:

## Microsoft Sentinel

[Microsoft Sentinel](https://docs.microsoft.com/en-us/azure/sentinel/overview) is a security information and event management (SIEM) and security orchestration, automation and response (SOAR) solution. Sentinel collects data across all your uses, applications and infrastructure and can be leveraged both for on-premise resources and in multiple clouds. Using Microsoft's analytics and threat intelligence it can alert you to previously undetected threats and minimizes false positives. It utilizes Artificial Intelligence to hunt for suspicious activity, leveraging years of Microsoft's cyber security experience and expertise. Finally through built-in orchestration and automation of common tasks it enables you to respond to incidents rapidly, via your own custom [playbooks](https://docs.microsoft.com/en-us/azure/sentinel/tutorial-respond-threats-playbook).

![Microsoft Sentinel Dashboard](/assets/img/azure-sentinel-dashboard.png)

[Microsoft Sentinel pricing](https://azure.microsoft.com/en-gb/pricing/details/microsoft-sentinel/) is based on the amount of GBs of logs ingested. At time of writing, the cost in UK South is £1.89 per GB on the pay as you go tier. If you have a high level of daily logging, commitment tiers can be purchased to reduce the per GB cost. There is also a reduced cost for the ingestion of basic log types (which are often verbose but have a low amount of security data). Microsoft Sentinel can be tried free for 31 days.

## Microsoft Defender for Cloud

Previously known as Security Centre and Azure Defender, [Microsoft Defender for Cloud](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) uses a secure score to simplify your understanding of the security posture of your resources and to provide simple actionable recommendations to harden your environment. 

![Azure Defender for Cloud Dashboard](/assets/img/azure-defender-for-cloud-dashboard.png)

Microsoft Defender for Cloud is free, but it can also be augmented with additional plans for the following resource and technology types:

- Servers
- Storage
- SQL
- Containers
- App Service
- Key Vault
- Resource Manager
- DNS
- Open-source relational databases
- Cosmos DB

These plans enable additional security features such as endpoint protection, vulnerability scanning and the detection of suspicious or unusual activity.

## Application Insights

..

## Azure Monitor / Azure Monitor logs

..

## Azure Advisor

..

# Deployment

..

