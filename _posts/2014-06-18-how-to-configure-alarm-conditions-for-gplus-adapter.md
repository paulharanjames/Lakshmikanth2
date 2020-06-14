---
id: 2401
title: 'Genesys GPlus &#8211; How to configure alarm conditions for GPlus Adapter?'
date: 2014-06-18T14:29:22+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2401
permalink: /2014/06/18/how-to-configure-alarm-conditions-for-gplus-adapter/
dsq_thread_id:
  - "2775276025"
  - "2775276025"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - How to
tags:
  - Genesys
  - GPlusAdapter
  - How to
  - Tips
---
<span style="color: #000000;">GPlus Adapter for Aspect eWFM supports alarm codes for major errors, so that it can be monitored on SCI or Genesys Administrator. For this feature to work correctly, alarm codes must match up with log event id defined in the alarm condition.</span>

<div style="color: #000000;">
  In my environment, I configured GPlus Adapter to send alarm codes as below
</div>

<div style="color: #000000;">
</div>

<div style="color: #000000;">
  <img class="aligncenter size-full wp-image-2421" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/GPlusAdapterOptions.png" alt="GPlusAdapterOptions" width="600" height="564" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/GPlusAdapterOptions.png 600w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/GPlusAdapterOptions-300x282.png 300w" sizes="(max-width: 600px) 100vw, 600px" />
</div>

<div style="color: #000000;">
</div>

<div style="color: #000000;">
   Now, you need to create alarm condition to match alarm codes as below
</div>

<div style="color: #000000;">
  <div>
    <p>
      In Genesys Administrator, you can create a new Alarm Condition:
    </p>
    
    <ol>
      <li>
        Go to Provisioning > Environment > Alarm Conditions.
      </li>
      <li>
        If required, navigate to the folder in which you want to store the new Alarm Condition.
      </li>
      <li>
        Click  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/NewAC.png"><img class="alignnone wp-image-2431 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/NewAC.png" alt="NewAC" width="59" height="20" /></a>
      </li>
      <li>
        On the Configuration tab, enter or modify information as required.
      </li>
      <li>
        On the Options tab, enter or modify information as required.
      </li>
      <li>
        To save the new Alarm Condition and register it in the Configuration Database, do one of the following: <ul>
          <li>
            Click   <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/SaveAC.png"><img class="alignnone wp-image-2441" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/SaveAC.png" alt="SaveAC" width="49" height="20" /></a>to continue configuring the Alarm Condition.
          </li>
        </ul>
      </li>
    </ol>
    
    <div>
      In the screenshot below, I created &#8216;diskWriteFailure&#8217; alarm with log event Id as 9001 and cancel log event id as 9002. You can fine tune this by setting &#8216;Detect Selection Mode&#8217; to &#8216;Select by Application&#8217; and selecting &#8216;GPlusAdapter&#8217; application in &#8216;Detect Application&#8217;.
    </div>
  </div>
  
  <div>
  </div>
  
  <div>
    Two main items to note here
  </div>
  
  <div>
    <ul>
      <li>
        9001 &#8211; I selected 90XX number series to configure custom alarms as other series are used by other components
      </li>
      <li>
        9002 &#8211; Another custom alarm configured for &#8216;diskWriteSuccess&#8217;
      </li>
    </ul>
  </div>
  
  <div>
    <img class="aligncenter size-full wp-image-2481" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Alarm-Condition1.png" alt="Alarm Condition" width="808" height="435" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Alarm-Condition1.png 808w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Alarm-Condition1-300x162.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Alarm-Condition1-768x413.png 768w" sizes="(max-width: 808px) 100vw, 808px" />
  </div>
  
  <div>
  </div>
  
  <div>
    By following above steps, you can configure alarm conditions and assign reaction scripts to get notifications 🙂
  </div>
  
  <p>
    &nbsp;
  </p>
</div>