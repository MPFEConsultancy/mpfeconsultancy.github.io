---
layout: post
title: Azure Cost Management
image: /assets/img/azure-cost-management.png
description: >
  One of the key advantages of Cloud Computing is that it is very easy to start deploying and using resources. However without careful management costs can quickly escalate. This article explores some of the ways in which Azure empowers you to monitor and control costs.
hide_last_modified: true
author: mark
---

> The best time to control your cloud computing costs was from day one. The second best time is now.

When leveraging cloud computing it is important to give consideration to how you will monitor and control your costs. The best time to do this is when you first start to utilise the cloud, the second best time is now (and it is of course never too late). In this article we will explore the tools and techniques you can use on Microsoft Azure to manage and (hopefully) reduce your costs.

# Use the Cost Management dashboard to understand your costs

Within the Azure Portal under All Services > Management and Governance you'll find Cost Management + Billing > Cost Management, within which there is Cost Analysis, Cost Alerts and Budgets. You can also get to these tools from the side bar of a Subscriptions or Resource Group, allowing you to quickly access cost information or configure alerts for a specific subset of resources.

The Cost Analysis tool allows you to access graphs or tables of information to understand your costs. By default you're shown the Accumulated Costs view, which shows you the current total cost for the month, how it has accumulated over that month and attempts to project what your cost will be by the end of the month based on the current trend. I don't generally find this view particularly useful, because a lot of cloud costs are consumption based they are rarely fixed and linear. I prefer the Daily Cost view (click View > Daily Costs) this shows you the last 30 days of cost per day, and then groups those costs by Resource Group. Note that it will show you the top 10 most expensive Resource Groups and then will group all others under an entry named "Other".

From the Daily Cost view you can get an immediate sense of where you most expensive resources are and how your costs fluctuate on a day to day basis. You can click on the graph to filter for specific Resource Groups. You can then change the "Group By" option to be "Resource", to see which specific resources are the most expensive within that Resource Group. From the Subscription level it can also be informative to group your costs by "Service Name" to get a view of which types of services are you biggest costs, such as Virtual Machines, Networking or Storage.

# Ensure ownership and perform regular reviews

- Have a technical resource be responsible for understanding and controlling costs so they are empowered to make changes quickly.

It is important for someone to be responsible for the management of costs, and ideally that person (or people) should be able to both review costs and control them. In an ideal world, everyone would be responsible and motived to ensure that they were using the Cloud as efficiently as possible, but in reality this is rarely the case and you should be wary of a responsibility being so broadly applied that it ultimately ends up belonging to no one. Equally be wary of making the control of costs the responsibility of the management team. This can have cause friction as management want to drive down cost without understanding why various cloud resources have been created, while the technical people want their resources to exist as simply and easily as possible to ease the flow of technical work.

The role of DevOps Engineer can be well placed to manage Cloud costs, as they have a good understanding of the technical needs of the Development and Operations teams, develop automation that can simplify the creation or modification of resources and can (typically) directly execute changes to resources.

Azure provides a tool within Cost Management called "Advisor Recommendations". This performs 

- Cost Advisor
- Automate: Use of PowerShell to total up costs for specific periods / perform comparisons

# Configure budgets and billing alerts



# Use multiple subscriptions as a way to organise and control costs



# Fully automate the creation and destruction of environments (and get good at it)



# Control waste



# Purchase Reservations

