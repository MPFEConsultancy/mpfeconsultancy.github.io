---
layout: post
title: Azure Cost Management
image: /assets/img/azure-cost-management.png
description: >
  One of the key advantages of Cloud Computing is that it is very easy to start deploying and using resources. However without careful management costs can quickly escalate. This article explores some of the ways in which Azure empowers you to monitor and control costs.
hide_last_modified: true
author: mark
---

> The best time to control your cloud computing costs was X years ago. The second best time is now.

When leveraging cloud computing it is important to give consideration to how you will monitor and control your costs. The best time to do this is as you first start to utilise the cloud, but if your initial focus was on velocity and experimentation you may now find yourself with a lot of uncontrolled expense, particularly if staff churn has occurred. In this article we will explore the tools and techniques you can use on Microsoft Azure to understand and (hopefully) reduce your costs.

# Use the Cost Management dashboard to understand your costs

- **Use the built in tools Azure provides to explore and understand your costs.**

Within the Azure Portal under All Services > Management and Governance you'll find Cost Management + Billing > Cost Management, within which there is Cost Analysis, Cost Alerts and Budgets. You can also get to these tools from the side bar of a Subscriptions or Resource Group, allowing you to quickly access cost information or configure alerts for a specific subset of resources.

![Azure Cost Management Portal](/assets/img/azure-cost-analysis.png)

The Cost Analysis tool allows you to access graphs or tables of information to understand your costs. By default you're shown the Accumulated Costs view, which shows you the current total cost for the month, how it has accumulated over that month and attempts to project what your cost will be by the end of the month based on the current trend:

You or may not find this view particularly useful, because a lot of cloud costs are consumption based they are rarely fixed and linear (or logarithmic). Switching to the Daily Cost view (click View > Daily Costs) can often be more informative as it shows you the last 30 days (or period of your choice) of cost per day, and then groups those costs by Resource Group. Note that the chart view will only show you the top 10 most expensive Resource Groups and then will group all others under an entry named "Other", which you can click on to drill into.

From the Daily Cost view you can get an immediate sense of where you most expensive resources are and how your costs fluctuate on a day to day basis. You can click on the graph to filter for specific Resource Groups. You can then change the "Group By" option to be "Resource", to see which specific resources are the most expensive within that Resource Group. 

![Azure Cost Management Portal Daily Costs](/assets/img/azure-cost-analysis-daily.png)

From the Subscription level it can also be informative to group your costs by "Service Name" to get a view of which types of services are you biggest costs, such as Virtual Machines, Networking or Storage.

# Ensure ownership and perform regular reviews

- **Have a technical resource be responsible for understanding and controlling costs so they are empowered to make changes quickly.**

It is important for someone to be responsible for the management of costs, and ideally that person (or people) should be able to both review costs and control them. In an ideal world, everyone would be responsible and motived to ensure that they were using the Cloud as efficiently as possible, but this is likely optimistic and you should be wary of a responsibility being so broadly applied that it ultimately ends up belonging to no one. Equally be wary of making the control of costs the responsibility of someone disconnected from the day to day work (such as a non-technical manager). This can cause friction as management (of course) want to drive down cost, but may lack understanding of why various cloud resources have been created, while the technical people want their resources to exist as simply and easily as possible to ease the flow of their technical work.

The role of DevOps Engineer can be well placed to manage Cloud costs, as they have a good understanding of the technical needs of the Development and Operations teams, develop automation that can simplify the creation or modification of resources and can (typically) directly execute changes to resources.

Azure provides a tool called Advisor that provides a list of recommendations to optimise costs based on the resources you have in your subscriptions. You can access this from Cost Management, or by searching in the portal for "Advisor" which can then show you cost recommendations across all of your subscriptions. I recommend checking Advisor on a regular basis, but be wary that it will make recommendations based on the patterns of usage its seen in the last 7, 30 or 60 days (you can select this "look back" period in Advisor and the recommendations will refresh accordingly). If your usage patterns are unpredictable then the recommendations may not always be useful, but they are always worth assessing, particularly because the Azure platform changes all the time and they can then alert you when new platform options may benefit you. Advisor will provide actionable suggestions such as resizing Virtual Machines, switching to or from autoscaling options (such as within Cosmos DB), enabling auto stop/start of VMs etc. 

# Configure budgets and billing alerts

- **Be alerted when costs become higher than expected.**

Depending on what kind of cloud resources you consume and how you use them, your costs may vary significantly from month to month. However it's likely that by reviewing historical trends you can get an idea of what normal costs look like. You may also have a specific corporate budget you are expected to operate within. Azure provides the ability to configure budgets and billing alerts in the Cost Management portal so that you can be informed during the month if your costs are starting to escalate close to or beyond your ideal maximum. Configuring these is very important to avoid being surprised by excessive costs at the end of a month and to give you an opportunity during the month to correct out of control costs by stopping, removing or scaling in resources.

To configure budgets go to Cost Management > Budgets. Click Add and fill in the details. You can create multiple budgets and use the filter option to scope them to different resource groups, resources, reservations etc. I recommend creating at a minimum a budget for the overall subscription costs. The budget tool shows the previous 6 months of costs and forecasts the next 6 months to help you to determine a suitable level, if you're confident the current historical levels of consumption are likely to remain valid. Once configured your budgets will also be visible in the cost analysis view.

![Azure Create Monthly Budget](/assets/img/azure-create-monthly-budget.png)

When configuring your budget/s ensure you also configure an alert. You can set this to trigger at a specific percentage of your budget, so for example if you want to be alerted when you have consumed 90% of your budget you can do so. These alerts can be linked to action groups which can then notify stakeholders by email, and/or can invoke a number of other actions such as running an azure automation / logic app / function that you might (for example) use to automatically scale in, stop or remove non-essential resources.

Don't forget to review your budgets regularly to make sure they remain sensible. If costs have decreased, reduce your budget accordingly.

# Fully automate the creation and destruction of your resources (and get good at it)

- **Use automation to create / destroy resources on demand.**

The easiest way to save money is to not spend money. One of the major benefits of the cloud is the ability to easily and fully automate the creation, configuration and destruction of resources. Have a look at my previous blog post for some of the [Infrastructure as Code tools that are available for Azure](https://mpfe.uk/blog/2021-05-01-Azure-infrastructure-as-code/). Obviously every implementation is different, but it's not unusual for a customer to require a series of non-Production environments that are used for testing changes into Production. Depending on how often you implement changes, running these environments at full scale full time may be wasteful. By utilising Infrastructure as Code and automation pipelines, you can make the creation and destruction of various resources a one-click or fully automated scheduled operation. Even the most complex environments can be deployed within a matter of hours and with suitable planning and automation in place this is unlikely to block the flow of work. The creation and destruction of resources could also form part of a testing pipeline, so that resources are deployed, automated tests run and then destroyed once complete.

Note that there may be some resources that are of no benefit to destroy if you've removed other resources that mean they won't be used. A good example of this is Log Analytics / Application Insights. If you are using the default retention periods (30 days for Log Analytics, 90 days for Application Insights), these only incur cost when log data is consumed, so if you've removed or stopped the resources that write into these, there may be little to no cost in keeping the historical data until it expires based on the retention.

You also may not wish to destroy resources that contain stores of data, such as databases or storage accounts if the contents of these are important or difficult to recreate. If this is the case then you can automate the scale in / down of these resources to ensure they are run as cheaply as possible. For example, scaling a SQL Server database down to the lowest tier (S0) results in a cost of about £12 a month, which is relatively insignificant and may be a cheaper / simpler option than taking and retaining a backup of the database.

# Ensure resource ownership

- **Use policy and alerting to ensure the purpose/ownership of all resources is clear.**

The ability to create resources quickly in the cloud means that development teams can easily self provision resources that they require as part of implementation or experimentation. The ability to self serve removes a lot of potentially wasted time moving work back and forth between teams (as it might have done in the past, when an infrastructure team would need to provision resources). However without suitable controls or monitoring in place, resources can easily be forgotten (long after an experiment is complete), ultimately resulting in the unnecessary consumption of cost.

Cloud providers recommend you implement a good tagging strategy as part of your cloud adoption. Tags can be assigned to all resources and can be any key/value that is useful to you to organise resources. You can use Azure Policy to create a tagging policy that will automatically apply tags during resource creation, or require that a value for certain tags be applied. For example you could create a policy that requires the completion of an "Owner" tag. Resources would fail to deploy without this tag.

If you are implementing controls on an already established environment, you may need to go through resources one at a time to identify and understand them, hopefully finding ones that can be eliminated along the way.

Azure Monitor features a sophisticated alerting tool. You can utilise this to create alerts on the creation of resource groups. Use this to ensure that appropriate stakeholders are made aware any time a new resource group is created (i.e such as your DevOps Engineers if they monitor and control costs). This can be important not only for cost management but for security, as you will want to know if any unexpected resource creation is occurring in your subscriptions and make sure any resources created are suitably secured. 

To configure such an alert, go to Azure Monitor > Alert > Alert Rules. Create a new Alert Rule and scope it to your subscription. Under condition select the signal called "Create Resource Group". For Action, select or create an action group that will notify the appropriate stakeholders (such as by email, or chat webhook).

![Azure Create Alert Rule for Create Resource Group activity](/assets/img/azure-create-alert-rule.png)

If you want to be notified (or have some other action occur) whenever any resource creation or modify operation occurs, you can configure an Alert Rule for the "Create Deployment" signal. Most changes (i.e even ones performed in the Portal) trigger an ARM deployment to occur, even if you haven't explicitly executed a template.

# Purchase reservations

- **Use reservations to get the best prices for resources you know you will need in the medium to long term.**

When you know that you will consistently need a service for the foreseeable future, purchasing a reservation can be a great way to reduce costs. You can buy 1 or 3 year reservations for services such as Virtual Machines, Databases and Storage. Purchasing a reservation can get you up to 72% cheaper prices than the pay as you go pricing. You're not entirely locked in either, if your needs change you can exchange a reservation for another of the same type (such as a different type of Virtual Machine) and also refund reservations up to $50k in a 12 month rolling window, if you no longer need it. Azure Advisor is a good place to look for potential reservations that may benefit you.

Azure recently introduced [Azure Savings Plan for Compute](https://learn.microsoft.com/en-us/azure/cost-management-billing/savings-plan/savings-plan-compute-overview), which is a more flexible way to make a reservation purchase than can save you up to 65% on pay as you go pricing. You commit to a certain hourly usage of compute which is then billed at a discounted price. If you use less than the commitment, you pay for the committed amount regardless. Usage above the commitment is billed at standard pay as you go pricing. The plan covers most Virtual Machine types, as well as App Service, Functions, Container Instances and Dedicated Host services. 

# Summary

To summarise, some key strategies you can employ to reduce your Azure costs include:

- Understand and monitor your costs, get alerts when your bill gets higher than expected. Make sure there's someone empowered to track and control costs.
- Automate, automate, automate the deployment _and_ destruction of resources so that you only run services when you need them.
- Be alerted when new resources are created / configure policies to ensure identifying ownership is required as part of deployment.
- Purchase reservations when you know you're going to have long term consistent usage.

If MPFE can be of any assistance in helping you understand, control or reduce your Azure costs, please [get in touch](enquiries@mpfe.uk).