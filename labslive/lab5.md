---
title: "Lab 5: Intelligent IVR using CCAI"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>
In this Lab, we will go through the tasks that are required to setup a simple flow and make a test call into the Contact Center.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-setting-up-a-simple-flow)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you to be familiar with the control hub and admin portal UI. 
- The lab contains multiple exercises on Control Hub and Admin Portal to make you comfortable with the Webex Contact Center application.

### Pre-requisites

- You have an assigned POD and attendee ID
- You have the customer admin login credentials
- You have the calling DNIS
- You have the agent's extension number

### Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**

# Lab

## Video: BONUS Lab 5 - Intelligent IVR and CCAI

> The following video outlines the process to create a simple flow. The video uses a generic example. You will use the naming convention of `EP_<ID>_wxcclab` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/j78p-gxeTaE?rel=0" title="WxCC Lab 5 : CCAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.
---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1_\<POD-ID\>@email.carehybrid.com   | 3001 |

**NOTE:**

Your \<ID\> is your `Attendee ID` provided in the email visible as the **"Attendee ID"** line.

## Detailed Steps

### 1. Setup the Google CCAI voice bot

- Open the Control Hub Admin (admin.webex.com) > Contact Center Settings > Features > New Template > Virtual Bot > Use for Voice (You can enable it for Chat as well, if you’d like)
- Click on the next prompt and select “Yes, I have a preconfigured Dialogflow agent.” - 
Note: We will use a preconfigured bot for this exercise. This bot has been tied to an already existing paid account on https://dialogflow.cloud.google.com/ 
- Click on Next if it prompts you to download the Intents. We have already uploaded these for you.
- When it asks for the Upload JSON key – upload the file provided: ciscolive-ccai.json
- When it asks for a name – name the bot: CLUS_CCAI_Bot
- Click on Next > Skip the avatar section > Click Finish.
Note: The DialogFlow agent’s credentials are created on the DialogFlow API of the project on Gooogle Cloud Console. We need the DialogFlow API as well as the TTS API enabled on the account, along with the DialogFlow API Admin role. This has already been done for you and which is why just uploading the key provided is sufficient.

### 2. Wire up the DialogFlow Agent inside of the Flow.

- In Flow Designer – Remove the menu block and the welcome message block. We will use the CCAI Bot to front end the conversation, and then perform the lookup and send it to the queue.
- Put in the Virtual Agent block.
- For the Virtual Agent selection, select the CLUS_CCAI_Bot 
- Make Prompts Interruptible for the bot.
- Under the Advanced settings, ensure that “Enable Conversation Transcript” is checked. This will help the agent get a copy of the conversation with the customer. 
- Scroll down and configure the bot settings as detailed below

### 3. Configure the Settings for the Bot and the output connections

- The Bot has 2 connections – Handled and Escalated.
- Handled is meant to gracefully disconnect the call and end Self Service. Connect the handled branch to a play message block with “Thank you for calling” using a TTS Play Message block.
- Escalated is meant to send the call to the queue. Send the caller to a Queued block by connecting the escalated Intent to the queued block.
- 

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

- Use any of the trigger intents to get information about the lab:
“Cisco Live”
“Tell me about your lab”
“What labs are supported”
- Use any of the trigger intents to get to an agent: 
“I need Help”
“I need an Agent”
“Where is my proctor”
“Help”
“Assistance”, etc – these are the words that have utterances trained to trigger the escalation intent of the bot.

### 7. Have the Agent handle the call

- Have the agent go ready after you said “I need an agent”.
- The Agent should get the call, and be able to view the transcript on the agent desktop.

---

## Congratulations! You're All done with the Bonus Lab! 
## You are now ready to start the next Bonus Lab!
## [Lab 6: BONUS --> Outdial Lab](lab6.md)

## We hope you enjoyed the labs!

---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Adding Menu and Queue treatment to the call](lab2.md){:target="_blank"}
* [Lab 3: Advanced HTTP Request](lab3.md){:target="_blank"}
* [Lab 4: Skills Based Routing (SBR)](lab4.md){:target="_blank"}

### BONUS LABS

* [BONUS - Lab 5 : Intelligent IVR using CCAI](lab5.md)
* [BONUS - Lab 6 : Configuring Out-dial](lab6.md){:target="_blank"}