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

Previously known as Security Centre and Azure Defender, [Microsoft Defender for Cloud](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) uses a secure score to simplify your understanding of the security posture of your resources and to provide simple actionable recommendations to harden your environment. Defender for Cloud generates security alerts which can be managed within its own dashboard or can be exported to Sentinel or another non-Azure SIEM, SOAR or IT Service Management (ITSM) system.

![Azure Defender for Cloud Dashboard](/assets/img/azure-defender-for-cloud-dashboard.png)

Microsoft Defender for Cloud is free, but it can also be augmented with additional plans for the following resource and technology types:

- [Servers](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-introduction)
- [Storage](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction)
- [SQL](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-sql-introduction)
- [Containers](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-containers-introduction)
- [App Service](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-app-service-introduction)
- [Key Vault](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-key-vault-introduction)
- [Resource Manager](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-resource-manager-introduction)
- [DNS](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-dns-introduction)
- [Open-source relational databases](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-databases-introduction)
- [Cosmos DB](https://docs.microsoft.com/en-us/azure/defender-for-cloud/concept-defender-for-cosmos)

These plans enable additional security features such as endpoint protection, vulnerability scanning and the detection of suspicious or unusual activity.

## Application Insights

[Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) is now a feature of Azure Monitor, and provides application performance management and monitoring for web applications. While Application Insights is foremost a performance monitoring and analysis tool, the logs that it captures can form part of your ability to monitor the security and behaviour of your applications.

![Application Insights Search](/assets/img/application-insights-search.png)

Application Insights also now features the [Application security detection pack](https://docs.microsoft.com/en-us/azure/azure-monitor/app/proactive-application-security-detection-pack) which analyses the telemetry generated by your applications to detect potential security issues. The pack currently detects three issues:

1. Insecure URL access: A URL that is accessible via HTTPS is also accessible via HTTP (i.e unencrypted).
2. Insecure Form: a form or other POST request is using HTTP instead of HTTPS.
3. Suspicious user activity: the same user is accessing the application for multiple locations at the same time.

The Application security detection pack requires no special setup, other than capturing telemetry from your application as usual.

## Azure Monitor

[Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/overview) is a powerful tool that can be used to correlate metrics and logs across all of your Azure resources, as well as those on premise. By visualising and combining metrics from different sources you can better identify abnormal behaviour in your environments. Azure Monitor alerts can then be used to notify stakeholders of criticial incidents and can be configured to trigger remediation actions via automation or ensure availability by autoscaling.

![Azure Monitor Dashboard](/assets/img/azure-monitor-dashboard.png)

Azure Monitor can be used to collect data from a variety of sources, including:

- Application logs / metrics
- Guest OS events and performance counters
- Azure resource monitoring data
- Azure subscription monitoring data
- Azure tenant monitoring data, such as activity in Active Directory

## Azure Advisor

[Azure Advisor](https://docs.microsoft.com/en-us/azure/advisor/advisor-overview) provides personalised recommendations to improve the cost effectiveness, performance, reliability and security of your resources. Azure Advisor integrates with Microsoft Defender for Cloud to bring you security recommendations, but its still an important tool to review to improve the overall quality of your deployments, and to manage those improvements in priority order.

![Azure Monitor Dashboard](/assets/img/azure-advisor.jpg)

Where possible Azure Advisor recommendations take you directly to actionable fixes and where that isn't possible provide you with the requisite documentation.

# Deployment

Azure has a low barrier of entry and creating resources via the Portal can be quick and easy, but over time this is an ineffective and risky way to manage your resources. Azure provides [Azure Resource Manager](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview) as a service to automate the deployment of your resources. Often you want to produce multiple near identical environments in order to test an application or product through different stages before delivering changes into production. Using deployment automation ensures these environments are consistent. In addition by limiting access to deploy resources through other means, your deployment pipelines act as gates that can be used (with automated testing) to deliver safe and secure resources.

![Azure ARM templates](/assets/img/azure-arm-templates.png)

For more information on the different tools you can use to automate deployments in Azure, have a look at our [Azure infrastructure as code](/blog/2021-05-01-Azure-infrastructure-as-code/) article.

# Access Control

..

# Disaster Recovery

..