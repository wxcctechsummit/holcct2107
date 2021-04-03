---
title: "Lab 3: Advanced Flows - HTTP Requests"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>
In this Lab, we will go through the tasks that are required to setup the HTTP Request block on Flow Designer and perform advanced data manipulation.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-setting-up-a-simple-flow)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you understand Flow Designer and the HTTP Requests within Flow. 
- This lab will get you familiar with reading JSON as a data interchange format within Flow Designer to send information to the Agent desktop.

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

## Video: Setting up a Simple Flow

> The following video outlines the process to create a simple flow. The video uses a generic example. You will use the naming convention of `EP_<ID>_wxcclab` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/WVGACrbLxp0?rel=0" title="WxCC Lab 3: HTTP Request" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. The steps are detailed below the video if you would like a snapshot of what configuration is required.
---

| **User Role** | **User email**      | **User Extension**                   |
| ----------- | ----------------- | -------------------------------- |
| Agent        | agent1_\<ID\>@mailinator.com   | 1000 |
| Supervisor         | supervisor1_\<ID\>@mailinator.com  | 2000 |

**NOTE:**

Your \<ID\> is your `Attendee ID` provided in the email visible as the **"Attendee ID"** line.

## Detailed Steps

### 1. Copy out the flow and configure the advanced flow 2

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow advanced_flow1_wxcclab and edit the copied flow - name it advanced_flow2_wxcclab
- Edit the flow to go into flow designer.

### 2. Enhance the existing flow with an authentication piece

- Drag a play message block, Collect Digits, HTTP Request, Condition Block, 2 more Play message blocks and put them in front of the menu step.
- Ensure the prompts are plugged in to the play message prompts. welcome, enter_pin, and after the HTTP and Condition, a corresponding success and failure prompt.

### 3. Configure the Collect Digits block

- Configure the Collect Digits Block to a 5 digits max/min and ensure the timeouts are properly setup.

### 4. Configure the custom variables and the HTTP Request Block

- Create 3 Custom variables - mark them CAD variables - with names customerName,customerEmail ,customerAccount with labels Name, Email, Account and values of None OR Unavailable OR null - (depends on what you prefer as the default for the agents to see if no info is available in the data dip)
- The request we will construct is : HTTPS GET -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716
- Use the variable from the CollectDigits1.EnteredPIN variable to inject it in the pin lookup.
- We will construct it as follows

The HTTP Request URL : https://5f97898842706e0016957443.mockapi.io/crm/api/customers. 
Query Parameters: 
pin with value of the block 
(recheck your block variable name!) 
The type would be application/json 
The Parse settings would be : 
customerName with $.[0].name 
customerEmail with $.[0].email 
customerPhone with $.[0].phone

**Tech-Tip:** Here are some practice exercises you can try by going to jsonpath.com 

> - Go to https://5f97898842706e0016957443.mockapi.io/crm/api/customers 

> - Copy out the JSON into https://jsonpath.com on the left pane. 

> - Try out all of these to learn how JSON path works!


Query For 	Parse statement	Remarks
All Customers
	$.[0]
	
First Customer	$.[0]	
Last Customer	$.[-1:]	
First two customers	$.[0:2]	
Last two customers	$.[-2:]	
Second from last	$.[-2:-1]	
first customer	$.[0]	
All the names	$..name	
All the pins	$..pin	
All the customers who’s pin value is more than 70000 or 80000	$..[?(@.pin > 70000)]	
All details of customer with account number	$..[?(@.account == "87305901”)].*	
name of customer with account number	$.[?(@.account == "70579265")].name	
		

### 5. Configure the Conditional for Error Check

- Use the httpBlock.StatusCode variable to check the value retured.
- Note that the test API does not give a 404 but an empty list [] with a 200 when no match is found. However, this step is just to understand error handling and checking.
- Use the </> expression check on the condition and play success and failure prompts accordingly.
- Ensure all the settings per block are entered and properly setup.
- Validate and Publish the new script, correcting any errors that show up during validation.

### 6. Point to the New flow in the Routing Strategy

- Go to the routing Strategy page > Routing Strategy > EP_voice_wxcclab
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow advanced_flow2_wxcclab.

### 7. Verify the flow end to end

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Ensure you’re able to recieve the variables on the Agent Desktop.


## Congratulations! You're done! 
## You are now ready to start the next Lab!
## [Lab 4: Skills Based Routing](lab4.md)


> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**
