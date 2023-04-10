---
layout: page
title: Prequisites
permalink: /Chaos-Studio-Lab/Prequisites/
nav_order: 3
---

# Make sure you have everything ready to start the workshop
Please make sure that you have completed the following requirements in order to complete the hands-on lab:

## Azure Requirements
- Access to Azure Portal
- Access to an Active Azure Subscription
- You need to have "Ower" or "Contributor" role or have been granted access to the Microsoft.Chaos via a custom role.  For more information on Chaos Studio permissions [click here](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-permissions-security){:target="_blank"}
- An existing resource group or create a new one to host your Chaos Studio instance
- Register the Chaos Studio resource provider.  For details on how to register the provider [click here](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-quickstart-azure-portal#register-the-chaos-studio-resource-provider){:target="_blank"}
- Enable Chaos Studio in your subscription.  For steps on how to do this [click here]({{ site.baseurl }}/Chaos-Studio-Lab/Resources/AzureChaosStudio-Creation/)

## Recommendations
- Use either your own or Azure’s common naming convention for the various resources you will be using.  For more details on Azure Best Practices for Resource Naming, [click here](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming){:target="_blank"}


## Note
There may be additional requirements depending on your specific use case, such as having **"Network Contributor"** role for NSG experiments or **"DB Owner"** for Cosmos DB Faults.  For the experiments outlined in the labs I will callout the requirements for each scenario. 

[Back to top](#top)
