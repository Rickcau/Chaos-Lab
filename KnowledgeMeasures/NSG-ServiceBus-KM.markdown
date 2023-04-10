---
layout: default
title: NSG Service Bus - KM
permalink: /Chaos-Studio-Lab/KnowledgeMeasures/NSG-Service-Bus
parent: Knowledge Measures
nav_order: 6
---
# Knowledge Measure - NSG Service Bus Lab - Manually create the Experiement
<p>1. Once the NSG is created, there are two very important steps needed prior to running the Experiment.  What are they?
<details>
<summary>Answer</summary>
You need to enable the target and capabilities for the NSG.
</details>
</p>
<br>

<p>2. Will the experiement run if the target and capabilities are not enabled?
<details>
<summary>Answer</summary>
No!
</details>
</p>
<br>
<p>3. Are there any role assignments needed in order for the experiement to run?
<details>
<summary>Answer</summary>
Yes. You need to navigate to the NSG and create a Role Assignment for the Experiement and grant it Network Contributor.
</details>
</p>
<br>

<p>4. In order to target Service Bus, what property do we use and can we use a Service Tag for this?
<details>
<summary>Answer</summary>
      The property we need to set in the fault is <b>destinationAddresses</b> and yes, we use the service tag <b>ServiceBus</b> in order to target the Service Bus IP addresses.
</details>
</p>
<br>

<p>5. Is the NSG Rule we created for Outbound or Inbound traffic?
<details>
<summary>Answer</summary>
    Outbound
</details>
</p>
<br>

<p>6. What would happen if we did not grant the Experiement Network Contributor to the NSG?
<details>
<summary>Answer</summary>
   The experiement would fail and in the error details it should say <b>access denied</b>!
</details>
</p>
<br>

<p>7. How long will the experiment run?
<details>
<summary>Answer</summary>
  10 minutes
</details>
</p>
<br>

<p>8. Can you use other service tags with an NSG Fault?
<details>
<summary>Answer</summary>
   Yes.
</details>
</p>
<br>

<p>9.  What is the name of the rule that gets created when the experiment runs?
<details>
<summary>Answer</summary>
  DenyAllOutBound
</details>
</p>
<br>

<p>10.  Does the DenyAllOutbound Service Bus rule get removed after the experiment finishes running?
<details>
<summary>Answer</summary>
Yes. 
</details>
</p>
<br>
  