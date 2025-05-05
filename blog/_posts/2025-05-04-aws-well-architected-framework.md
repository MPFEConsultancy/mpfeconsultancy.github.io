---
layout: post
title: The AWS Well Architected Framework
image: /assets/img/aws-well-architected.png
description: >
  The AWS Well Architected framework is a set of best practices and guidelines for designing and operating infrastructure on the AWS cloud.
hide_last_modified: true
author: mark
---

First published in 2012, the [Amazon Web Services (AWS) Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/) is a collection of best practice guidelines to help customers implement high quality solutions and infrastructure in the AWS cloud. The AWS Well-Architected Framework helps you understand trade-offs for decisions you make while building workloads on AWS, and how to apply best practices in the design, delivery and maintenance of your environments. The framework is continuously being improved in response to new best practices, customer feedback and industry trends.

Other cloud providers have similar frameworks, and we've blogged about the [Azure Well-Architected Framework](https://mpfe.uk/blog/2021-04-01-azure-well-architected-framework/) previously.

## Pillars

The framework currently features [six pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html):

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization
- Sustainability

![AWS Well-Architected Pillars](/assets/img/aws-well-architected-pillars.png)

### Operational Excellence

[Operational Excellence](https://docs.aws.amazon.com/wellarchitected/latest/framework/operational-excellence.html) is less about what you build in AWS and more about how you organise your teams or business to achieve business outcomes. It is about evaluating the needs of your internal and external customers, any governance or compliance requirements and potential threats. From this you can determine an appropriate operating model to meet the needs of your business or a mix of models to meet the needs of different teams. You should establish key performance indicators (KPIs) and leverage telemetry to ensure you can make informed decisions. Safely automate where possible, such as ensuring your application, infrastructure, configuration and procedures are defined and maintained as code. Keep changes frequent but small, so they can be easily reversed. Perform regular reviews of your operational procedures so they can be continuously improved. Expect failures to occur, and plan for them by identifying the risks and rehearsing your responses to outages.

### Security

[The security pillar](https://docs.aws.amazon.com/wellarchitected/latest/framework/security.html) provides guidance and recommendations to ensure the secure design, delivery and maintenance of AWS workloads. Security is a shared responsibility between you and AWS, who remove some of the burden by taking responsibility of security of the host operating system, virtualisation layer and physical security. The customer is responsible for the guest operating systems (including security updates/patches) and any applications or software they run. They are also responsible for designing and configuring the security of the networks they configure by utilising technologies such as firewalls. Customers are also responsible for managing and controlling access to their resources by ensuring they appropriately manage and configure Identity and Access Management (IAM) users and roles. AWS provides tools to help centralise security controls, such as by applying policies to restrict the type of resources and/or regions that can be used.

### Reliability

[Reliability](https://docs.aws.amazon.com/wellarchitected/latest/framework/reliability.html) is concerned with ensuring that a workload performs its intended function correctly and consistently. This pillar encourages customers to consider designing or improving their solutions to be able to automatically recover from failure. Workloads should be designed to use highly available resources, and to scale horizontally so that requests are managed across a number of smaller resources that do not share a common point of failure, reducing the impact if one or more fails. It also encourages the monitoring of demand so that capacity can be appropriately predicted and planned. It advises managing change through automation, so infrastructure changes can be predictably tested and repeated. Finally it advises on managing failure, and ensuring that appropriate protections have been implemented such as data backups and fault isolation.

### Performance Efficiency

[The performance efficiency pillar](https://docs.aws.amazon.com/wellarchitected/latest/framework/performance-efficiency.html) is about helping customers to build architectures on AWS that deliver sustained performance over time. The focus areas are:

- **architecture selection** — choosing the optimal solution for a particular workload, factoring in cost and other trade offs.
- **compute and hardware** — selecting the best compute options, collecting metrics and scaling dynamically.
- **data management** — using purpose-built data stores that best suit your data access and storage requirements, collecting metrics and implementing strategies to improve query performance and data access.
- **networking and content delivery** — understanding how network architecture decisions impact performance, evaluating available features, distributing load and optimising performance based on metrics.
- **process and culture** — utilising infrastructure as code / deployment pipelines to manage and deploy infrastructure and iterate rapidly, ensure well defined metrics are setup to monitor your KPIs, perform performance testing automatically as part of the deployment process, generate synthetic load as part of testing and make performance metrics visible to appropriate teams.

### Cost Optimization

> A cost-optimized workload fully utilizes all resources, achieves an outcome at the lowest possible price point, and meets your functional requirements.

[Cost optimisation](https://docs.aws.amazon.com/wellarchitected/latest/framework/cost-optimization.html) is a continual process, working to identity the most cost efficient resources for delivering a specified workload over its lifecycle. This pillar is concerned with ensuring customers understand the tools and processes AWS provides to monitor and manage costs. It recommends customers adopt a consumption model, paying only for the resources they consume, increasing or decreasing depending on demand and ensuring resources that aren't required 24x7 (such as development or test environments) are stopped when not required to reduce cost. This pillar also advises using techniques with AWS to ensure costs are attributed to specific revenue streams or owners, helping businesses measure the return on investment (ROI) of a particular workload.

### Sustainability

[The sustainability pillar](https://docs.aws.amazon.com/wellarchitected/latest/framework/sustainability.html) was added in 2021, which focuses on the environmental sustainability of your workloads, addressing the long-term environment, economic and societal impact of your business activities. Sustainability is also a shared responsibility between you and AWS, who make their own efforts to lower the carbon footprint of their data centres by utilising efficient power and cooling technology, and are typically more energy efficient than on-premises alternatives, due to the shared nature of their resources and the resultant higher server utilisation rates. As the customer you can go further to minimise the environmental impact of your resources, reducing energy consumption by minimising the total resources required or making technology selections that improve efficiency such as reducing data storage. Through this pillar customers identify targets, evaluate specific improvements and then prioritise, plan test and validate them.

## Lenses

AWS have further extended the well-architected framework through lenses, which extend the pillars with additional best practices for specific technologies or industries. More than one lens can be applied to a workload, and can be found in the [Lens Catalog](https://docs.aws.amazon.com/wellarchitected/latest/userguide/lens-catalog.html). The current official lenses are:


- **AWS Well-Architected Framework** —  Core best practices, applied by default to all workloads
- **Connected Mobility** — Guidance for automotive and transportation workloads focusing on connected vehicles and mobility solutions.
- **Container Build** — Best practices for building containerized applications, including CI/CD pipelines and artifact management.
- **Data Analytics** — Design principles for analytics workloads including data ingestion, processing, and visualization at scale.
- **DevOps** — Recommendations for implementing DevOps practices such as automation, infrastructure as code, and observability.
- **Financial Services Industry** — Tailored best practices to meet the regulatory, security, and operational needs of financial services.
- **Generative AI** — Guidance for building, training, and deploying generative AI workloads responsibly and efficiently.
- **Government** — Best practices aligned with government standards and compliance requirements for public sector workloads.
- **Healthcare Industry** — Specialized recommendations for handling sensitive healthcare data and meeting industry regulations like HIPAA.
- **IoT** — Guidance on designing scalable, secure, and efficient Internet of Things (IoT) workloads.
- **Mergers and Acquisitions** — Framework for IT planning and execution during organizational mergers, acquisitions, or divestitures.
- **Machine Learning** — Best practices for ML lifecycle management including data prep, model training, and deployment.
- **Migration** — Structured approach to migrating workloads to AWS, including planning, execution, and optimization.
- **SaaS** — Architectural guidance for building and operating multi-tenant SaaS applications on AWS.
- **SAP** — Best practices for deploying and managing SAP workloads on AWS infrastructure.
- **Serverless Applications** — Design principles for serverless workloads using services like AWS Lambda, DynamoDB, and API Gateway.

Customers can also create [custom lenses](https://docs.aws.amazon.com/wellarchitected/latest/userguide/lenses-custom.html), featuring their own pillars, questions, best practices and improvement plans.

## Summary

We hope the above has been a useful summary of the AWS Well-Architected Tool. If you're ready to get started validating your workloads, there is a [getting started guide here](https://docs.aws.amazon.com/wellarchitected/latest/userguide/getting-started.html).