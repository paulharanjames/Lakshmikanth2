---
id: 5512
title: 'CCPulse &#8211; Contrasting Color Functionality'
date: 2015-06-24T12:18:42+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5512
permalink: /2015/06/24/ccpulse-contrasting-color-functionality/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3874727517"
  - "3874727517"
categories:
  - CCPulse
  - Genesys
  - Reporting
tags:
  - CCPulse
  - Genesys
  - Reporting
---
### CCPulse &#8211; Contrasting Color

* * *

One of our blog subscriber Ted Lizotte asked this question

_We have a window that used to look like this:_

_[<img class="aligncenter size-full wp-image-5661" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Previous.png" alt="" width="431" height="201" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Previous.png 431w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Previous-300x140.png 300w" sizes="(max-width: 431px) 100vw, 431px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Previous.png)_

_And since our CCPulse upgrade to 8.1.000.19 looks like this:_

_[<img class="aligncenter size-full wp-image-5651" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Current.png" alt="CCPulse Current" width="337" height="155" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Current.png 337w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Current-300x138.png 300w" sizes="(max-width: 337px) 100vw, 337px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/CCPulse-Current.png)_

_Simply making the background Action Black solved the problem before.  I was wondering if another Action that set the font color to black would work? We’ve basically put two different Service Level thresholds in the same window to save space and blacked out the one that didn’t apply.  But now it since it now turns the font white, it’s defeating the purpose._

### Solution

* * *

From version 8.1.000.17, CCPulse uses contrasting color for text and below is actual snippet from CCPulse release notes

>  _Now CCPulse+ uses a contrasting color (Black or White) of the text in the Objects Pane, Tree View, and Table View for items with explicitly set background._

I achieved the same functionality using formula and details are as below

**Scenario :** Show background color as black if agent logged out.

<img class="size-full wp-image-5532 aligncenter" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/AgentView.png" alt="Agent View" width="715" height="190" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/AgentView.png 715w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/AgentView-300x80.png 300w" sizes="(max-width: 715px) 100vw, 715px" /> 

**Step 1: Formula to set agent state as empty string if agent is logged out.**

<img class="size-full wp-image-5542 aligncenter" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Scripting-Expression.png" alt="Scripting Expression" width="610" height="528" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Scripting-Expression.png 610w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Scripting-Expression-300x260.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Scripting-Expression-80x70.png 80w" sizes="(max-width: 610px) 100vw, 610px" /> 

**Step 2: Create Threshold to check for empty string.**

<img class="size-full wp-image-5552 aligncenter" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Threshold.png" alt="Threshold" width="563" height="491" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Threshold.png 563w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Threshold-300x262.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Threshold-80x70.png 80w" sizes="(max-width: 563px) 100vw, 563px" /> 

**Step 3: Create action to set color as black**

<div id="attachment_5522" style="width: 532px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Action.png"><img aria-describedby="caption-attachment-5522" class="size-full wp-image-5522" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Action.png" alt="Action Script" width="522" height="436" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Action.png 522w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/Action-300x251.png 300w" sizes="(max-width: 522px) 100vw, 522px" /></a>
  
  <p id="caption-attachment-5522" class="wp-caption-text">
    Action Script
  </p>
</div>

**Step 4 : Apply this threshold to the statistic and you will find background color as black when agent logged out**

&nbsp;