---
layout: page
title: Pro Tips
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ProTips
---

# Pro Tips
In this section I will call some items that may be of help to you.

## Targets and Capabilities are not enumerating in the portal
This issue has occured in the past that the have been fixes deployed for this, but if this is blocking you, here are some things you can try to workaround this issue.

1. Select only one subscription and one resource group.

2. Use the Resource Graph Explorer to view the Targets and Capabilities.  

[Click here](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade){.target:=_blank} to open the Resource Graph Explorer in Azure Portal.

       az graph query -q "chaosresources | where type == 'microsoft.chaos/targets' | where subscriptionId == 'YourSubscriptionID'" 

2. Enumerate all all the capabilities for a subscription
       
       az graph query -q "ChaosResources | where type == 'microsoft.chaos/targets/capabilities' | where subscriptionId == 'mySubscriptionID'"
       
**Note:** You can enumerate the Targets and Capabilities in the Azure Portal under the Chaos Studio blade, but if for any reason there are issues with the portal, this approach can be used.


