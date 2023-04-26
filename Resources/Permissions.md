---
layout: page
title: Chaos Studio Permissions
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/Permissions/
---

# Chaos Studio Permissions
For those of you that want granular control over the permissions for Chaos you will need to create a custom role.  We will outline the ARM operations, roles and walk through some examples, as well as point you to official Microsoft Documentation.  There are other roles/permissions that you will need based on what is that your experiment is doing i.e. with working with NSGs or VMs etc.

## ARM Operations and roles

| Operation | Description |
| --- | --- |
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
      Microsoft.Chaos/experiments/start/action
      Microsoft.Chaos/experiments/cancel/action
   ~~~
   
If you create such a role, the user would not be able to create experiments or perform any of the other operations!   

## Create a Role that only allows Starting and Stopping of experiements
      

       az vm extension list --resource-group <RESOURCE_GROUP_NAME> --vm-name <VM_NAME> <br>

The above command will return an empty result if no extenstions are installed, if extenstions are installed, results similiar to the following are returned:<br>
    
       [
        {
           "autoUpgradeMinorVersion": true,
           "enableAutomaticUpgrade": false,
           "forceUpdateTag": null,
           "id": "/subscriptions/<SUBSCRIPT_ID>/resourceGroups/vm-rdc-chaos_group/providers/Microsoft.Compute/virtualMachines/vm-rdc-chaos/extensions/ChaosAgent",
           "instanceView": null,
           "location": "eastus",
           "name": "ChaosAgent",
           "protectedSettings": null,
           "protectedSettingsFromKeyVault": null,
           "provisioningState": "Succeeded",
           "publisher": "Microsoft.Azure.Chaos",
           "resourceGroup": "vm-rdc-chaos_group",
           "settings": {
               "appinsightskey": "",
               "auth.msi.clientid": "<SOME_GUID>",
               "profile": "<PROFILE_GUID>"
         },
           "suppressFailures": null,
           "tags": null,
           "type": "Microsoft.Compute/virtualMachines/extensions",
           "typeHandlerVersion": "1.0",
           "typePropertiesType": "ChaosWindowsAgent"
         }
        ]
    
If you like to return only the details for the Chaos Agent Extension, you can run the following command: <br>

       az vm extension show -g <RESOURCE_GROUP_NAME> --vm-name <VM_NAME> -n ChaosAgent
      
