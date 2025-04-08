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

### Azure Kubernetes Service (AKS)

> Deploy and scale containers on managed Kubernetes

Kubernetes (often shortened as "K8s") is an open-source container orchestration platform. It automates the deployment, scaling and management of containerized applications. You can build and run your open Kubernetes cluster, but this can involve a lot of complexity and the burden of ongoing maintenance. [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/products/kubernetes-service), simplifies this by offering Kubernetes as a managed service, meaning Microsoft are responsible for the underlying infrastructure, maintenance and patching.

![AKS control plane and nodes](/assets/img/aks-control-plane-and-nodes.png)

### Azure Red Hat OpenShift

> Deploy and scale containers on managed Red Hat OpenShift

OpenShift is a family of containerization products developed by Red Hat. OpenShift is built on top of Kubernetes, but adds additional features and tools to automate tasks such as building, deploying, scaling and managing applications. Azure Red Hat OpenShift is a PaaS (Platform as a Service) offering (much like AKS), which simplifies running Red Hat OpenShift by extrapolating away the complexity of building, maintaining and operating the cluster. Unlike AKIS, OpenShift includes an integrated container image registry, simplifying image management. It is also includes other software by default, such as application runtimes and observability packages.

![Red Hat OpenShift components](/assets/img/redhat-open-shift-components.jpg)

### Azure Container Apps

> Build and deploy modern apps and microservices using serverless containers

### Azure Functions

> Execute event-driven, serverless code with an end-to-end development experience

### Web App for Containers

> Run containerized web apps on Windows and Linux

### Azure Container Instances

> Launch containers with hypervisor isolation

[Container Instances](https://azure.microsoft.com/en-gb/services/container-instances/) (preview) - a service for easily running containers without needing to worry about orchestration. I think this service is aimed at testing/development.

[Container Groups](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-container-groups) (preview) - a top level resource for Azure Container instances. A container group is a collection of containers that get scheduled on the same host machine. They share a lifecycle, local network and storage volumes.

### Azure Service Fabric

Deploy and operate always-on, scalable, distributed apps

### Azure Container Registry

Build, store, secure, and replicate container images and artifacts

[Container Registries](https://azure.microsoft.com/en-gb/services/container-registry/) - a private docker registry to store and manage container images.
