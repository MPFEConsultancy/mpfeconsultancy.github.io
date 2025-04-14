---
layout: post
title: Azure Container Services
image: /assets/img/azure-container-services.png
description: >
  Azure features a number of services for working with Containers. These can be leveraged to improve the deployment speed and security of containerized software, while eliminating the complexity of hosting and running a container platform.
hide_last_modified: true
author: mark
---

In modern software development, containers have become a popular way to package and deploy code. Microsoft Azure features a number of containerization services. In this blog article we will explore those services and how they can be leveraged to improve the speed and security of deploying software code in a way that is both cost efficient and scales to meet demand.

> **What is a container?**
>
> In computing, a container is a lightweight, portable, and self-contained package that bundles an application's code, runtime, libraries, and dependencies, allowing it to run consistently across different environments.
> The history of containers can be traced back to the 1970s, where it was first implemented on Unix systems as a way to better isolate application code.
> However the popularity of containers really exploded with the release of Docker in 2013.
> This led to a de facto standard format for container images (OCI) which the industry rallied around.
> Docker made containers approachable for developers with a clean CLI, sensible defaults and easy to write Dockerfiles.
> Ultimately "It works on my machine" became "It works everywhere".

Azure offers a range of containerization services. Which one/s you should choose will depend on your specific needs, the complexity of your application/s and how much control you want of the underlying platform.

![Azure compute services](/assets/img/azure-compute-services.png)

Compute services are often grouped under the following terms, that describe the type and complexity of the service being offered to the end consumer:

- **IaaS — Infrastructure as a Service**, a cloud computing model that provides on-demand access to virtualized computing resources like servers, storage, and networking, allowing businesses to rent these resources instead of managing their own physical hardware.
- **CPaaS — Container Platform as a Service**, is a cloud-based service that allows developers to manage and deploy applications using containers, providing a managed environment for container orchestration, scaling, and deployment, without the need to manage the underlying infrastructure.
- **CaaS — Container as a Service**, is a cloud-based service that allows developers and IT departments to manage and deploy containerized applications, enabling rapid deployment and scaling without managing underlying infrastructure.
- **PaaS — Platform as a Service**, is a cloud computing model where a third-party provider delivers hardware and software tools, including infrastructure, over the internet, enabling users to develop, run, and manage applications without managing the underlying infrastructure.
- **FaaS — Function as a Service**, a cloud computing model where developers can deploy individual functions to the cloud without managing the underlying infrastructure, allowing them to focus on code execution and event-driven applications.

As of April 2025, the Azure containerization services are as follows:

### Azure Kubernetes Service (AKS)

> Deploy and scale containers on managed Kubernetes

Kubernetes (often shortened as "K8s") is an open-source container orchestration platform. It automates the deployment, scaling and management of containerized applications. You can build and run your own Kubernetes cluster, but this can involve a lot of complexity and the burden of ongoing maintenance. [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/products/kubernetes-service), simplifies this by offering Kubernetes as a managed service, meaning Microsoft are responsible for the underlying infrastructure, maintenance and patching.

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

### Web App for Containers

> Run containerized web apps on Windows and Linux

Azure App Service can be used to run containers via the [Web App for Containers](https://azure.microsoft.com/en-gb/products/app-service/containers) resource. Azure App Service is a fully managed platform, optimised for hosting web applications such as websites and web APIs. This can be another good choice if you want to focus on developing your application and don't need or want any specific control of the underlying infrastructure on which it's run. By using Web App for Containers you can develop, test and deploy your web app as a container.

### Azure Container Instances

> Launch containers with hypervisor isolation

[Azure Container Instances](https://azure.microsoft.com/en-gb/products/container-instances/) (ACI) is another serverless option for running containers in Azure. The containers are able to be spun up very quickly (in seconds), so can be beneficial for scaling vs other VM based platforms. In fact Azure Container Instances can be used to supplement your AKS compute, by utilizing [Virtual nodes on Azure Container instances](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-virtual-nodes) you can add a pod to your existing AKS cluster that run as container groups in ACI. The underlying platform is fully managed by Microsoft. Despite being a multitenant platform, the containers are isolated by Hypervisor, so are as isolated as they would be on a VM.

Within ACI you define [Container Groups](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-container-groups) a top level resource for Azure Container instances. A container group is a collection of containers that get scheduled on the same host machine. They share a lifecycle, local network and storage volumes, which is conceptually similar to a pod in Kubernetes.

### Azure Container Registry

> Build, store, secure, and replicate container images and artifacts

[Azure Container Registry](https://azure.microsoft.com/en-us/products/container-registry) (ACR) is not a compute platform (like the other offerings above), but a resource that can be used as a private repository for your container images. It also can be used to store other related artifacts such as Helm charts. ACR is geo-replicated and secured via Entra ID much like Azure Storage. It also has automatic vulnerability scanning built in.

![Azure Container Instances](/assets/img/azure-container-instances.png)

## Summary

Using containers can be a useful way to ensure software can be deployed consistently and successfully across different platforms and environments. Selecting the right containerization service in Azure requires you to consider the needs and complexity of the application you want to run. For example if you're lifting and shifting an existing Kubernetes cluster to the cloud, Azure Kubernetes Service could be a good option to ensure you can continue to configure the cluster to the specific needs of your application while removing the management and maintenance overhead. If you're deploying containers to the cloud for the first time Azure Container Instances or Azure Container Apps could be a good choice, simplifying the configuration required of the platform. Ultimately Azure makes it easy to experiment with these technologies and many have free tiers to help you get started.