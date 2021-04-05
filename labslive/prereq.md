---
title: "Important: Lab Pre-requisites"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

## Overview

In this section, we will go through the tasks that are required to complete the general pre-configuration of a tenant. These tasks are to be undertaken by a customer administrator. By following each of the steps, you would have prepped your tenant to begin configuring different services offered by the platform. At the end of the lab, you should be able to login an agent with the configured user extension.


The following video outlines the pre-requisites. These need to be complete before beginning the rest of the lab.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/?rel=0" title="WxCC Pre-reqs: Pre-requisites" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

## Summary

1. Login to Control Hub > Users.

-	Ensure the agents have the contact center license selected and are properly configured as Contact center enabled on Webex Contact center.
- Ensure that they have activated the Email and are “Active” on Control Hub. 

2. Synchronize users to get any newly activated users.

- Got to Contact Center > Settings > Synchronize Users

3. Launch Portal to ensure all the users (admins, agents, supervisors) are contact center configured for testing.

- Create a Site : Site_wxcclab, Team_wxcclab
- Activate the agents to be Contact Center Enabled.
- Associate the Agents to the Site, Team, default Multimedia Profile - Default_Telephony_Profile.
- Verify by Launching the Agent Desktop and logging in.

> **Participants can download and install the WebEx Calling App for Agents, Admins or Supervisors and make on-net calls.**

| **S.No** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Agent        | agent1_\<ID\>@mailinator.com   | 1000 |
| Supervisor         | supervisor1_\<ID\>@mailinator.com  | 2000 |


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