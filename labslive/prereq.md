---
title: "Important: Lab Pre-requisites"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

## Overview

In this section, we will go through the tasks that are required to complete the general pre-configuration of a tenant. These tasks are to be undertaken by a customer administrator. By following each of the steps, you would have prepped your tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to login an agent with the configured user extension.


The following video outlines the pre-requisites. These need to be complete before beginning the rest of the lab.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/PYI9ug4PH0o?rel=0" title="WxCC Pre-reqs: Pre-requisites" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

> 0:20 - Check User License

> 0:38 - Check the Directory Number

> 1:21 - Check Main Number and PSTN Connection

> 1:35 - Default PSTN Option for all Locations

> 1:52 - Hit Synchronize Users

## Summary

> Check your user credentials in the Lab Email you just received. Through the course of this lab you will use the user starting with admin1pod__@__

**Check Licenses**


1. Login to Control Hub > Users.
-	Ensure the agents have the contact center license selected and are properly configured as Contact center enabled on Webex Contact center.
- Ensure that they have activated the Email and are “Active” on Control Hub. 

**Check Webex Calling Settings**


2. Verify Webex Calling Settings
- Check that a "Main" number is assigned to Webex Calling.
- Check that the Calling Location is correctly set to "Intelepeer"


**Synchronize Users**

3. Synchronize users to get any newly activated users.
- Got to Contact Center > Settings > Synchronize Users

**Check Admin settings, Agent Settings, Site, Team Configuration**

4. Launch Portal to ensure the admin user admin1pod__@__ is Contact center configured for testing.
- A Site has been created for the Admin: `Cisco_Live`, `Team_CiscoLive`
- Ensure the Admin is Contact Center Enabled.
- Associate the User to the Site, Team, default Multimedia Profile - `Default_Telephony_Profile`.
- Verify by Launching the Agent Desktop and logging in.

Desktop URL: **https://desktop.wxcc-us1.cisco.com/**

> **Creating additional Agents:** You may create additional aliases using Mailinator (3rd party email alias generator) https://www.mailinator.com/

> Login to mailinator, create an inbox : username@mailinator.com will then be able to receive emails.

> Feel free to the user to Control Hub to add more users!

> Remember to Synchronize Users on Control Hub when adding new users.

5. Verify Webex Calling Installation

> **Participants can download and install the WebEx Calling App for Agents, Admins or Supervisors and make on-net calls.**

| **S.No** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1_\<POD-ID\>@email.carehybrid.com   | 3001 |


### Quick Links

> Control hub: **[https://admin.webex.com](https://admin.webex.com){:target="_blank"}**\
> Portal: **[https://portal.wxcc-us1.cisco.com/portal](https://portal.wxcc-us1.cisco.com/portal){:target="_blank"}**\
> Agent Desktop: **[https://desktop.wxcc-us1.cisco.com/](https://desktop.wxcc-us1.cisco.com/){:target="_blank"}**
> Mailinator: **[https://www.mailinator.com/](https://www.mailinator.com/){:target="_blank"}**

---
## You are now ready to Begin the Lab!
## [Lab 1: Setup A Simple Flow](lab1.md)


---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md)
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md)
* [Lab 2: Adding Menu and Queue treatment to the call](lab2.md)
* [Lab 3: Advanced HTTP Request](lab3.md)
* [Lab 4: Skills Based Routing (SBR)](lab4.md)

### BONUS LABS

* [BONUS - Lab 5 : Intelligent IVR using CCAI](lab5.md)
* [BONUS - Lab 6 : Configuring Out-dial](lab6.md)