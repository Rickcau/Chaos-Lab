---
layout: page
title: Pro Tips
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ProTips
---

# Pro Tips
## Targets and Capabilities are not enumerating in the portal
This issue has occured in the past that the have been fixes deployed for this, but if this is blocking you, here are some things you can try to workaround this issue.

1. Select only one subscription and one resource group.

2. Use the Resource Graph Explorer to view the Targets and Capabilities.  
   [Click here](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade/){:target="_blank"} to open the Resource Graph Explorer in Azure Portal.  You will find several Chaos Studio Resource Query examples.

## How to deploy experiments if Azure Portal is not responsive?

1. You can deploy using Bicep.
   [Click here]({{ site.baseurl }}/Labs/NSG-Service-Bus-Lab2.markdown)){:target="_blank"} to learn more about how to deploy using Bicep.
**Note:** You can enumerate the Targets and Capabilities in the Azure Portal under the Chaos Studio blade, but if for any reason there are issues with the portal, this approach can be used.


