---
layout: page
title: Chaos Studio Agent
parent: Resources 
permalink: /Chaos-Studio-Lab/Resources/ChaosAgent/
---

# Chaos Agent
For Agent Based faults the Chaos Agent Extension needs to be installed on the VM.  For details on how to install the Chaos Agent Extension, you can follow the steps outline in the ***Enable chaos target, capabilities, and agent*** section of this [document](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-tutorial-agent-based-portal){:target="_blank"}.

## Useful Azure CLI commands

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
      
