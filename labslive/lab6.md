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
- [Video: Lab Walkthrough](#Video-BONUS-Lab-6---Outdial-Configuration)
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
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**

# Lab

## Video: BONUS Lab 6 - Outdial Configuration

> The following video outlines the process to create a simple flow. The video uses a generic example. You will use the naming convention of `EP_<ID>_wxcclab` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/8IPR0WwFfCQ?rel=0" title="WxCC Lab 6: Outdial" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1_\<POD-ID\>@email.carehybrid.com   | 3001 |

**NOTE:**

Your \<ID\> is your `Attendee ID` provided in the email visible as the **"Attendee ID"** line.

## Detailed Steps

### 1. Verify/create the Outdial Entry Point and Queue

- Login to Portal > Provisioning > Outdial Entry Point / Outdial Queue.
- Ensure that the system created outdial entry points and queues are present and configure their settings.
- Go to Provisioning > Outdial ANI > Create an Outdial ANI on the setup by mapping it to your existing toll free.
- Go to Provisioning > Agent Profiles > Select the Agent Profile and go to the Dial Plan tab.
- Configure all the Outdial settings on the dial plan.

### 2. Create the Outdial Entry Point Routing Strategy

- Go Routing Strategy > Outdial Entry Point-1 and configure the outdial entry point routing strategy to the script Outdial_EP.js which is the system default.
- Ensure the strategy time of day setting is correctly open 24x7 and marked default.

### 3. Create the Outdial Queue Routing Strategy

- Go Routing Strategy > Outdial Queue-1 and configure the outdial queue routing strategy to map to the Team_wxcclab.

### 4. Test Outdial

- Logout/login the Agent on the agent desktop for the new agent profile settings to take effect.
- You should see the Outdial button and the agent is now able to make an outdial call.
- Test it by calling your cell or the provided Cisco Public Tollfree - +18005536387` –Note: This will actually connect you to the live toll free number!
- You should have all the connected call features pop on the agent desktop once the call is complete.

---

## Congratulations! You're All done with the Bonus Lab! 

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

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md){:target="_blank"}
* [BONUS - Lab 6 : Configure Out-dial](lab6.md)