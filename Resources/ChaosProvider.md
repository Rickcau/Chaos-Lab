---
layout: page
title: Register Microsoft.Chaos
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ChaosProvider/
---
# Register Microsoft.Chaos Studio Provider
***You will not be able to use Chaos Studio without registering the Microsoft.Chaos provider.  You will get errors when trying to enable targets & capabilities.  You must have a User account with Owner or Contributor Role in order to register the Microsoft.Chaos provider.***

[Click here](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-quickstart-azure-portal#register-the-chaos-studio-resource-provider){:target="_blank"}  for official documentation on registering the Microsoft.Chaos provider.

# Check to see of the Microsoft.Chaos Provider is registered using Azure CLI

**BASH**<br>
Open an Azure CLI prompt or open the CLI shell and run the following  command:<br>

        az provider show --namespace 'Microsoft.Chaos' | grep registrationState

**Bash or PS**
      
        az provider show --namespace Microsoft.Chaos
        
 ![]({{ site.baseurl }}/assets/images/Chaos-Registered.jpg)

# Register Microsoft.Chaos Provider using Azure CLI
Run the following command from the Azure CLI or from the Cloud Shell in the portal:

       az provider register --namespace Microsoft.Chaos

# Portal - Check to see of the Microsoft.Chaos Provider is registered and if not register it
1. Search for Subscriptions and open the subscription management page.

2. Click on the subscription where you will be using Chaos Studio.

3. In the left-hand navigation, click on Resource providers.

4. In the list of resource providers that appears, search for Microsoft.Chaos.

5. Click on the Microsoft.Chaos provider, and click the Register button.
![]({{ site.baseurl }}/assets/images/Chaos-Register-Portal.jpg)

