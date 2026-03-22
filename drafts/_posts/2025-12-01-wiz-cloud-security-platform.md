---
layout: post
title: Wiz Cloud Security
image: /assets/img/wiz.png
description: >
  In the age of AI, cybersecurity has never been more important. Wiz is one of the tools you can leverage to manage risks in your cloud environments. Wiz is a comprehensive security platform that is being continuously updated and improved, and can be quickly leveraged for any existing cloud infrastructure to identify and manage security risks.
hide_last_modified: true
author: mark
---

Wiz is a Cloud Security Software platform, designed to help organisations understand, identify and manage security risks in various cloud environments, including Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP), Oracle Cloud Infrastructure (OCI), Alibaba Cloud and Linode Cloud. It can also be used to monitor VMware vSphere environments on premise. Wiz is a cloud-native application protection platforms (CNAPP). Wiz can be implemented in an entirely agentless way, so can be used to very quickly assess the security posture of even the most complex cloud environments. Wiz's magic is really from two key features:

1. It builds a graph database of your resources, vulnerabilities, security principals and the relationships between them. This database can be quickly and easily queried to answer many complex questions about your infrastructure, applications and their security posture.
2. It uses this graph database to identify "toxic combinations", of vulnerabilities, cloud misconfigurations and exposed secrets to identify and prioritise the most critical risks.

By taking a risk-based approach to vulnerability management, Wiz makes security actionable. Many customers may discover that they have hundreds of thousands if not millions of vulnerabilities across their estate. While this visibility is important, it isn't very actionable. Wiz takes this raw scan data, along with what it knows about your cloud configuration (such as whether your systems are internet exposed), applies its threat intelligence to determine how likely a breach is to occur (based on it's knowledge of which vulnerabilities are being actively explioted in the wild), and the impact to your business (partly based on what you've told it about the importance / purpose of different resources, such as whether they are dev, staging or production) and creates a smaller inbox of "issues" that can be actioned to address the most important threats.

![Wiz Risk-based approach to vulnerability management in the cloud](/assets/img/wiz-risk-approach.webp)

Wiz exposes a number of different types of issues:

- **Risk issues:** These are active risks that Wiz has identified in your Cloud environments, as defined by the policies. Wiz provides thousands of built-in policies, but your can also define your own custom policies to suit your organisations needs.
- **Cloud Configuration issues:**
- **External Exposure issues:**
- **Identity Entitlements issues:**
- **Data Security issues:**