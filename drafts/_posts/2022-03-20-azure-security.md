---
layout: post
title: Azure Security Tools and Capabilities
image: /assets/img/azure-security-center.png
description: >
  Cloud security is a shared responsibility between you and your  cloud provider. It is important to consider security throughout the lifecycle of the services you deploy in the cloud. This article explores some of the security tools and capabilities that are available within the Microsoft Azure platform.
hide_last_modified: true
author: mark
---

Microsoft Azure provides a number of tools and capabilities that can be leveraged to create secure cloud solutions, but these must be carefully considered and intentionally implemented. Azure also provides a number of security services and plans that can be leveraged at additional cost to monitor and manage threats and vulnerabilities. New attack vectors are discovered every day and it is not unusual for hackers to breach systems weeks or months before they leverage their unauthorised access for malicious means. Maintaining your security in the cloud needs to be an ongoing and equally evolving process.

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

# Monitor, Detect and Respond

> - _How will you monitor, detect, and respond to threats within your cloud resources?_

Azure provides a number of services that enable you to monitor and respond to security threats. To manage security effectively you need a tool that surfaces security issues and helps you to quickly understand their urgency and mitigation. These tools can also apply intelligence to automatically respond to threats, and these responses can be tailored to your needs. The main security and monitoring tools built-in to Azure are as follows:

## Microsoft Sentinel

[Microsoft Sentinel](https://docs.microsoft.com/en-us/azure/sentinel/overview) is a security information and event management (SIEM) and security orchestration, automation and response (SOAR) solution. Sentinel collects data across all your users, applications and infrastructure and can be leveraged both for on-premise resources and across multiple clouds. Microsoft's analytics and threat intelligence can alert you to previously undetected threats and works to minimise false positives. It utilises Artificial Intelligence to hunt for suspicious activity, leveraging Microsoft's years of cyber security experience and expertise. Finally through built-in orchestration and automation of common tasks it enables you to respond to incidents rapidly, via [pre-defined](https://docs.microsoft.com/en-us/azure/sentinel/use-playbook-templates) or your own custom designed [playbooks](https://docs.microsoft.com/en-us/azure/sentinel/tutorial-respond-threats-playbook).

![Microsoft Sentinel Dashboard](/assets/img/azure-sentinel-dashboard.png)

[Microsoft Sentinel pricing](https://azure.microsoft.com/en-gb/pricing/details/microsoft-sentinel/) is based on the amount of GBs of logs ingested. At time of writing, the cost in UK South is £1.89 per GB on the pay as you go tier. If you have a high level of daily logging, commitment tiers can be purchased to reduce the per GB cost. There is also a reduced cost for the ingestion of basic log types (which are often verbose but have a low amount of security data). Microsoft Sentinel can be tried free for 31 days.

## Microsoft Defender for Cloud

Previously known as Security Centre and Azure Defender, [Microsoft Defender for Cloud](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) is enabled by default and presents you with a "secure score" to simplify your understanding of the security state of your resources and to provide simple actionable recommendations to harden your environment. Defender for Cloud generates security alerts which can be managed within its own dashboard or can be exported to Azure Sentinel or another non-Azure SIEM, SOAR or IT Service Management (ITSM) system.

![Azure Defender for Cloud Dashboard](/assets/img/azure-defender-for-cloud-dashboard.png)

Microsoft Defender for Cloud is free, but it can also be augmented (at cost) with additional plans for the following resource and technology types:

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

[Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) is now integrated with Azure Monitor by default, and provides application performance management and monitoring for web applications. While Application Insights is foremost a performance monitoring and analysis tool, the logs that it captures can form part of your ability to monitor the security and behaviour of your applications.

![Application Insights Search](/assets/img/application-insights-search.png)

Application Insights also now features the [Application security detection pack](https://docs.microsoft.com/en-us/azure/azure-monitor/app/proactive-application-security-detection-pack) which analyses the telemetry generated by your applications to detect potential security issues. The pack currently detects three issues:

1. Insecure URL access: A URL that is accessible via HTTPS is also accessible via HTTP (i.e unencrypted).
2. Insecure Form: a form or other POST request is using HTTP instead of HTTPS.
3. Suspicious user activity: the same user is accessing the application from multiple locations at the same time.

The Application security detection pack requires no special setup, other than capturing telemetry from your application as usual.

## Azure Monitor

[Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/overview) is a powerful tool that can be used to correlate metrics and logs across all of your Azure resources, as well as those on premise. By visualising and combining metrics from different sources you can better identify abnormal behaviour in your environments. Azure Monitor alerts can then be used to notify stakeholders of critical incidents and can be configured to trigger remediation actions via automation or ensure availability by autoscaling.

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

# Managing Deployments and Detecting Vulnerabilities

> - _How will you manage the deployment of resources and control, manage, and monitor changes to your cloud infrastructure and applications?_
> - _How will you detect vulnerabilities in your cloud applications?_

While threat detection and management is key, prevention is better than a cure. Deploying infrastructure in Azure is likely to be an iterative and ongoing process for you. By utilizing CI/CD pipelines and infrastructure as code to automate your deployments you can ensure infrastructure changes are delivered safely and securely. By applying appropriate controls and monitoring around other changes made within your subscriptions you can remove the risk of uncontrolled or rogue changes introducing security risks.

## Azure Resource Manager

Azure has a low barrier of entry and creating resources via the Portal can be quick and easy, but over time this is an ineffective and risky way to manage your resources. Azure provides [Azure Resource Manager](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview) as a service to automate the deployment of your resources. Often you want to produce multiple near identical environments in order to test an application or product through different stages of your development lifecycle before delivering changes into production. Using deployment automation ensures these environments are consistent. In addition by limiting access to deploy resources through other means, your deployment pipelines can act as gates that can be used (with automated testing and vulnerability scanning tools) to deliver safe and secure changes.

![Azure ARM templates](/assets/img/azure-arm-templates.png)

For more information on the different tools you can use to automate deployments in Azure, have a look at our earlier [Azure infrastructure as code](/blog/2021-05-01-Azure-infrastructure-as-code/) article.

## Vulnerability Scanning

By deploying Azure's [Vulnerability Assessment agent](https://docs.microsoft.com/en-us/azure/defender-for-cloud/deploy-vulnerability-assessment-vm) (provided by Qualys) on to your Virtual Machines in both pre-production and production application vulnerabilities can be surfaced and reported to Defender for Cloud for mitigation. The agent can be deployed directly from Defender for Cloud and/or you can enable an Azure policy to ensure its deployed by default on to any new and existing Virtual Machines.

# Access Control

> - _How will you limit access between specific devices and subnets and ensure that the minimum required access is enabled?_
> - _How will you limit, monitor, and control access to your Azure resources and manage access to your applications?_

When planning access to your Azure resources you need to consider the needs of your users and those administering your resources. User access is enforced through network controls and through whatever authentication (if required) is configured for your applications. Administrative access in Azure is managed via role based access control.

## Role Based Access Control

By using Azure [role based access control](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview) you can implement permissions for your Azure administrators so they have access to specific resources they require and are able to execute only the actions they need to in order to perform their duties. Implementing roles and access correctly in Azure is critical to securing your infrastructure. Over provisioning permissions could result in a compromised account causing significant harm or disruption, so you should ensure that you understand the permissions users need and limit them via roles and groups appropriately.

![Access Control](/assets/img/access-control.png)

Permissions in Azure can be set at the following levels:

- Management Group -- This is the highest organisation level and allows you to group more than one subscription so that permissions can be assigned for them all easily.
- Subscription -- A collection of resources that fall under the same billing subscription.
- Resource Group -- A management group that allows you to group related resources for ease of management.
- Resource -- A specific resource in Azure (i.e a Virtual Machine, database etc.)

Permissions are assigned via roles. You can use either the built-in roles (which provide pre-determined sets of permissions for various typical responsibilities) or you can create your own custom roles. Roles are additive, which means that if a user is a member of more than one role, they effectively have the combined permissions for both. Roles can now also feature [deny assignments](https://docs.microsoft.com/en-us/azure/role-based-access-control/deny-assignments), where a specific permission is blocked for a user. Deny assignments always take precedence over those allowed. 

Users are managed for your tenant via Azure Active Directory (AD) and its important to consider enforcing a [Multi-factor Authentication](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) requirement for any users who have significant permissions within your subscriptions.

## Network Access Control

Many services in Azure are publicly accessible by default, so giving careful thought to [network security](https://docs.microsoft.com/en-us/azure/security/fundamentals/network-overview) is essential. Network controls in Azure can be applied via one or more of the following technologies:

- [Network Security Groups](https://docs.microsoft.com/en-us/azure/virtual-network/network-security-group-how-it-works)
- [Application Security Groups](https://docs.microsoft.com/en-us/azure/virtual-network/application-security-groups)
- [Azure Firewall](https://docs.microsoft.com/en-us/azure/firewall/overview)
- [Azure DDoS protection](https://docs.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview)
- [Azure Web Application Firewall](https://docs.microsoft.com/en-us/azure/web-application-firewall/overview)

Controlling access in, out and within your networks is a basic tenant of IT security. Azure allows you to define Network Security Groups (NSGs) with ordered lists of rules to allow traffic from specific sources, to specific destinations on specific ports and protocols. NSGs can be assigned to subnets or network interface (NICs). By using Application Security Groups (ASGs) you can simplify the management of the rules in your NSGs by grouping services together and then using the ASG as the source or destination for your rules. By using ASGs it may be possible to define all of your rules via a single NSG (applied to all subnets for a specified VNET), which has the advantages of centralising network security management. There's no cost for NSGs and an Azure Subscription can have up to 5000 NSGs with a maximum of 1000 rules in each.

![Azure Network Security Group Rules](/assets/img/nsg-rules.png)

Where as NSGs allow you to define network access at OSI layers 3 and 4, Azure Firewall allows you to filter traffic based on layers 3 - 7. This kind of filtering is able to inspect the contents of traffic coming in and out of your network to determine if they may be malicious. Threat intelligence-based filtering can alert or automatically deny access from known malicious IPs or domains. Azure Firewall is available as standard and [premium](https://docs.microsoft.com/en-us/azure/firewall/premium-features), with the premium version providing advanced capabilities for rapid detection of attacks by looking for specific patterns, to block things like malware, phishing, coin mining and trojan attacks.

Distributed Denial of Service (DDoS) attacks attempt to force a service offline by overwhelming it with requests, making the service unavailable to legitimate users. Any internet facing service is vulnerable to DDoS attacks. Azure DDoS Standard protection is a feature that can be enabled for a fixed monthly cost (currently £2,218/month in West Europe) to one or more of your VNETs within a specified tenant to protect up to 100 public IPs (with additional IPs being charged as overage). DDoS protection is an always-on service and attack mitigation is a fully automatic process. It also learns your traffic over time to tune itself to the profile that is most suitable for your service. There is a [basic level of DDoS protection](https://docs.microsoft.com/en-us/azure/ddos-protection/ddos-faq#are-services-unsafe-in-azure-without-the-service-) enabled by default in Azure, but Microsoft warns that the threshold at which this may trigger will already be at a level higher than most applications have the capacity to handle.

Azure Web Application Firewall is a feature of Azure Application Gateway (a web traffic load balancer) that provides centralised protection of your services from common exploits and vulnerabilities, such as SQL injection and cross-site scripting. You enable WAF via your own custom policy where you define the rules you want to apply from one of the [OWASP Core rule sets](https://docs.microsoft.com/en-us/azure/web-application-firewall/ag/application-gateway-crs-rulegroups-rules?tabs=owasp32). Azure WAF is an additional cost vs deploying an Application Gateway without the WAF feature enabled. However if you have DDoS protection enabled on the tenant then you pay the standard Application Gateway pricing for WAF. In West Europe Application Gateway with WAF is charged at £77.59 a month, with data processing charged at £0.0061 per connection/month.

# Backup and Disaster Recovery

> - _How will you recover your service should malicious activity or disruption occur?_

Your last line of defence against security intrusion and malicious disruption is a working backup and disaster recovery strategy. It is important to consider both of these in isolation: a backup strategy does not necessarily allow you to recover from a disaster, in that it doesn't necessarily protect you from the loss of you primary Azure region, or give you the scripts and procedures necessary to fully recover your services if they are lost. Equally a disaster recovery strategy isn't a form of backup, as it typically involves replicating your data to a secondary location and malicious or accidental corruption or deletion of data would be immediately replicated to the secondary site. However implementing and regularly testing both backup and disaster recovery gives you the protection you need to recover quickly (and with minimal data loss) from an unexpected or malicious outage.

## Azure Backup

[Azure Backup](https://docs.microsoft.com/en-us/azure/backup/backup-overview) provides a simple built-in solution to backup and restore your data in the cloud, as well as on-premise. Azure backup can be used to backup the following resources:

- [On-premise files](https://docs.microsoft.com/en-us/azure/backup/backup-mabs-protection-matrix), folders and system state, using the Microsoft Azure Recovery Services (MARS) agent.
- [Entire Azure VMs](https://docs.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction) (Windows and Linux), or specific files, folders or system state.
- [Azure Managed disks](https://docs.microsoft.com/en-us/azure/backup/backup-managed-disks)
- [Azure File shares](https://docs.microsoft.com/en-us/azure/backup/backup-afs)
- [SQL Servers on Azure VMs](https://docs.microsoft.com/en-us/azure/backup/backup-azure-sql-database)
- [SAP HANA databases on Azure VMs](https://docs.microsoft.com/en-us/azure/backup/backup-azure-sap-hana-database)
- [Azure Database for PostgreSQL servers](https://docs.microsoft.com/en-us/azure/backup/backup-azure-database-postgresql)
- [Azure Blobs](https://docs.microsoft.com/en-us/azure/backup/blob-backup-overview)

To use Azure Backup you deploy a Recovery Services Vault which is used to define your backup policies and store your backup data. Backups can be replicated to protect them against regional outages by using either Geo-redundant storage (GRS) (for protection against the loss of an entire Azure Region) or Zone-redundant storage (ZRS) (for protection against the loss of a zone within an Azure region). When you are using GRS you can also enable the Cross Region Restore feature, allowing you to access and restore the secondary region backups at any time, which can be useful for testing or if you want to trigger a restore in the secondary region regardless of the state of the primary region.

![Azure Backup](/assets/img/azure-backup.png)

Via your Azure Backup policies you define how long your backups are retained. You can specify daily, weekly, monthly and yearly backup points, allowing you to retain backups for a long period of time but at a lower frequency than more recent backups.

## Disaster Recovery

[Azure Site Recovery](https://docs.microsoft.com/en-gb/azure/site-recovery/site-recovery-overview) is the built-in Azure Disaster Recovery Service. Site Recovery works by replicating your workloads to a secondary location so that when an outage occurs you can fail over and resume service quickly. With Site Recovery you can replicate:

- Azure VMs from one region to another.
- On-premise VMWare VMs, Hyper-V VMs, physical servers (Windows and Linux) and Azure Stack VMs to Azure or to a secondary site.
- AWS Windows instances to Azure.

![Disaster Recovery](/assets/img/disaster-recovery.jpg)

Site Recovery is a good solution for getting your VMs up and running quickly after a disaster, but your DR strategy needs to consider all of the resource types your using in Azure. Most have DR features built in, such as the ability for data to be geo-replicated, but you'll need to ensure these features are enabled and that you understand if and when you need to trigger a failover as part of your recovery strategy or testing. You also may need to consider how you will redirect users and traffic to the secondary location as part of a DR failover, and services such as [Azure Traffic Manager](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview) can be used to automate this.

# Summary

We hope you've found this introduction to security capabilities and tools in Azure useful. Remember that security is an ongoing practice and requires ownership and accountability to be effective. Microsoft provide the tools to surface threats in your infrastructure but its largely your responsibility to act on the information they provide. If you think MPFE can be of any assistance in securing your Azure resources, please do not hesitate to [get in touch with us](mailto:mark@mpfe.uk).