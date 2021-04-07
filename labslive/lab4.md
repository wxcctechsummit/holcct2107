---
title: "Lab 4: Skills Based Routing (SBR)"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

In this Lab, we will go through the tasks that are required to setup Skills Based Routing (SBR) on Webex Contact Center.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-lab-4---skills-based-routing)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you to configure Skils Based Routing on Webex Contact Center. 
- At the end of the lab, you will be able to routing calls using Skill based routing by assigning agent skill requirements for the call.

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

## Video: Lab 4 - Skills Based Routing

> The following video outlines the process to create a simple flow. The video uses a generic example. 

> You will use the naming convention of `EntryPoint_CL_Lab_<ID>` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/6YoNyFGpAUQ?rel=0" title="WxCC Lab 4 : Skills Based Routing" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 00:00 - 00 01 - Recap

> 00:01 -3:17 - Agenda

> 3:17 -  5:22 - Define Skill & Skill Profile 

> 5:23 - 5:53 - Tagging Skill Profile to User

> 5:54 - 7 30 - SBR Queue 

> 7:30 - 18:30 -Step Step Flow Building

> 18:31 - End   - Troubleshoot & Test the flow 

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.

## Steps


### 1.Create Skill Definition

- Open portal > Provisioning > Skill  > Skill Definition
- Click (New Skill Creation)  > Give Name(Agent_Profiency)and Description(Agent_Profiency) Type Proficiency
- Click (New Skill Creation)  > Give Name(Premium_Agent)and Description(Premium_Agent) Type `Text`

> **Note:** We are using "TEXT Skills" in this SBR lab so that you can directly target agents with a specific variable from flow. This gives powerful capabilities as you will see later.

### 2.Crete Skill Profile

- Open portal > Provisioning > Skill > skill Profile
- Click (New Skill Profile)  > Give Name (Cisco_Live_SP1) and Description(Cisco_Live_SP1) Select only Agent_Proficiency enter Skill Value to 5
- Click (New Skill Profile)  > Give Name (Cisco_Live_SP2) and Description(Cisco_Live_SP2) Select Agent_Proficiency enter Skill Value to 5 and Premium_Agent and enter Skill Value to Yes

### 3. Add skill profile to User/ Agent

- Open portal > Users
- Edit user  > under Skill Profile select the skill profile created in step 2 ((Cisco_Live_SP2)

### 4.Create new Queue with Skill based routing and Add team

- Open portal > Provisioning > Entry point/Queue  > Queue
- Create new Queue  >  Give Name and Description
- Channel Type  > Telephony
- Queue Routing Type  > Skill Based  > Best Available Agent
Add Team  > Team[Team_CiscoLive]

|Configuration field|	Value|
|----|---|
|Name	|Queue_SBR|
|Channel Type	|Telephony|
|*Contact Routing Settings*| 
|Queue Routing Type	|Skills Based|
|Agent Selection	|Best Available Agent|
|Call Distribution|	`<Add team>`|
|Service Level Threshold|	20|
|Maximum Time in Queue|	7200|
|Time Zone|	Default|


### 5. Change the previous flow with Skill based routing queue

- Open the Flow created before and click on Queue Contact node (Team1) and change the queue from Queue_Dummy to Queue_SBR
- Skill Requirement Details  > Select Skill and condition
Under value – Skill Requirements 

**Set the following settings**

> `Agent_Proficiency >= 4`

> `Premium_Agent` IS {% raw %}{{premium_cust_set}}{% endraw %}

> Enable Skill Relaxation After waiting in queue for: `15 seconds`

**Set skill requirements to:**

> `Agent_Proficiency >= 4`

### 6. Additional String Manipulation ! - CUSTOMER EMAIL CHECK

- Create Custom String variable, `Cust_Premium_check` and `Cust_Premium_check`.
- Drag and Drop Set Variable, Condition node and another Set Variable as explained in Video

- In the First set variable parse for email, use 

{% raw %}
'''{{ Customer_Email | split("@") | last }}'''
{% endraw %}

to parse the domain name of email

> **Note:** We used "" within the String hence we will need a new String wrapper of `'''String with "substring" to differentiate'''`

> The filter functions on Pebble templates has a lot of info. 

> [See Pebble Split Function](https://pebbletemplates.io/wiki/filter/split/){:target="_blank"}

> [See Pebble Last Filter](https://pebbletemplates.io/wiki/filter/last/){:target="_blank"}

>  In the Condition node, use this condition 


{% raw %}
{{Cust_premium_check =="gmail.com"}}
{% endraw %}

- If `True`, Set `Cust_premium_check` to `Yes` and connect it to main menu
- If `False`, connect it to main menu


### 7. Make a call and Test the end to end flow

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Call the Dial number > Enter 5 digit pin non premium agent ( `36238` ) >  On - Main Menu press 1 >  Call queued for 15 seconds and gets connected to agent
- Call the Dial number > Enter 5 digit pin premium agent ( `93752` ) >  On Main Menu press 1 >  Call gets connected to agent immediately

---

## Congratulations! You're done! 
## You are done with all the mandatory sections! Explore the bonus lab below!
## [BONUS - Lab 5: Intelligent IVR using Contact Center AI](lab5.md){:target="_blank"}


> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**
---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Add Menu and Queue treatment to the call](lab2.md){:target="_blank"}
* [Lab 3: Setup an advanced HTTP Request](lab3.md){:target="_blank"}
* [Lab 4: Setup Skills Based Routing (SBR)](lab4.md)

### BONUS LABS

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md){:target="_blank"}
* [BONUS - Lab 6 : Configure Out-dial](lab6.md){:target="_blank"}

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/labslive/lab5.html";}
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
  padding: 10px;">NEXT Lab 5: Configure CCAI Bots and TTS</button>
  
</div>