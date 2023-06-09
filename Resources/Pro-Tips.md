---
layout: page
title: Pro Tips
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ProTips
---

# Pro Tips
## Targets and Capabilities are not enumerating in the portal
1. Select only one subscription and one resource group.

2. Use the Resource Graph Explorer to view the Targets and Capabilities.  
   [Click here](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade/){:target="_blank"} to open the Resource Graph Explorer in Azure Portal.  You will find several Chaos Studio Resource Query examples.

## How to deploy experiments if Azure Portal is not responsive?
1. You can deploy using Bicep.<br>
   [Click here]({{ site.baseurl }}/Lab%202%20Deploy%20Using%20Bicep.md){:target="_blank"} to learn more about how to deploy using Bicep.

## Experiencing failures or errors and the details are not very helpful?
1. Triple check your permissions<br>
   [Click here]({{ site.baseurl }}/Permissions.md){:target="_blank"} read up and learn how to check permissions.

2. Is the Chaos.Studio Provider enabled or did someone disable it?<br>
   [Click here]({{ site.baseurl }}/ChaosProvider.md){:target="_blank"} to learn more about how to check the Chaos.Studio Provider
   
## Getting Access Denied errors when running Experiments?
1. Double check the permissions for the Experiment.<br>
In **Lab 1**, I demonstrate this exact scenario and how the Experiment will fail with an “Access Denied” error.  The experiment needed *Network Contributor* permissions to create the fault.  

   Use [Lab 1]({{ site.baseurl }}/Labs/Lab%201%20NSG-Service-Bus.md) as an example to better understand what Roles/Permissions your Experiments need and then grant them as needed. 




