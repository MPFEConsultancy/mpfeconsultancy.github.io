---
layout: post
title: Azure Container Services
image: /assets/img/azure-container-services.png
description: >
  Azure features a number of services for working with Containers. These can be leveraged to improve the deployment speed and security of containerized software, while extrapolating away the complexity of hosting and running containers.
hide_last_modified: true
author: mark
---

Microsoft Azure features a number of services for working with the virtualization concept known as "containerization". In this blog article we will explore those services and how they can be leveraged to improve the speed and security of software development.

> **What is a container?**
>
> In computing, a container is a lightweight, portable, and self-contained package that bundles an application's code, runtime, libraries, and dependencies, allowing it to run consistently across different environments.
> The history of containers can be traced back to the 1970s, where it was first implemented on Unix systems as a way to better isolate application code.
> However the popularity of containers really exploded with the release of Docker in 2013.
> This led to a de facto standard format for container images (OCI) which the industry rallied around.
> Docker made containers approachable for developers with a clean CLI, sensible defaults and easy to write Dockerfiles.
> Ultimately "It works on my machine" became "It works _everywhere_".











Microsoft Azure has two container services:

- [Azure Container Service](https://azure.microsoft.com/en-gb/overview/containers/) (generally available [since April 2016](https://azure.microsoft.com/en-us/blog/azure-container-service-is-now-generally-available/)  – you can also use Kubernetes as an orchestrator)
- [Azure Container Service - AKS](https://azure.microsoft.com/en-gb/services/container-service/) (preview) - also known as container services (managed) is a dedicated managed Kubernetes service, in preview since Oct 2017
There are also the following services:

- [Container Groups](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-container-groups) (preview) - a top level resource for Azure Container instances. A container group is a collection of containers that get scheduled on the same host machine. They share a lifecycle, local network and storage volumes.
- [Container Registries](https://azure.microsoft.com/en-gb/services/container-registry/) - a private docker registry to store and manage container images.
- [Container Instances](https://azure.microsoft.com/en-gb/services/container-instances/) (preview) - a service for easily running containers without needing to worry about orchestration. I think this service is aimed at testing/development.

# Azure Container Service

- Available in all regions
- The master Kubernetes machines are exposed to you in the Azure portal and are yours to manage (and pay for).

# Azure Container Service (AKS)
- Kubernetes as a service. Currently in preview
- Only available in the East US and Central US regions
- The master Kubernetes machines are a managed service grouped and referred to as the "Hosted Control Plane". You still control if/when Kubernetes version is upgraded (which can be done without downtime) but you aren't having to otherwise pay for or manage the management machines.
- Only pay for the virtual machines instances, storage and networking resources consumed by your Kubernetes cluster.
- Azure Container Service is a free service, therefore it does not have a financially backed SLA. However, for the availability of underlying virtual machines, the Virtual Machine SLA applies.