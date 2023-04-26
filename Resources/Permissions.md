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
      Microsoft.Chaos/experiments/cancel
      Microsoft.Chaos/experiments/Read
   ~~~
   
If you create such a role, the user would not be able to create experiments or perform any of the other operations if this is the only role assigned!  The user will also need the **Reader role**, otherwise the user will not be able to see the experiements.     

## Create a Role that only allows Starting and Stopping of experiements

1. Log in to Azure Portal and navigate to the subscription, and click on **Access control (IAM)**, then click on **Add > add custom role**, example below.
![](/assets/images/Custom-Role-Chaos-1.jpg)

2. Next, click on **Permissions**, then click on the **Add Permissions** button and add the permissions as outlined in the example below.
![](/assets/images/Custom-Role-Chaos-Add-Perms-2.jpg)

3. Now, you should be on the **Review + create** tab there should be an **Add** button at the bottom of the page, as outlined in the example below, click add.
![](/assets/images/Custom-Role-Chaos-Add-Perms-3.jpg

Now, you have a custom role that has these permissions.  Later I went back and added the Microsoft.Chaos/experiemtnts/Read role and the image above does not reflect that, so make sure you add these permissions as well.
