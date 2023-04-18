---
layout: default
title: Lab 3 - CPU Pressure
permalink: /Chaos-Studio-Lab/Labs/CPU Pressure
parent: Labs 
nav_order: 9
---
# Overview
Faults fall into two categories; service-direct or agent-based.  Agent-based faults requires the installation of the Chaos Agent, unlike a service-direct fault.  A CPU Pressure fault is an **agent-based** fault, so we will need to install the Chaos Agent Extenstion on the VM. 





In this Lab we will build an experiment and applies CPU Pressure to a VM.  We will be used a Windows 10 VM for this exercise, but a Linux VM could be used. This experiement 
In this lab we will quickly deploy the same type of NSG Experment we did in the [NSG Lab]({{ site.baseurl }}/Labs/NSG-Service-Bus-Lab2.markdown) using one Azure command.  After we deploy the experiement we will take a look at the Bicep files and dive into those.  

The goal of this lab is to demostrate how easy it is to use Bicep to create an experiement that sets up everything for us, including the Network Contributor role assignment.

# Install VS Code and clone my Azure-Chaos-Studio Repo
1. Download and install VS Code by [clicking here](https://code.visualstudio.com/){:target="_blank"} 

2. Download and install Git by [clicking here](https://git-scm.com/download/win){:target="_blank"}

3. Install the Azure CLI Tool extension in VS Code.

4. Install the Bicep extension in VS Code

5. Navigate to my [Azure-Chaos-Studio](https://github.com/Rickcau/Azure-Chaos-Studio){:target="_blank"} repo and copy the URL so you can clone the repo in VS Code.  (Techncially, you can just copy the Bicep files to a local directory.)

6. Clone the repo in VS Code so you have a local copy on your computer.

If you are new to **VS Code** and **GitHub** and cloning repos, [read this guide](https://learn.microsoft.com/en-us/azure/developer/javascript/how-to/with-visual-studio-code/clone-github-repository?tabs=create-repo-command-palette%2Cinitialize-repo-activity-bar%2Ccreate-branch-command-palette%2Ccommit-changes-command-palette%2Cpush-command-palette){:target="_blank"} on the Microsoft Learn website to get started.

# Let's deploy the Experiment now using the Bicep files
1. Open the local repo folder for **Azure-Chaos-Studio** from VS Code.
![]({{ site.baseurl }}/assets/images/Open-Repro.jpg)

2. Open a terminal window in VS Code and change into the following directory on your computer:
   ~~~
     PS C:\Users\<YOUR USER ID>\<CLONE_DIRECTORY>Azure-Chaos-Studio\Experiments\NSG Faults\BICEPcls>
   ~~~

3. Log in to your Azure account by running the following command:
   ~~~
     az login
   ~~~

4. Create a new Resource Group by running the following command:
   ~~~
     az group create --location eastus --resource-group rg-chaos-bicep-lab2
   ~~~

5. Deploy the experiment by running the following command:
   ~~~
     az deployment group create --resource-group rg-chaos-bicep-lab2 --template-file main.bicep --parameters experimentPrefix=exp-bicep-lab2- networkSecurityGroupPrefix=nsg-bicep-lab2-
   ~~~

   **Note:**  Technically, *Main.bicep* does not need to be passed any parameters, by default it will set values for the *experimentPrefix* and *networkSeucruityGroupPrefix* if you do not pass them.

6. As the *Main.bicep* is being deployed, you notice the status displays as */Running*.  When it has completed, it will render some JSON data to the screen.  Make note of the property *provisioningState* if it was successful it will have a value of *Succeded*.
![]({{ site.baseurl }}/assets/images/Bicep-Completed.jpg) 

7. Now, navigate to the *Experiments* in *Chaos Studio* and search for an experiement with a prefix of *exp-bicep-lab2* and click *Start* to run the experiment.
Did the experiement run or did it fail?  
![]({{ site.baseurl }}/assets/images/Lab2-Failed.jpg)

Take a few minutes to try and figure out how to fix the issue and what you might change in the Bicep to fix it.  *Hint:* Marksman often do what to maintain their accuracy?



 


