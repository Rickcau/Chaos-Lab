---
layout: default
title: Bicep - KM
permalink: /Chaos-Studio-Lab/KnowledgeMeasures/Deploy Using Bicep
parent: Knowledge Measures
nav_order: 6
---
# Knowledge Measure - Deploy Using Bicep
<p>1. Do you need VS Code to deploy the experiement using Bicep?
<details>
<summary>Answer</summary>
No, you can simply copy down the Biceap files and run them from the Azure CLI locally or via the Cloud Shell.
</details>
</p>
<br>

<p>2. Do you need Git installed to deploy the experiment?
<details>
<summary>Answer</summary>
No, you can simply copy down the Biceap files and run them from the Azure CLI locally or via the Portal.
</details>
</p>
<br>
<p>3. Do you need the Azure CLI installed?
<details>
<summary>Answer</summary>
If you plan to run the commands locally, otherwise you can use the Portal by copying the files into the Cloud Shell and running the commands from there.
</details>
</p>
<br>

<p>4. In what file or files are the NSG Capabilities and Targets enabled?
<details>
<summary>Answer</summary>
      NetworkSecurityGroup.becip
</details>
</p>
<br>

<p>5. Is there a new NSG rule created after the deployment is created?
<details>
<summary>Answer</summary>
    Yes
         <pre><code>
        {
              name: 'Allow-SSH'
              properties: {
                  priority: 100
                  direction: 'Inbound'
                  access: 'Allow'
                  protocol: 'Tcp'
                  sourceAddressPrefix: '*'
                  sourcePortRange: '*'
                  destinationAddressPrefix: '*'
                  destinationPortRange: '22'
              }
          }
      </code>
     </pre>
</details>
</p>
<br>

<p>6. Is there a Role Assignment needed in order for the Experiment to run?
<details>
<summary>Answer</summary>
   Yes, Network Contributor
</details>
</p>
<br>

<p>7. Does the Main.bicep file require you to pass in parameters?
<details>
<summary>Answer</summary>
   No, if no parameters are pass in, it will use default values.
</details>
</p>
<br>

<p>8. When using the *az deployment group create* to deploy the resources, do it automatically create a role assignment?
<details>
<summary>Answer</summary>
   Yes
</details>
</p>
<br>

<p>9.  What resouce types are required in order to create a role assignement?
<details>
<summary>Answer</summary>
        Microsoft.Authorization/roleDefinitions<br>
        Microsoft.Authorization/roleAssignments
</details>
</p>
<br>

<p>10.  Which two modules are required in order for the Main.bicep file to work properly?
<details>
<summary>Answer</summary>
Experiment.BICEP and NetworkSecurityGroup.BICEP. 
</details>
</p>
<br>
  