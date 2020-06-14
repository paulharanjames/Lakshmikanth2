---
id: 4111
title: 'Genesys &#8211; How to customize log events?'
date: 2014-09-24T21:24:10+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4111
permalink: /2014/09/24/genesys-customize-log-steps/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3050763448"
  - "3050763448"
categories:
  - Genesys
  - How to
tags:
  - Genesys
  - Log Events
---
In this post, we will see how to customise log events in Genesys environment. For more information about log events customization, refer my last post [here](http://www.lakshmikanth.com/genesys-customize-log-events/ "Genesys – Customize log events")

For this, we will consider URS log event 15-20003 as below

<div id="attachment_4061" style="width: 1212px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1.png"><img aria-describedby="caption-attachment-4061" class="size-full wp-image-4061" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1.png" alt="URS Log Message" width="1202" height="343" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1.png 1202w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1-300x86.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1-1024x292.png 1024w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/URSDefaultRouting1-768x219.png 768w" sizes="(max-width: 1202px) 100vw, 1202px" /></a>
  
  <p id="caption-attachment-4061" class="wp-caption-text">
    URS Log Message
  </p>
</div>

As you can see from picture above, this is &#8216;INTERACTION&#8217; level log and going to configure this as &#8216;STANDARD&#8217; level.

## Configuration Steps

* * *

Steps to configure log event customization is as below

  1. Configure section **&#8216;log-extended&#8217;** in application options, if not available already
  2. Create new option **&#8216;level-reassign-20003&#8217;** and set value as **&#8216;standard&#8217;**. Here 20003 indicates log event id and valid options are as below 
      * **alarm** &#8211; log level will be set to Alarm.
      * **standard** &#8211; log level will be set to Standard.
      * **interaction** &#8211; log level will be to Interaction.
      * **trace** &#8211; log level will be set to Trace.
      * **debug**&#8211; log level will be to Debug.
      * **none** &#8211; log will not be recorded
  3. Optional Configuration. Create option **&#8216;level-reassign-disable&#8217;** and set value to **&#8216;false&#8217;.** This is useful as setting this value to **&#8216;true&#8217; **disables log event customizations for this application.

<div id="attachment_4121" style="width: 605px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/level-reassign.png"><img aria-describedby="caption-attachment-4121" class="size-full wp-image-4121" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/level-reassign.png" alt="Log Event Customisation" width="595" height="172" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/level-reassign.png 595w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/level-reassign-300x87.png 300w" sizes="(max-width: 595px) 100vw, 595px" /></a>
  
  <p id="caption-attachment-4121" class="wp-caption-text">
    Configuration Options
  </p>
</div>