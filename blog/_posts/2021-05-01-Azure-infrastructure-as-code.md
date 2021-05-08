---
layout: post
title: Infrastructure-as-Code tooling options for Azure
image: /assets/img/azure-arm-templates.png
description: >
  There are now several different options for infrastructure as code in Azure. Historically ARM templates or Terraform have been the main tools of choice, but there is now also Bicep and PSArm to consider. This post explores these different tooling options and their advantages and disadvantages.
hide_last_modified: true
author: mark
---

Cloud computing has a low barrier of entry. It is generally very easy to deploy resources through a web based portal and this can be a quick way to experiment and get started. However cloud infrastructure can also become complex very quickly and so managing your resources via automation is a must. Infrastructure as Code (IaC) is the concept of declaring your infrastructure as one or more configuration templates and then having your cloud provider execute those templates via its API in order to deploy and configure your resources to align with your declaration. Used well, infrastructure templates ensure consistency, repeatability and enable version control.

In Azure there are several different tools you can choose for implmenting Infrastructure as Code. We detail four of these below, two of which are well established and two are new / in Beta.

## ARM Templates

The native approach to Infrastructure as Code in Azure is to use [ARM (Azure Resource Manager) templates](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview). ARM templates are authored in JSON (JavaScript Object Notation), which is a common data format for storing objects. ARM templates have a schema which includes the following sections:

- Parameters - Used to provide environment specific values at deployment time. By using paramemters you can have one template generate multiple environments (e.g: test, staging, prod)
- Variables - Define values that you reuse in your template, so that you are controlling their value in a single location.
- User-defined functions - Create functions to simplify operations in your template (e.g to create or transform a specific input value).
- Resources - Define the Azure resources that the template should deploy and their configuration settings.
- Outputs - Use to output values after the template has been run (such as URLs or Keys) that might then be fed into future scripts or templates as inputs.

You can execute an ARM template via the Azure Portal, Azure CLI, PowerShell, the REST API, via a GitHub Repository or by using the Azure cloud Shell. Generally the best practice approach is to have a CI/CD pipeline execute your templates and have the templates themselves stored in source control and provided as an imput to the pipeline as an artifact. By using a CI/CD pipeline you can create other automation around the template deployment to pull the input values needed for a specific environment from a configuration store.

ARM templates can be intimidating to get started with because JSON is quite a complex format. Azure makes getting started with ARM templates easier by allowing you to export an ARM template for resources you have initially deployed. These exports can themselves be more verbose than is needed, but can be a good starting point. Good tooling is also a must, such as using the ARM Template extension in VSCode which can identify issues in your template before you execute them.

Here is a simple ARM template example:

~~~js
// file: "azuredeploy.json"
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "storageAccountName": {
      "type": "string",
      "metadata": {
        "description": "Specifies the name of the Azure Storage account."
      }
    },
    "containerName": {
      "type": "string",
      "defaultValue": "logs",
      "metadata": {
        "description": "Specifies the name of the blob container."
      }
    },
    "location": {
      "type": "string",
      "defaultValue": "[resourceGroup().location]",
      "metadata": {
        "description": "Specifies the location in which the Azure Storage resources should be deployed."
      }
    }
  },
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2019-06-01",
      "name": "[parameters('storageAccountName')]",
      "location": "[parameters('location')]",
      "sku": {
        "name": "Standard_LRS",
        "tier": "Standard"
      },
      "kind": "StorageV2",
      "properties": {
        "accessTier": "Hot"
      },
    }
  ]
}
~~~

One of the main issues with ARM templates historically has been that you couldn't easily preview what changes a deployment was going to make before executing it. Azure have recently added a `-WhatIf` function to ARM deployments that does give you a detailed output of what the deployment would change. However this feature is still in preview and isn't always 100% accurate.

## Terraform

[Terraform](https://www.terraform.io/) is an infrastructure as code tool by Hashicorp. Terraform is cloud agnostic, which means you can use the same language (HCL - Hashicorp Configuration Language) to deploy resources across a multitude of cloud providers. That is not to say that the exact same Terraform template would work across multiple cloud providers, the resources themselves often still require configuration settings that are provider specific, but using the same tooling and language can still be beneficial if you are multi-cloud.

Here is a simple Terraform example:

~~~terraform
// file: main.tf
resource "azurerm_resource_group" "example" {
  name     = "example-resources"
  location = "West Europe"
}

resource "azurerm_storage_account" "example" {
  name                     = "storageaccountname"
  resource_group_name      = azurerm_resource_group.example.name
  location                 = azurerm_resource_group.example.location
  account_tier             = "Standard"
  account_replication_type = "GRS"

  tags = {
    environment = "staging"
  }
}
~~~

The Terraform language is much less verbose than the JSON of ARM templates and so can be easier to get started with, is more readable and easier to maintain. Terraform also allows you to preview your changes prior to executing them. It does this by maintaining a state while which is updated when your template is executed with the current state of resources. Maintaining this state file can become a challenge when a team needs to work on the same resources. When collaborating its best practice to store the state remotely, such as in an Azure Blob Storage account. Because Terraform is a third party tool it can also lag behind when new Azure resources are released.

## Bicep

[Bicep](https://github.com/Azure/bicep) is a DSL (Domain Specific Language) for deploying Azure resources. The intention of Bicep is to drastically simplify the template authoring experience by providing a cleaner syntax than you get with native ARM templates. Bicep is a transparent abstraction over ARM, so anything you can do in ARM templates should be possible in Bicep. Bicep templates transpiled into standard ARM template JSON files, so ultimately the deployment approach is the same.

Here is a simple Bicep example:

~~~terraform
// file: "main.bicep"
param location string = 'eastus'

@minLength(3)
@maxLength(24)
param storageAccountName string = 'uniquestorage001'

var storageSku = 'Standard_LRS' // declare variable and assign value

resource stg 'Microsoft.Storage/storageAccounts@2019-06-01' = {
  name: storageAccountName
  location: location
  kind: 'Storage'
  sku: {
    name: storageSku // reference variable
  }
}

output storageId string = stg.id // output resourceId of storage account
~~~

Bicep is in preview and the current release has some known limitations. It may therefore not be suitable for production deployments yet, but Microsoft do seem serious about its development as Bicep examples are already being included throughout the Azure documentation. 

## PSArm

[PSArm](https://github.com/PowerShell/PSArm) is an experimental PowerShell module that (like Bicep) also provide a DSL for deploying ARM templates. Where PSArm differs to Bicep is that its embedded within PowerShell, so it allows you to delcare Azure resources within what to many will already be a familiar scripting framework. Some of the benefits of working in this way are:

- Ability to integrate wth PowerShell's existing command completion functionality to make discoverability of the PSArm lanaguage concepts easier.
- Reuse existing PowerShell concepts such as piping, `foreach` and `foreach-object` to create concise, dynamic templates.
- Use PowerShell's whitespace-aware syntax to create clean templates but with the ability to add comments.

Here is a simple PSArm example:

```powershell
// file: "storage.psarm.ps1"
param(
  [Parameter(Mandatory)]
  [string]
  $StorageAccountName,

  [Parameter()]
  [ValidateSet('WestUS2', 'CentralUS')]
  [string]
  $Location = 'WestUS2'
)

Arm {
  param(
    [ValidateSet('Hot', 'Cool', 'Archive')]
    [ArmParameter[string]]
    $accessTier = 'Hot',

    [ArmParameter[int]]
    $allowPublicAccess,

    [ArmParameter[int]]
    $httpsOnly,

    [ArmParameter[string]]
    $deploymentTime = (utcNow),

    [ArmVariable]
    $timePlus3 = (dateTimeAdd $deploymentTime 'PT3H')
  )

  Resource $StorageAccountName -Namespace Microsoft.Storage -Type storageAccounts -ApiVersion 2019-06-01 -Kind StorageV2 -Location $Location {
    ArmSku Standard_LRS
    properties {
      accessTier $accessTier
      supportsHTTPSTrafficOnly $httpsOnly
      allowBlobPublicAccess $allowPublicAccess
      allowSharedKeyAccess 1
    }
  }

  Output 'deploymentTime' -Type string -Value $deploymentTime
  Output 'timePlus3' -Type string -Value $timePlus3
}
```

PSArm has only been publicly available since March 2021, and its label as "experiemental" probably means you should invest in it with caution. Like Bicep its probably best not to use it for production deployments yet, but its definitely one to watch (and try!) as it continues to improve and develop.