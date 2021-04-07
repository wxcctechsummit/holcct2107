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

> **[Download the TTS Connector here - holcct-2107-tts-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="_blank"}**

> **[Download the CCAI Bot Connector here - holcct-2107-ccai-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="_blank"}**

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/j78p-gxeTaE?rel=0" title="WxCC Lab 5 : CCAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Task 1 - CCAI BOT**
> 00:00 - 4.55 - Setting up the Google Account (DONE ALREADY)

> 4:55 - 5:15 - Configure TTS Connector

> **[Download the TTS Connector here - holcct-2107-tts-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="_blank"}**

> 5:15 - 5:20 - Create a new Virtual Agent

> **[Download the CCAI Bot Connector here - holcct-2107-ccai-connector.json](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="_blank"}**

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

## Steps - TASK 1 : CCAI

### 1. Setup the Google CCAI voice bot

- Open the Control Hub Admin (admin.webex.com) > Contact Center Settings > Features > New Template > Virtual Bot > Use for Voice (You can enable it for Chat as well, if you’d like)
- Click on the next prompt and select “Yes, I have a preconfigured Dialogflow agent.” - Note: We will use a preconfigured bot for this exercise. This bot has been tied to an already existing paid account on https://dialogflow.cloud.google.com/
- Click on Next if it prompts you to download the Intents. We have already uploaded these for you.
- When it asks for the Upload JSON key – upload the file provided: ciscolive-ccai.json
- When it asks for a name – name the bot: CLUS_CCAI_Bot
- Click on Next > Skip the avatar section > Click Finish. 

> **Note:** The DialogFlow agent’s credentials are created on the DialogFlow API of the project on Gooogle Cloud Console. 

> We need the `DialogFlow API` as well as the `TTS API` enabled on the account, along with the `DialogFlow API Admin role`. 

> This has already been done for you and which is why just uploading the key provided is sufficient.

> **[The Keys are in the Location - here](https://cisco.app.box.com/s/oakd708czpfe0cpcgc3fd08o7ulxd9hw){:target="_blank"}**


### 2. Wire up the DialogFlow Agent inside of the Flow.

- In Flow Designer – Remove the menu block and the welcome message block. - We will use the CCAI Bot to front end the conversation, and then perform the lookup and send it to the queue.
- Put in the Virtual Agent block.
- For the Virtual Agent selection, select the CLUS_CCAI_Bot
- Make Prompts Interruptible for the bot.
- Under the Advanced settings, ensure that “Enable Conversation Transcript” is checked. This will help the agent get a copy of the conversation with the customer.
- Scroll down and configure the bot settings as detailed below

### 3. Configure the Settings for the Bot and the output connections

- The Bot has 2 connections – Handled and Escalated.
- Handled is meant to gracefully disconnect the call and end Self Service. - Connect the handled branch to a play message block with “Thank you for calling” using a TTS Play Message block.
- Escalated is meant to send the call to the queue. Send the caller to a Queued block by connecting the escalated Intent to the queued block.

### 4. Store the bot variables as CAD variables for the screen pop

- The bot block (VirtualAgent1) has 2 variables : LastIntent and TranscriptURL
- We will store these in CAD variables and pop them on the agent desktop.
- Create 2 CAD variables called lastIntent and transcriptURL
- Use the set variables as shown in the example above to set these as CAD variables.
- This will ensure that when the call hits the agent, the agent is able to view these statistics. It is also helpful during debugging.

### 5. Test the end to end flow

- Login to the agent desktop and go Idle (Not Ready)
- Call the main number on the entry point.
- You should hear the bot asks you what you want to do. (e.g “How may I help you”)

### 6. Experiment with what the configured Bot can do

> **Note:** This simple bot has been programmed on DialogFlow to give you information about the Cisco Live Session Schedule as well as escalate the call to an agent).

- Use any of the trigger intents to get information about the lab: “Cisco - - Live” “Tell me about your lab” “What labs are supported”
- Use any of the trigger intents to get to an agent: “I need Help” “I need an Agent” “Where is my proctor” “Help” “Assistance”, etc – these are the words that have utterances trained to trigger the escalation intent of the bot.
### 7. Have the Agent handle the call
- Have the agent go ready after you said “I need an agent”.
- The Agent should get the call, and be able to view the transcript on the agent desktop.


## STEPS: Task 2 - TTS - EWT - PIQ

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/j78p-gxeTaE?rel=0&start=480" title="WxCC Lab 5 : CCAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**Timestamps**

> 08:00 - 09:20 - Verify TTS connector

> 09:20 - 10:30 - Use a Set Variable Block to parse the email 

> 13:10 - End - Estimated Wait Time and Position in Queue

### 1. Setup the Google CCAI TTS 

- Follow the Video above and ensure that the TTS Connector is already setup on your org.

### 2. Wire up the TTS in the Webex Contact Center Flow Designer

- Drag and Drop A Play message node, `Enable Test-to-Speech` and select the Connector , Select Language
- Under play message copy paste this test 

> “Thanks {{% raw %}} {{Customer_Name}} {{% endraw %}}, we got your information”

### 3 PIQ and EWT 

- Drag and drop Queueinfo node after “Team2 Queue Contact node”  play EWT and PIQ from success  link
- Play PIQ alone from the “Insufficient Information ” link 
- Connect Failure link to Play Music node 

### 4. Test the Call Flow with the latest additions

- Call the Dial number > Enter 5 digit pin > Heard personalized greeting
- On the Main Menu press 2 > PIQ is played > Call gets connected to agent Immediately


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
> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](https://wxcctechsummit.github.io/holcct2107/)**

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