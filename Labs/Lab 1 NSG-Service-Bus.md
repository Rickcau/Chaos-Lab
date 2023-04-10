---
layout: default
title: Lab 1 - NSG Service Bus Lab
permalink: /Chaos-Studio-Lab/Labs/NSG-ServiceBus
parent: Labs 
nav_order: 7
---
# Create an NSG based Experiment Manually
In this lab, I will walk you thought the process of manually creating all the resources needed to for an Experiment that allows you to trigger an NSG Fault. Depending on the fault type, the perminssions and roles needed to run the experiment will vary.

**Requirements**
- Completed all the steps outlined in the Prerequesites section to ensure Chaos Studio is properly setup. For details [click here.]({{ site.baseurl }}/Chaos-Studio-Lab/Prequisites/)

# Create a Resource group for our Experiment
1. Sign in to [Azure portal](https://portal.azure.com){:target="_blank"}

2. Select resource groups, then click create <br>
![]({{ site.baseurl }}/assets/images/Create-RG.jpg)
For the Resouce Group name, I used **rg-NSG-Chaos-Lab1**, I'd suggest you do the same as I will be using this resouce group in other exercises.

3. Select subscription and enter values and finish creating the Resource Group and use **rg-NSG-Chaos-Lab1** for the Resource Group name.
![]({{ site.baseurl }}/assets/images/RG-Finish-Creation.jpg)

# Create a new Network Security Group in the Resouce Group you just created
  **Note** make sure you are **NOT** creating a **(Classic) Network Security Group**
1. Navigate to the Azure Portal and search for **Network Security Groups** and click on **Create* and finish the creation using the following properties:
![]({{ site.baseurl }}/assets/images/NSG-Create.jpg)

   **Note** how I used **nsg-Chaos-Lab1** for the NSG name and I selected the **rg-NSG-Chaos-Lab1** resource group we created in the previous step.

# Now we need to enable the NSG as target and enable the capabilities for it  Capability
1. Navigate the the Azure Portal and search for **Chaos Studio** and open it

2. Click on **Targets** and you will see a list of resouces that we can enable.
![]({{ site.baseurl }}/assets/images/Chaos-Targets.jpg)

    **Note** that for **nsg-Chaos-Lab1** it displays **Not Enabled** in the **Service Direct** column and **Manage Actions** is disabled?  This is **very** important to make note of, if the proper targets/capabilities are not enabled you are going to have issues.  Notice for **nsg-Chaos-Lab1** it displays **Enabled** in the **Service Direct** column and **Manage Actions** is enabled?  Now, we need to do this for the **nsg-Chaos-Lab1**.

3. Click on **nsg-Chaos-Lab1** and make sure it is selected and it is checked, then click on **Enable service-direct targets**, then click on **Review+Enable** then click on **Enabled**
![]({{ site.baseurl }}/assets/images/Chaos-Enable-ServiceDirect.jpg)

4. Now, refresh the page and **Manage Actions** will be enabled, click on it.  You will note that two **Capabilities** are selected, now click on **Save**
![]({{ site.baseurl }}/assets/images/Chaos-Capability.jpg)

   **Note** now the the NSG target and capabilities are enabled, we can create the **Experiment**.

# Now, lets create an Experiment that introduces an NSG Fault for Service Bus
1. Click on **Experiments**, then click on **Create** and populate the **Project Details** with the following values:
![]({{ site.baseurl }}/assets/images/Chaos-Exp-Create.jpg)

2. Click on **Review+Create**, then click on **Experiment Designer**, click on **Add Action -> Add Fault** and select **NSG Security Rule (version 1.1)** from the list of faults and set the **destinationAddresses** to **ServiceBus**.
![](/assets/images/Chaos-Exp-Add-Fault.jpg)

3. Now, click on **Next: Target resources >** and check **nsg-Chaos-Lab1** and click on **Add**. 
![]({{ site.baseurl }}/assets/images/Chaos-Exp-Add-Fault2.jpg)

4. Let's finish up by clicking on **Review + Create**, then **Create**.  Now, you will see your Experiment in the list of Experiments in **Chaos Studio**
![]({{ site.baseurl }}/assets/images/Chaos-Exp-Created.jpg)

# What happens if you run the experiement now?
Did the experiement fail?  Why did it fail?  **Hint:** The Experiment uses a **System Assigned Identity**.  Take a look at the error details for the failure.  Also, take a look at the role assignments for the experiment.  Is there anything missing?  Have you looked at the role assignments for the NSG?
![]({{ site.baseurl }}/assets/images/Chaos-Exp-Failed.jpg)

What might you do to fix this? **Hint:** In order to add a rule to an NSG what role assignment is needed?  Do some research and try to figure this out without looking at the answer below.  If you want the fix for the issue, click on the **Answer** for details.
<details>
<summary>Answer</summary>
You need to grant the experiment Network Contributor permissions to the NSG.  Navigate to the NSG and and Add the role assignment for Network Contributor and make sure you add exp-NSG-Chaos-Lab1 as a member.
</details>

Here is what the NSG should look like if you properly added the role assignment:
![]({{ site.baseurl }}/assets/images/Chaos-Exp-NetworkContrib.jpg)

# Run the Experiment now that we have added the proper Role Assignment
1. Navigate to the **exp-NSG-Chaos-Lab1** experiment and click **Start**.  Keep an eye on the **Status*, if you properly add the role assignment, the experiment should change to **Running* status.
![]({{ site.baseurl }}/assets/images/Chaos-Exp-Running.jpg)

2. Now, navigate to the **nsg-Chaos-Lab1**, you will see that a new rule called **DenyAllOutbound** has been added and it's denying traffic to ServiceBus!
![]({{ site.baseurl }}/assets/images/Chaos-NSG-Rule-Enabled.jpg)

# Congratulations!
You have just completed your first Chaos Studio Experiement that leverages an NSG Fault that Denies Service Bus Traffic
## Let's recap the important takeaways for this lab.
1. Experiments have a System Assigned Identity and each experiement needs to have the proper role assignments in order to run.
2. In this case, the experiement needed to be granted the **Network Contributor* role to the Network Security Group.
3. When the experiement runs, it will create a rule that denies traffic to range of IP addresses.  In order for the experiement to be able to create the Rule it needs Network Contributor to do this.

## Recap of the steps needed
1. Create a Resource Group to be used for the Experiement and NSG
2. Enable the Target/Capibilities for the NSG
3. Add the proper Role Assignment

These are the fundamental steps needed for service-direct faults and depending on the fault your role assignements may vary.

