---
layout: post
title: Azure Security Tools and Capabilities
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

Where possible Azure Advisor recommendations take you directly to actionable fixes or (where that isn't possible) provide you with the requisite documentation.

# Deployment

## Azure Resource Manager

Azure has a low barrier of entry and creating resources via the Portal can be quick and easy, but over time this is an ineffective and risky way to manage your resources. Azure provides [Azure Resource Manager](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview) as a service to automate the deployment of your resources. Often you want to produce multiple near identical environments in order to test an application or product through different stages before delivering changes into production. Using deployment automation ensures these environments are consistent. In addition by limiting access to deploy resources through other means, your deployment pipelines act as gates that can be used (with automated testing) to deliver safe and secure resources.

![Azure ARM templates](/assets/img/azure-arm-templates.png)

For more information on the different tools you can use to automate deployments in Azure, have a look at our [Azure infrastructure as code](/blog/2021-05-01-Azure-infrastructure-as-code/) article.

# Access Control

When planning access to your Azure resources you need to consider the needs of your customers and those administering your resources. Generally customer access is managed via network controls, or via authentication if required. Administrator access in Azure is managed in Azure via role based access control.

## Role based access control

By using Azure [role based access control](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview) you can implement specific permissions for your users so they have access just to the resources they require and are able to perform only the actions they need to in order to perform their duties. Implementing roles and access correctly in Azure is critical to securing your infrastructure. Over provisioning permissions could result in a compromised account causing significant harm or disruption, so you should ensure that you understand the permissions users need and limit them via roles and groups appropriately.

![Access Control](/assets/img/access-control.png)

Permissions in Azure can be set at the following levels:

- Management Group -- This is the highest organisation level and allows you to group more than one subscription so that permissions can be assigned for them all easily.
- Subscription -- A collection of resources that fall under the same billing subscription.
- Resource Group -- A management group that allows you to group related resources for ease of management.
- Resource -- A specific resource in Azure (i.e a Virtual Machine, database etc.)

Permissions are assigned via roles. You can use either the built-in roles (which provide pre-determined sets of permissions for various typical responsibilities) or you can create your own custom roles. Roles are additive, which means that if a user is a member of more than one role, they effectively have the combined permissions for both. Roles can now also feature [deny assignments](https://docs.microsoft.com/en-us/azure/role-based-access-control/deny-assignments), where a specific permission is blocked for a user. Deny assignments always take precedence over those allowed. 

## Network Access

..

# Disaster Recovery

## Azure Backup

[Azure Backup](https://docs.microsoft.com/en-us/azure/backup/backup-overview)

![Azure Backup](/assets/img/azure-backup.png)

## Disaster Recovery

[Azure Site Recovery](https://docs.microsoft.com/en-gb/azure/site-recovery/site-recovery-overview)

![Disaster Recovery](/assets/img/disaster-recovery.jpg)

# Summary

We hope you've found this introduction to security capabilities and tools in Azure useful. Remember that security is an ongoing practice and requires ownership and accountability to be effective. Microsoft provide the tools to surface threats in your infrastructure but its largely your responsibility to act on the information they provide. If you think MPFE can be of any assistance in securing your Azure resources, please do not hestiate to [get in touch with us](mailto:mark@mpfe.uk).