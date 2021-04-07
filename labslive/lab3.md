---
title: "Lab 3: Advanced Flows - HTTP Requests"
---
<p align="center">
  <img src="https://ayankovs-ccp-s3.s3.eu-west-3.amazonaws.com/CiscoLiveLogo.jpg">
</p>

In this Lab, we will go through the tasks that are required to **Setup the HTTP Request block on Flow Designer** and perform advanced data manipulation.

# Table of Contents

- [Overview](#overview) 
  * [Lab Objective](#lab-objective)
  * [Pre-Requisites](#pre-requisites)
  * [Quick Links](#quick-links)
- [Video: Lab Walkthrough](#video-lab-3---advanced-http-request-and-expressions)
- [Detailed Steps](#detailed-steps)

# Overview

### Lab Objective

- This lab is designed to help you understand Flow Designer and the HTTP Requests within Flow.
- This lab will get you familiar with reading JSON as a data interchange format within Flow Designer to send information to the Agent desktop.

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

## Video: Lab 3 - Advanced HTTP Request and Expressions

> The following video outlines the process to create a simple flow. 

> You will use the naming convention of `EntryPoint_CL_Lab_<ID>` where `<ID>` is your attendee ID provided. This is to keep a track of all the configuration created end to end.

**E.g**: `If you are attendee 123 you would use EntryPoint_CL_Lab_123`

<iframe width="1024" height="576" src="https://www.youtube-nocookie.com/embed/WVGACrbLxp0?rel=0" title="WxCC Lab 3: HTTP Request" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> The video serves as a reference. View detailed steps in text below.

> **VIDEO TIMESTAMPS**

> 00:00 - 00:04 — Overview

> 04:00 - 18:00 — Step by Step Flow Building and Advanced HTTP Request

> 18:00 — 21:40 - Troubleshooting & Test the flow 

---

| **User Role** | **Contents**      | **Extension-DN Allotted**                   |
| ----------- | ----------------- | -------------------------------- |
| Admin        | admin1pod`<POD>`@email.carehybrid.com   | 3001 |

**NOTE:**
Your `<POD>` is your `POD ID` allocated.
## Steps

### 1. Copy out the flow and configure the advanced flow 2

- Open the Portal > Routing Strategy > Flow page.
- Copy the existing flow `Flow_Lab2_<ID>` and edit the copied flow - name it `Flow_Lab3_<ID>`
- Edit the flow to go into flow designer.

### 2. Enhance the existing flow with an authentication piece

- Drag a play message block, Collect Digits, HTTP Request, Condition Block, 2 more Play message blocks and put them in front of the menu step.
- Ensure the prompts are plugged in to the play message prompts. `welcome`, `enter_pin`, and after the HTTP and Condition, a corresponding success and failure prompt.

### 3. Configure the Collect Digits block

- Configure the Collect Digits Block to a 5 digits max/min and ensure the timeouts are properly setup.

### 4. Configure the custom variables and the HTTP Request Block

- Create 3 Custom variables - mark them CAD variables - with names `customer_Name`,`customer_Email` ,`customer_Account` with labels `Name`, `Email`, `Account` and values of `Unavailable` OR `null` - *(depends on what you prefer as the default for the agents to see if no info is available in the data dip)*

> The request we will construct is : 

> **HTTPS GET** -> https://5f97898842706e0016957443.mockapi.io/crm/api/customers?pin=18716

- Use the variable from the CollectDigits1.EnteredPIN variable to inject it in the pin lookup.
- We will construct it as follows

```
HTTP Request
GET https://5f97898842706e0016957443.mockapi.io/crm/api/customers

Query Parameters: 
pin with {{CollectDigits.DigitsEntered}} 

with value of the block (recheck your block variable name!) 

The type would be application/json 

The Parse settings would be : 
customerName = $.[0].name 
customerEmail = $.[0].email 
customerPhone = $.[0].phone
```

**Tech-Tip:** Here are some practice exercises you can try by going to jsonpath.com 

> - Go to https://5f97898842706e0016957443.mockapi.io/crm/api/customers 

> - Copy out the JSON into https://jsonpath.com on the left pane. 

> - Try out all of these to learn how JSON path works!


|Query For 	|Parse statement|
|---|---|
|All Customers|`$.[0]`|
|First Customer|	`$.[0]`	|
|Last Customer|	`$.[-1:]`	|
|First two customers|	`$.[0:2]`	|
|Last two customers	|`$.[-2:]`	|
|Second from last|	`$.[-2:-1]`	|
|All the names|	`$..name`	|
|All the pins|	`$..pin`	|
|All the customers who’s pin value is more than 70000 or 80000|	`$..[?(@.pin > 70000)]`	|
|All details of customer with account number	|`$..[?(@.account == "87305901”)].*`|
|Name of customer with account number	|`$.[?(@.account == "70579265")].name`|

### 5. Configure the Conditional for Error Check

- Use the httpBlock.StatusCode variable to check the value retured.
- Note that the test API does not give a 404 but an empty list [] with a 200 when no match is found. However, this step is just to understand error handling and checking.
- Use the `</>` expression check on the condition and play success and failure prompts accordingly.
- Ensure all the settings per block are entered and properly setup.
- Validate and Publish the new script, correcting any errors that show up during validation.

### 6. Point to the New flow in the Routing Strategy

- Go to the routing Strategy page > Routing Strategy > `EP_CiscoLive_<ID>`
- Once the flow is published, configure the Entry Point Routing strategy to point to the new flow `Flow_Lab3_<ID>`.

### 7. Verify the flow end to end

- Verify the new flow end to end by first, logging into the Agent Desktop and going into a ready state.
- Execute the bewlo Test:
- Call the Dial number > Enter the 5 digit PIN number > On Main Menu press 2 > call gets connected to agent, 

`Agent should see all CAD variables (Customer Name, Email, Account Number)`

---

## Congratulations! You're done! 
## You are now ready to start the next Lab!
## [Lab 4: Skills Based Routing](lab4.md){:target="_blank"}


> #### Note: If you would like to go back to the **[HOME PAGE, CLICK HERE](index.md)**
---

## Index: Quick Links

* [Important: Pre-Requisites](prereq.md){:target="_blank"}
* [Lab 1: Setup a Simple Flow and make a test call](lab1.md){:target="_blank"}
* [Lab 2: Add Menu and Queue treatment to the call](lab2.md){:target="_blank"}
* [Lab 3: Setup an advanced HTTP Request](lab3.md)
* [Lab 4: Setup Skills Based Routing (SBR)](lab4.md){:target="_blank"}

### BONUS LABS

* [BONUS - Lab 5 : Setup Intelligent IVR using CCAI](lab5.md){:target="_blank"}
* [BONUS - Lab 6 : Configure Out-dial](lab6.md){:target="_blank"}

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/";}
function nextLab() {window.location.href = "https://wxcctechsummit.github.io/holcct2107/labslive/lab4.html";}
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
  padding: 10px;">NEXT Lab 4: Configuring Skills Based Routing</button>
  
</div>