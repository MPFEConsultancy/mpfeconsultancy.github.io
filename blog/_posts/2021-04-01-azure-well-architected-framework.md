---
layout: post
title: The Azure Well Architected Framework
image: /assets/img/azure-well-architected.png
description: >
  The Azure Well Architected framework is a set of guiding principals that can be used to plan or assess your use of Azure to improve the quality of your infrastructure. 
sitemap: false
hide_last_modified: true
author: mark
---

In 2020 Microsoft introduced the Azure Well-Architected Framework. Freely available online via the Microsoft Documentation site, the framework is a best practice guide for planning or improving your Azure infrastructure. The framework is organised into five pillars of architectural excellence:

- Cost Optimization
- Operational Excellence
- Performance Efficiency
- Reliability
- Security

## Cost Optimisation

One of the primary advantages of leveraging the cloud is the ability to take a "pay as you go" approach to your infrastructure. Traditional IT generally required a lot of up front capital expenditure, as well as pre provisioning for the highest peak in demand. With the clouds ability to scale on demand and with infrastructure automation tools infrastructure can be provisioned more flexibly to meet demand. However, without a focus on cost when implementing cloud architecture there is a risk costs getting out of control.

> "You can use Cosmos DB to burn money, but you can also use it as a database." -- https://mijailovic.net/2020/07/25/cosmosdb-throughput/



## Operational Excellence

It can be quick and easy to get started deploying resources in Azure, via the Azure Portal. This enables easy experimentation, but it is important to have a strategy for operating and monitoring your resources long term, particularly once you're considering running production workloads (and even if you're not!). The Operational Excellence pillar is about ensuring you leverage automation as part of your deployments, such as by using ARM or Terraform templates to deploy infrastructure. It is also about ensuring you have monitoring and diagnostic tools in place and have given consideration to the different nature of cloud resources, where you may sometimes not have access to the operating system and where you may need to troubleshoot issues across many 10s or 100s of instances.

## Performance Efficiency

The Performance Efficiency pillar is about giving consideration to how your workloads will scale to meet demand. The best way to achieve this is to leverage Azure resource types that have scaling options built in. You can scale vertically or horizontally. Vertical scaling (scaling up) is about increasing capacity, such as adding more memory or CPU to a Virtual Machine (VM). Horizontal scaling (scaling out) is about adding more instances of a resource, such as additional VMs or replicas.

## Reliability

Reliability is about giving consideration to resilience and availability. Cloud systems are often complex and there are many layers outside of your control. Rather than focus on avoiding failures, your workloads should be designed to be suitably resilient. This means choosing and designing Azure resources with appropriate redundancy features configured as well as ensuring your applications are designed to handle failures, such as the unavailability of an external service.

## Security

The final pillar is about considering security throughout the lifecycle of your application, giving consideration to both external threats as well as how permissions and access should be managed internally. The Azure platform provides multiple layers of security, some of which you need to manage and others which are managed for you (such as physical security). Managing permissions can quickly become complex so having a good strategy for implementing and monitoring access is essential. 