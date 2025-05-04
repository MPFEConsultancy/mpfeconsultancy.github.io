---
layout: post
title: The AWS Well Architected Framework
image: /assets/img/aws-well-architected.png
description: >
  The AWS Well Architected framework is a set of best practices and guidelines for designing and operating infrastructure on the AWS cloud.
hide_last_modified: true
author: mark
---

First published in 2012, the Amazon Web Services (AWS) Well-Architected Framework is a collection of best practice guidelines to help customers implement high quality solutions and infrastructure in the AWS cloud. The framework currently features six pillars:

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization
- Sustainability

The AWS Well-Architected Framework helps you understand trade-offs for decisions you make while building workloads on AWS, and how to apply best practices in the design, delivery and maintenance of your environments. The framework is continuously being improved in response to new best practices, customer feedback and industry trends.

![AWS Well-Architected Pillars](/assets/img/aws-well-architected-pillars.png)

Other cloud providers have similar frameworks, and we've blogged about the [Azure Well-Architected Framework](https://mpfe.uk/blog/2021-04-01-azure-well-architected-framework/) previously.

## Operational Excellence

Operational Excellence is less about what you build in AWS and more about how you organise your teams or business to achieve business outcomes. It is about evaluating the needs of your internal and external customers, any governance or compliance requirements and potential threats. From this you can determine an appropriate operating model to meet the needs of your business or a mix of models to meet the needs of different teams. You should establish key performance indicators (KPIs) and leverage telemetry to ensure you can make informed decisions. Safely automate where possible, such as ensuring your application, infrastructure, configuration and procedures are defined and maintained as code. Keep changes frequent but small, so they can be easily reversed. Perform regular reviews of your operational procedures so they can be continuously improved. Expect failures to occur, and plan for them by identifying the risks and rehearsing your responses to outages.

## Security

The security pillar provides guidance and recommendations to ensure the secure design, delivery and maintenance of AWS workloads. Security is a shared responsibility between you and AWS, who remove some of the burden by taking responsibility of security of the host operating system, virtualisation layer and physical security. The customer is responsible for the guest operating systems (including security updates/patches) and any applications or software they run. They are also responsible for designing and configuring the security of the networks they configure by utilising technologies such as firewalls. Customers are also responsible for managing and controlling access to their resources by ensuring they appropriately manage and configure Identity and Access Management (IAM) users and roles. AWS provides tools to help centralise security controls, such as by applying policies to restrict the type of resources and/or regions that can be used.

## Reliability

Reliability is concerned with ensuring that a workload performs its intended function correctly and consistently. This pillar encourages customers to consider designing or improving their solutions to be able to automatically recover from failure. Workloads should be designed to use highly available resources, and to scale horizontally so that requests are managed across a number of smaller resources that do not share a common point of failure, reducing the impact if one or more fails. It also encourages the monitoring of demand so that capacity can be appropriately predicted and planned. It advises managing change through automation, so infrastructure changes can be predictably tested and repeated. Finally it advises on managing failure, and ensuring that appropriate protections have been implemented such as data backups and fault isolation.

## Performance Efficiency

The performance efficiency pillar is about helping customers to build architectures on AWS that deliver sustained performance over time. The focus areas are:

- architecture selection: choosing the optimal solution for a particular workload, factoring in cost and other trade offs.
- compute and hardware: selecting the best compute options, collecting metrics and scaling dynamically.
- data management: using purpose-built data stores that best suit your data access and storage requirements, collecting metrics and implementing strategies to improve query performance and data access.
- networking and content delivery: understanding how network architecture decisions impact performance, evaluating available features, distributing load and optimising performance based on metrics.
- process and culture: utilising infrastructure as code / deployment pipelines to manage and deploy infrastructure and iterate rapidly, ensure well defined metrics are setup to monitor your KPIs, perform performance testing automatically as part of the deployment process, generate synthetic load as part of testing and make performance metrics visible to appropriate teams.

## Cost Optimization

> A cost-optimized workload fully utilizes all resources, achieves an outcome at the lowest possible price point, and meets your functional requirements.

Cost optimisation is a continual process, working to identity the most cost efficient resources for delivering a specified workload over its lifecycle. This pillar is concerned with ensuring customers understand the tools and processes AWS provides to monitor and manage costs. It recommends customers adopt a consumption model, paying only for the resources they consume, increasing or decreasing depending on demand and ensuring resources that aren't required 24x7 (such as development or test environments) are stopped when not required to reduce cost. This pillar also advises using techniques with AWS to ensure costs are attributed to specific revenue streams or owners, helping businesses measure the return on investment (ROI) of a particular workload.

## Sustainability

..