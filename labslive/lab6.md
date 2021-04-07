---
title: "BONUS Lab 6: Configuring Outdial"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

In this Lab, we will go through the tasks that are required to setup an outdial call from the agent desktop in Webex Contact Center.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-bonus-lab-6---outdial-configuration)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to complete configuring the outdial capability on the Agent Desktop.
- At the end of the lab, your agent will be able to make an outbound call from the Agent Desktop.

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

> Mailinator (Can Be Used to Create a New User user@mailinator.com): **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**

# Lab

## Video: BONUS Lab 6 - Outdial Configuration

> The following video outlines the process to create a simple flow. The video uses a generic example. 

> You will use the naming convention of `EntryPoint_CL_Lab_<ID>` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/8IPR0WwFfCQ?rel=0" title="WxCC Lab 6: Outdial" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 00:00 — 0:21 — Overview

> 0:21 — 1:15 — Create Outdial Entry Point

> 1:15 — 2:20 — Create Outdial EP Routing Strategy

> 2:20 — 20:34 — Create Outdial ANI and OPTIONAL address books

> 3:45 — 4:40 — Setup Agent Profile

> 4:40 — End — Test Outdial
---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.

## Steps

### 1. Verify/create the Outdial Entry Point and Queue

- Login to Portal > Provisioning > Outdial Entry Point > Configure an Outdial Entry Point. 
- Verify you already have an outdial Queue configured on Portal > Provisioning > Outdial Queue.
- Ensure that the system created outdial entry points and queues are present and configure their settings.
- Alternatively, you can setup a new Outdial Entry Point as shown in the video.

### 2. Create the Outdial Entry Point Routing Strategy

- Go Routing Strategy > Outdial Entry Point-1 OR the One you just setup
- Configure the outdial entry point routing strategy to the script Outdial_EP.js which is the system default.
- Ensure the strategy time of day setting is correctly open 24x7 and marked default.

> **Note:** There are no more Queue Routing Strategies on the new Webex Contact Center.

### 3. Setup Your Agent Profile for Outdial

- Go to Provisioning > Agent Profiles > Select the Agent Profile and go to the Dial Plan tab.
- Configure all the Outdial settings on the dial plan as shown in the video.
- Attach the Outdial ANI, Address books etc. to the agent profile. Setup the Dial Plan Settings.

### 4. Test Outdial

- Logout/login the Agent on the agent desktop for the new agent profile settings to take effect.
- You should see the Outdial button and the agent is now able to make an outdial call.
- Test it by calling your cell or the provided Cisco Public Tollfree - `+18005536387` –Note: This will actually connect you to a live toll free number for Cisco Support!
- You should have all the connected call features pop on the agent desktop once the call is complete.

---

## Congratulations! You're All done with the Bonus Lab! 

---
> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](https://wxcctechsummit.github.io/holcct2107/)**

---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Add Menu and Queue treatment to the call](lab2.md){:target="_blank"}
* [Lab 3: Setup an advanced HTTP Request](lab3.md){:target="_blank"}
* [Lab 4: Setup Skills Based Routing (SBR)](lab4.md){:target="_blank"}

### BONUS LABS

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md){:target="_blank"}
* [BONUS - Lab 6 : Configure Out-dial](lab6.md)


<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
</script>

<div id="button-row">
	<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: #add8e6;
  padding: 10px;">Go Home</button>
  
</div>