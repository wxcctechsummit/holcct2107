---
title: "Lab 4: Skills Based Routing"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>
In this Lab, we will go through the tasks that are required to setup Skills Based Routing on Webex Contact Center.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-setting-up-a-simple-flow)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you to configure Skils Based Routign on Webex Contact Center. 
- At the end of the lab, you will be able to routing calls using Skill based routing by assigning agent skill requirements for the call.

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

## Video: Lab 4 - Skills Based Routing

> The following video outlines the process to create a simple flow. The video uses a generic example. You will use the naming convention of `EP_<ID>_wxcclab` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/6YoNyFGpAUQ?rel=0" title="WxCC Lab 4 : Skills Based Routing" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.
---

| **User Role** | **User email**      | **User Extension**                   |
| ----------- | ----------------- | -------------------------------- |
| Agent        | agent1_\<ID\>@mailinator.com   | 1000 |
| Supervisor         | supervisor1_\<ID\>@mailinator.com  | 2000 |

**NOTE:**

Your \<ID\> is your `Attendee ID` provided in the email visible as the **"Attendee ID"** line.

## Detailed Steps

### 1.Create Skill Definition

- Open portal-->Provisioning-->Skill-->skill Definition 
- Click (New Skill Creation) -->Give Name and Description 
- Type -->Text

### 2.Crete Skill Definition

- Open portal-->Provisioning-->Skill-->skill Profile
- Click (New Skill Profile) -->Give Name (Agent) and Description
- Under Active Skill select skill created in step 1
- Give Skill value as (Agent name : Agent 1)

### 3. Add skill profile to User/ Agent

- Open portal-->Users
- Edit user  -->under Skill Profile select the skill profile created in step 2

### 4.Create new Queue with Skill based routing and Add team 

- Open portal-->Provisioning-->Entry point/Queue -->Queue
- Create new Queue --> Give Name and Description
- Channel Type -->Telephony 
- Queue Routing Type -->Skill Based -->Best Available Agent 
- Add Team -->Team[podnumber]

### 5. Change the previous flow with Skill based routing queue 

- Open the Flow created before and click on Queue Contact node and change the queue to Skill based queue 
- Skill Requirement Details -->Select Skill and condition 
- Under value -->{{Agent}}

### 6. Make a call and test the flow 

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Ensure you’re able to recieve the variables on the Agent Desktop.

---

## Congratulations! You're done! 
## You are done with all the mandatory sections! Explore the bonus lab below!
## [BONUS -> Lab 5: Intelligent IVR using Contact Center AI](lab5.md)


> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**
---

## Index: Quick Links

* [Important: Pre-Requisites](labslive/prereq.md)
* [Lab 1: Setup a Simple Flow and make a test call](labslive/lab1.md)
* [Lab 2: Adding Menu and Queue treatment to the call](labslive/lab2.md)
* [Lab 3: Advanced HTTP Request](labslive/lab3.md)
* [Lab 4: Skills Based Routing (SBR)](labslive/lab4.md)
### BONUS LABS
* [BONUS - Lab 5 : Intelligent IVR using CCAI](labslive/lab5.md)
* [BONUS - Lab 6 : Configuring Out-dial](labslive/lab6.md)