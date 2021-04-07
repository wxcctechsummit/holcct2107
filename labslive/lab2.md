---
title: "Lab 2: Adding Menu and Queue treatment to the call"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

In this Lab, we will go through the tasks that are required to add additional functionality to the flow by adding a **Menu and Queue treatment to the call**.

# Table of Contents

- [Overview](#overview)
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#Video-Lab-2---Adding-Menu-And-Queue-Treatment)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you configure a Menu step in the call flow along with Queue Treatment. We will also configure counters and Opt-outs within the queue, along with Callbacks.
- At the end of this lab, you should be able to hear the Menu prompt, and Opt-out of queue settings in the flow, and send a courtesy callback call to the customer by picking a ready agent.

### Pre-requisites

- You have an assigned POD and Attendee ID (Refer to your Lab Details).
- You have the customer admin login credentials.
- You have the calling DNIS.
- You have the agent’s extension number.
- Prompt Wav files are uploaded, TEAM, SITE and USER are created. 

### Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**


# Lab

## Video: Lab 2 - Adding Menu and Queue Treatment

> The following video outlines the process of adding a Menu and Queue Treatment to the flow.

> You will use the naming convention of `EntryPoint_CL_Lab_<ID>` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/WnaVkrzcbWs?rel=0" title="WxCC Lab 2: Menu and Queue Treatment" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 00:00 — 1:04 — Overview

> 1:04 — 2:45 — Team and Queue Creation

> 2:46 — 8:04 — Flow Demonstration/ Overview

> 8:05 — 20:34 — step by step procedure to develop the flow

> 20:35 — End — Troubleshoot & Test the flow 

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.

## Steps

### 1. Copy out the flow and configure the advanced flow

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow flow_wxcclab and edit the copied flow - name it advanced_flow1_wxcclab
- Edit the flow to go into flow designer.
- Ensure that you configure the Menu steps with a 3 option - 2 queue, 1 Blind Transfer step.
- Ensure you configure all the fields in the menu step including the prompts and the entry timeout (requires you to explore all options on the step).
- Ensure you configure all the blind transfer location to Cisco Toll Free : +18005536387 –Note: This will actually connect you to the live toll free number!

### 2. Configure the Queue Treatment loop and Opt Out and Callback steps

- In Flow Designer - Configure the Queue treatment for the first queue. Use the queueCounter variable and configure the Opt out steps including the high volume message and the callback step.
- Configure the voicemail destination to the same external number above.
- Validate the flow and publish it.

### 3. Point to the New flow in the Routing Strategy

- Go to the routing Strategy page > Routing Strategy > EP_voice_wxcclab
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow advanced_flow1_wxcclab.

### 4. Test the end to end flow

- Login to the agent desktop and go Idle (Not Ready)
- Test Queue treatment by going not ready on the agent desktop.
- Call the main number on the entry point and go into the queue. You should hear the queue twice and then have an option to leave a callback.
- leave the callback and the call should end.

### 5. Execute the Callback
- Have the agent go ready after you left a callback.
- They should receive the callback call.

---

## Congratulations! You're done! 
## You are now ready to start the next Lab!
## [Lab 3: Add Advanced HTTP Request Capabilities](lab3.md){:target="_blank"}

---
> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**

---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Add Menu and Queue treatment to the call](lab2.md)
* [Lab 3: Setup an advanced HTTP Request](lab3.md){:target="_blank"}
* [Lab 4: Setup Skills Based Routing (SBR)](lab4.md){:target="_blank"}

### BONUS LABS

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md){:target="_blank"}
* [BONUS - Lab 6 : Configure Out-dial](lab6.md){:target="_blank"}

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/labslive/lab3.html";}
</script>

<div id="button-row">
	<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: #add8e6;
  padding: 10px;">Go Home</button>

 <button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: #add8e6;
  padding: 10px;">NEXT Lab 3: Configuring Advanced HTTP Request Block</button>
  
</div>