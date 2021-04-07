---
title: "BONUS Lab 5: Intelligent IVR using CCAI"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

In this Lab, we will go through the tasks that are required to setup **Contact Center AI with the Voice Bot and Text-to-Speech (TTS) capabilities**.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-bonus-lab-5---intelligent-ivr-and-ccai)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you configure a Google DialogFlow Agent using CCAI (Contact Center AI) on Webex Contact Center and utilize TTS (Text-to-speech) capabilities.
- At the end of this lab, you should have a fully functioning bot front-ending the Webex Contact Center and text to speech prompts.

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

## Video: BONUS Lab 5 - Intelligent IVR and CCAI

> The following video outlines the process to create a simple flow. The video uses a generic example. 

> **[Download the TTS Connector here - holcct-2107-tts-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw)**

> **[Download the CCAI Bot Connector here - holcct-2107-ccai-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw)**

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/j78p-gxeTaE?rel=0" title="WxCC Lab 5 : CCAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Task 1 - CCAI BOT**
> 00:00 - 4.55 - Setting up the Google Account (DONE ALREADY)

> 4:55 - 5:15 - Configure TTS Connector

> **[Download the TTS Connector here - holcct-2107-tts-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw)**

> 5:15 - 5:20 - Create a new Virtual Agent

> **[Download the CCAI Bot Connector here - holcct-2107-ccai-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw)**

> 6:29 - 8:20 - Plug in the CCAI Bot

**Task 2 - TTS Connector, EWT & PIQ**

> 08:00 - 09:20 - Verify TTS connector

> 09:20 - 10:30 - Use a Set Variable Block to parse the email 

> 13:10 - End - Estimated Wait Time and Position in Queue

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.



## Video: BONUS Content - How the Bot is Configured on CCAI (DialogFlow)

> The following video outlines the process on how to create the CCAI Bot on Google dialog flow. This is purely for informational purposes only since a Cisco Billing account is used in the lab.

> **Note: You will not need to configure anything as a part of this section.**

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/9R2MMQhmUa8?rel=0" title="WxCC Lab 5 : CCAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 00:00 — 1:04 — Overview

> 1:04 — 2:45 — Team and Queue Creation

> 2:46 — 8:04 — Flow Demonstration/ Overview

> 8:05 — 20:34 — step by step procedure to develop the flow

> 20:35 — End — Troubleshoot & Test the flow 


---
## Congratulations! You're All done with the Bonus Lab! 
## You are now ready to start the next Bonus Lab!
## [Lab 6: BONUS - Configure Outdial](lab6.md){:target="_blank"}

## We hope you enjoyed the lab!

---
> #### Note: If you would like to go back **[HOME, CLICK HERE](index.md)**

---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Add Menu and Queue treatment to the call](lab2.md){:target="_blank"}
* [Lab 3: Setup an advanced HTTP Request](lab3.md){:target="_blank"}
* [Lab 4: Setup Skills Based Routing (SBR)](lab4.md){:target="_blank"}

### BONUS LABS

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md)
* [BONUS - Lab 6 : Configure Out-dial](lab6.md){:target="_blank"}

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/labslive/lab6.html";}
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
  padding: 10px;">NEXT Lab 6: Configure Outdial</button>
  
</div>