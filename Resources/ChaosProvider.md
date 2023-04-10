---
layout: page
title: Register Microsoft.Chaos
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ChaosProvider/
---
You will not be able to do anything useful if the Microsoft.Chaos provider is not registered and this has to be done at the subscription level.

# Check to see of the Microsoft.Chaos Provider is registered using Azure CLI
**BASH**<br>
Open an Azure CLI prompt or open the CLI shell and run the following  command:<br>
     ~~~
        az provider show --namespace 'Microsoft.Chaos' | grep registrationState
     ~~~

**Bash or PS**
      ~~~
       az provider show --namespace Microsoft.Chaos
       ![]({{site.baseurl}}/assets/images/Chaos-Registered.jpg/)
      ~~~

# Check to see of the Microsoft.Chaos Provider is registered via the Portal
1. Search for Subscriptions and open the subscription management page.

2. Click on the subscription where you will be using Chaos Studio.

3. In the left-hand navigation, click on Resource providers.

4. In the list of resource providers that appears, search for Microsoft.Chaos.

5. Click on the Microsoft.Chaos provider, and click the Register button.
[]({{site.baseurl}}/assets/images/Chaos-Register-Portal.jpg/)
