---
layout: page
title: Chaos Studio Permissions
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/Permissions/
---

# **Chaos Studio Permissions**
For those of you that want granular control over the permissions for Chaos you will need to create a custom role.  We will outline the ARM operations, roles and walk through some examples, as well as point you to official Microsoft Documentation.  There are other roles/permissions that you will need based on what is that your experiment is doing i.e. with working with NSGs or VMs etc.

## ARM Operations and roles

| Operation | Description |
| ----- | ----- |
| Microsoft.Chaos/targets/[Read,Write,Delete] | Get, create, update, or delete a target. | 
| Microsoft.Chaos/targets/capabilities/[Read,Write,Delete] | Get, create, update, or delete a capability. |
| Microsoft.Chaos/locations/targetTypes/Read | Get all target types. |
| Microsoft.Chaos/locations/targetTypes/capabilityTypes/Read | Get all capability types. |
| Microsoft.Chaos/experiments/[Read,Write,Delete] | 	Get, create, update, or delete a chaos experiment. |
| Microsoft.Chaos/experiments/start/action | 	Start a chaos experiment. |
| Microsoft.Chaos/experiments/cancel/action | Stop a chaos experiment. | 
| Microsoft.Chaos/experiments/statuses/Read | Get the execution status for a run of a chaos experiment. |
| Microsoft.Chaos/experiments/executionDetails/Read | Get the execution details (status and errors for each action) for a run of a chaos experiment. |

For example you might only want to allow a select group of individuals to Start and Stop experiments.  In this case you would create a custom role that only allows:

   ~~~
      Microsoft.Chaos/experiments/start
      Microsoft.Chaos/experiments/cancel/action
      Microsoft.Chaos/experiments/Read
      Microsoft.Chaos/experiments/statuses/read
      Microsoft.Chaos/experiments/executionDetails/read
   ~~~
   
If you create such a role, the user would not be able to create experiments or perform any of the other operations if this is the only role assigned!  The user will also need the **Reader role**, otherwise the user will not be able to see the experiements.     

## Create a Custom Role
The Custom Role we are creating only allows permissions to **Read, Start and Stop/Cancel** experiments. 

1. Log in to Azure Portal and navigate to the subscription, and click on **Access control (IAM)**, then click on **Add > add custom role**, example below.<br>
![]({{ site.baseurl }}/assets/images/Custom-Role-Chaos-1.jpg)


2. Next, click on **Permissions**, then click on the **Add Permissions** button and add the permissions as outlined in the example below.<br>
![]({{ site.baseurl }}/assets/images/Custom-Role-Chaos-Add-Perms-2.jpg)

3. Now, you should be on the **Review + create** tab and there should be an **Add** button at the bottom of the page, as outlined in the example below, click add.<br>
![]({{ site.baseurl }}/assets/images/Custom-Role-Chaos-Add-Perms-3.jpg)

**Important Note**<br>
Later I went back and added the Microsoft.Chaos/experiemtnts/Read action to the role and the image above does not reflect that, so make sure you add this permission as well.  Also, it can take 5-20mins in some cases for the permissions to propagate across the system.  So, if you try to view experiments right away, you may not be able to, give it 20mins and then try again.

## Add the Custom Role to a User
Let's add the role to a user now so they have the proper permissions to view, start and stop experiments.

1. Navigate to the subscription and click on *Access Control (IAM)*, then click on Roles and search for the custom role and click on View as outlined in the example below.
![](({{ site.baseurl }}/assets/images/Chaos-Custom-Role-Selected.jpg)

2. Upon clicking on View, you will be presented with the following screen.
![](({{ site.baseurl }}/assets/images/Chaos-Custom-Role-View.jpg)

3. Now, click on Assignments, then + Add Assignments and add the users per the example below.
![](({{ site.baseurl }}/assets/images/Chaos-Custom-Role-Select-Member.jpg)
 



