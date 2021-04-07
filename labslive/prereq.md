---
title: "LAB 0 - IMPORTANT: Lab Pre-requisites"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

## Overview

In this section, we will go through the tasks that are required to complete the general pre-configuration of a tenant. These tasks are to be undertaken by a customer administrator. By following each of the steps, you would have prepped your tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to login an agent with the configured user extension.

The following video outlines the pre-requisites. These need to be complete before beginning the rest of the lab.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/PYI9ug4PH0o?rel=0" title="WxCC Pre-reqs: Pre-requisites" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 0:20 - Check User License

> 0:38 - Check the Directory Number

> 1:21 - Check Main Number and PSTN Connection

> 1:35 - Default PSTN Option for all Locations

> 1:52 - Hit Synchronize Users

> 2:28 - Configure Admin User for Agent Login

> 2:52 - Verify Agent Login

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.

### Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**

---

## Summary

> Check your user credentials in the Lab Email you just received. Through the course of this lab you will use the user starting with admin1pod__@__

**Check Licenses**


### 1. Login to Control Hub > Users.
-	Ensure the agents have the contact center license selected and are properly configured as Contact center enabled on Webex Contact center.
- Ensure that they have activated the Email and are “Active” on Control Hub. 

**Check Webex Calling Settings**


### 2. Verify Webex Calling Settings
- Check that a "Main" number is assigned to Webex Calling.
- Check that the Calling Location is correctly set to "Intelepeer"


**Synchronize Users**

### 3. Synchronize users to get any newly activated users.
- Got to Contact Center > Settings > Synchronize Users

**Check Admin settings, Agent Settings, Site, Team Configuration**

### 4. Launch Portal to ensure the admin user admin1pod__@__ is Contact center configured for testing.

- A Site has been created for the Admin: `Cisco_Live`, `Team_CiscoLive`
- Ensure the Admin is Contact Center Enabled.
- Associate the User to the Site, Team, default Multimedia Profile - `Default_Telephony_Profile`.
- Verify by Launching the Agent Desktop and logging in.

Desktop URL: **https://desktop.wxcc-us1.cisco.com/**

### 5. Verify Webex Calling PC App Installation

> **Participants can download and install the WebEx Calling App for Agents, Admins or Supervisors and make on-net calls.**

**[Webex Calling PC APP - Download HERE !](https://cisco.app.box.com/s/fcbh0abcsruf5qxp99tj31ksx1bf2mh5){:target="_blank"}**

> You will use the extension configured on Webex Calling : 3001 - to login to the Agent Desktop

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1_\<POD-ID\>@email.carehybrid.com   | 3001 |

### 5. OPTIONAL : Creating More Users - Agents - Supervisors - For Test Calling INBOUND

- **Creating additional Agents OR Supervisors:** You may create additional aliases using Mailinator (3rd party email alias generator) **[https://www.mailinator.com/](https://www.mailinator.com/)**

- `These CAN be used for inbound call testing into the Contact Center : As Contact Center Customers!`

> Login to mailinator, create an inbox : `username@mailinator.com` will then be able to receive emails.

> Add the user to Control Hub Via > Control Hub > Users > Manage Users > Add via email : add the user_ID@mailinator.com

> Remember to `Click Synchronize Users` on Control Hub when adding new users!



---
## You are now ready to Begin the Lab!
## [Lab 1: Setup A Simple Flow](lab1.md)

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
* [BONUS - Lab 6 : Configure Out-dial](lab6.md){:target="_blank"}


<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/labslive/lab1.html";}
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
  padding: 10px;">NEXT Lab 1: Configuring a Simple Flow</button>
  
</div>