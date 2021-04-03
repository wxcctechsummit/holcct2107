---
title: "Lab 1: Setup a Simple Flow and make a test call"
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

- This lab is designed to help you to make an end to end test call into the contact center. 
- The lab contains material to send the call to the agent desktop.

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

## Video: Lab 1 - Setting up a Simple Flow

> The following video outlines the process to create a simple flow. The video uses a generic example. You will use the naming convention of `EP_<ID>_wxcclab` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/EELO2flwwFc?rel=0" title="WxCC Lab 1: Setting up a Simple Flow" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.
---

| **User Role** | **User email**      | **User Extension**                   |
| ----------- | ----------------- | -------------------------------- |
| Agent        | agent1_\<ID\>@mailinator.com   | 1000 |
| Supervisor         | supervisor1_\<ID\>@mailinator.com  | 2000 |

**NOTE:**

Your \<ID\> is your `Attendee ID` provided in the email visible as the **"Attendee ID"** line.

## Detailed Steps

### 1. Verify that your users are ready to login

- With the steps outlined in the previous lab and recap above, you should now be able to login to the agent desktop.

### 2. Verify your inbound numbers are correctly setup on Calling

- The inbound Numbers need to be added on Control Hub.
- The telephony option on the location needs to be set to Intelepeer.
- Settings page needs to have Intelepeer configured for subsequent locations created.

### 3. Create an inbound Voice Entry Point and Voice Queue

- Login to Portal and create an inbound voice entry point and voice queue. (Provisioning > Entry Point / Queue). Create EP_voice_wxcclab and Q_voice_wxcclab respectively.
- Map the DN from Control Hub - that is assigned to Wx Calling - on the Entry Point Mappings page. (Proivisioning > Entry Point Mappings). Map the DN to EP_voice_wxcclab

### 4. Verify the Audio Prompts, Create the Entry Point flow.

- The audio prompts required for the script build out are wav files. The whole bundle of wav files can be found here.
- You may listen to the files to get an idea of the kind of flows being constructed in the later labs.
- To create a flow and have these wav files ready for use, ensure that these prompt files are already uploaded to the org.
- To upload the audio files, Go to Routing Strategy (from Portal) > Resources > Audio Files and ensure that the audio files are uploaded. (Browse > New > Upload the files)
- Then, you can go to flow to create the flow. Routing Strategy (from Portal) > Flow > New and create the new flow as described in the video above.

### 5. Configure and Publish the flow

- Configure the flow flow_wxcclab with a Play prompt - welcome message and queue block and play music block.
- Configure the Queue Block to Q_voice_wxcclab. Map the queue inside of the queue block.
- Configure the event flow under the queue - ensure they have end flow steps.
- Configure the play music to loop, and start 0, end 120 to play 2 minutes of music.
- Verify and publish the flow.

### 6. Configure the Entry Point Routing Strategy

- Configure the Open 24x7 routing strategy time of day on the Entry Point Routing strategy by selecting it on the Routing Strategies > EP_voice_wxcclab.
- Map the flow flow_wxcclab you just created in there.

### 7. Configure the Queue Routing Strategy

- Create the Queue routing strategy for Q_voice_wxcclab using a 24x7 open queue.
- Map the Team Team_wxcclab to the Queue. Your Agent will then login to that team to get the call.

### 8. Make a test call

- Login to the agent desktop into Team_wxcclab and go to a ready state.
- Dial the number using your cell. You should hear the welcome prompt and get the call on the agent desktop.

## Congratulations! You're done! 
## You are now ready to start the next Lab!
## [Lab 2: Adding Menu and Queue treatment to the call](lab2.md)


> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**
