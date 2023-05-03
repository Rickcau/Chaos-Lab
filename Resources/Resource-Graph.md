---
layout: page
title: Resource Graph
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/CResourceGraph
---

# Azure Resource Graph
Azure Resource Graph is a service that allows you to search and query all of your Azure resources across multiple subscriptions and tenants. It helps you to quickly find and analyze resources, and to identify security risks and compliance issues. You can use Resource Graph to create custom reports and dashboards, and to automate resource management tasks.

We can leverage Azure Resourrce Graph to enumerate Chaos Studio details.  

## Azure Graph queries for Chaos Studio
1. Enumerate all the enabled Chaos Targets for a subscription

       az graph query -q "chaosresources | where type == 'microsoft.chaos/targets' | where subscriptionId == 'YourSubscriptionID'" 

2. Enumerate all all the capabilities for a subscription
       
       az graph query -q "ChaosResources | where type == 'microsoft.chaos/targets/capabilities' | where subscriptionId == 'mySubscriptionID'"
       
**Note:** You can enumerate the Targets and Capabilities in the Azure Portal under the Chaos Studio blade, but if for any reason there are issues with the portal, this approach can be used.

