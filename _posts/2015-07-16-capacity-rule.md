---
id: 5821
title: 'Configure agent to handle multiple interactions &#8211; Capacity Rule'
date: 2015-07-16T14:33:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5821
permalink: /2015/07/16/capacity-rule/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3940292314"
  - "3940292314"
categories:
  - Genesys
  - How to
tags:
  - Capacity Rule
  - Genesys
---
### Capacity Rule &#8211; What it is?

* * *

If you have worked in Genesys multimedia environment, you know about this already. For others, Capacity rule defines work load capability for agents. For example, you can configure agent to handle 2 emails and 1 voice.

### Where is it located?

* * *

From version 8.5, Capacity rule wizard is available from GAX and for previous version, it is available from Reporting Installation CD

In this post, I will cover creating and applying capacity rule using GAX to an agent

### Create Capacity Rule

* * *

Follow the steps below to create capacity rule

  * After you login into GAX, navigate to Configuration -> Accounts -> Capacity Rules

<img class="aligncenter wp-image-5901 size-large" src="/wp-content/uploads/2015/07/Capacity-Rule-1024x497.png" alt="Capacity Rule" width="600" height="291" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Capacity-Rule-1024x497.png 1024w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Capacity-Rule-300x145.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Capacity-Rule-768x372.png 768w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Capacity-Rule.png 1225w" sizes="(max-width: 600px) 100vw, 600px" /> 

  * Click  &#8216; **+** &#8216;  sign to add new capacity rule

<img class="aligncenter wp-image-5861 size-large" src="/wp-content/uploads/2015/07/Add-CR-Media-1024x453.png" alt="Add CR Media" width="600" height="265" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Add-CR-Media-1024x453.png 1024w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Add-CR-Media-300x133.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Add-CR-Media-768x340.png 768w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Add-CR-Media.png 1339w" sizes="(max-width: 600px) 100vw, 600px" /> 

  1. In Media Type,  Click &#8216; **+** &#8216;  sign to add new media capacity. In the screenshots below, I configured the following

  * Voice &#8211; 1
  * Email &#8211; 2
  * Chat &#8211; 5

  1. Click &#8216;**Save**&#8216; button to save the changes

[<img class="aligncenter wp-image-5851 size-large" src="/wp-content/uploads/2015/07/Add-CR-Email-1-1024x448.png" alt="Add CR Email" width="600" height="263" />](/wp-content/uploads/2015/07/Add-CR-Email-1.png)

&nbsp;

<img class="aligncenter wp-image-5841 size-large" src="/wp-content/uploads/2015/07/Add-CR-Chat-1-1024x458.png" alt="Add CR Chat" width="600" height="268" /> 

### [  
](http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Add-CR.png) Assign Capacity Rule to Agents

* * *

&nbsp;

  * Open **&#8216;Configuration -> Accounts -> Persons&#8217;** and select the agent to configure Capacity rule
  * Select **&#8216;General&#8217;** tab from left hand side (as shown in fig below) to configure Capacity rule

[<img class="aligncenter wp-image-5921 size-medium" src="/wp-content/uploads/2015/07/Assign-CR-300x207.png" alt="Assign Capacity Rule" width="300" height="207" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Assign-CR-300x207.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Assign-CR-768x531.png 768w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Assign-CR.png 1008w" sizes="(max-width: 300px) 100vw, 300px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/07/Assign-CR.png)

By default, Stat Server applies Capacity rule as &#8216;Single Voice Interaction Only&#8217; and you can override this by configuring Capacity rule at tenant level (**Configuration -> Environment -> Tenant -> General Tab**)