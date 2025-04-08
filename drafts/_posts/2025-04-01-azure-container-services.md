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
> Ultimately "It works on my machine" became "It works everywhere".

Azure offers a range of containerization services. Which ones you should choose will depend on your specific needs, the complexity of your application/s and how much control you want of the underlying platform. The current services are as follows:

### Azure Kubernetes Service (AKS)

> Deploy and scale containers on managed Kubernetes

Kubernetes (often shortened as "K8s") is an open-source container orchestration platform. It automates the deployment, scaling and management of containerized applications. You can build and run your open Kubernetes cluster, but this can involve a lot of complexity and the burden of ongoing maintenance. [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/products/kubernetes-service), simplifies this by offering Kubernetes as a managed service, meaning Microsoft are responsible for the underlying infrastructure, maintenance and patching.

![AKS control plane and nodes](/assets/img/aks-control-plane-and-nodes.png)

### Azure Red Hat OpenShift

> Deploy and scale containers on managed Red Hat OpenShift

OpenShift is a family of containerization products developed by Red Hat. OpenShift is built on top of Kubernetes, but adds additional features and tools to automate tasks such as building, deploying, scaling and managing applications. [Azure Red Hat OpenShift](https://azure.microsoft.com/en-gb/products/openshift) is a Platform as a Service (PaaS) offering (much like AKS), which simplifies running Red Hat OpenShift by extrapolating away the complexity of building, maintaining and operating the cluster. Unlike AKS, OpenShift includes an integrated container image registry, simplifying image management. It is also includes other software by default, such as application runtimes and observability packages.

![Red Hat OpenShift components](/assets/img/redhat-open-shift-components.jpg)

While Red Hat Enterprise Linux CoreOS is used to run the "control plane" components of OpenShift (so that it can support upgrades and patches of the control plane), the compute nodes (where your containers / applications run) can be running Red Hat CoreOS, RHEL or Windows.

### Azure Container Apps

> Build and deploy modern apps and microservices using serverless containers

[Azure Container Apps](https://azure.microsoft.com/en-us/products/container-apps) (ACA) is a more app-centric, simpler and serverless PaaS offering for running containers. While the underlying technology is still Kubernetes, the Kubernetes API is not exposed and the cluster is fully managed by Microsoft. Scaling is event-driven, or automatic, where as with AKS you have the option to scale manually. One of the benefits of ACA is that for HTTP traffic, it automatically scales to zero which avoids usage charges when there's no traffic. You can do this with AKS, but it requires configuring Kubernetes-based Event Driven Autoscaling (KEDA). ACA is a good choice for less complex deployments where you don't need or want full control of the underlying Kubernetes cluster.

![Azure Container Apps example scenarios](/assets/img/azure-container-apps-example-scenarios.png)

### Azure Functions

> Execute event-driven, serverless code with an end-to-end development experience

[Azure Functions](https://azure.microsoft.com/en-us/products/functions) supports deploying your function apps as Linux containers, but the underlying host is essentially ACA. Azure Functions are best used for event-driven, serverless workloads, such as building lightweight APIs, processing messages from queues, or running scheduled tasks, where you want to focus on code execution without managing infrastructure. When you're developing an Azure Function you're typically focussed on the code itself and leaving it to Azure to determine how it is run.

![Deploying a container to Azure Functions](/assets/img/auzre-functions.png)

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
