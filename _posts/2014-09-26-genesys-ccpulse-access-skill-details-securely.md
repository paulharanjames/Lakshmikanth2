---
id: 4311
title: 'Genesys CCPulse &#8211; access skill details securely'
date: 2014-09-26T10:18:51+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4311
permalink: /2014/09/26/genesys-ccpulse-access-skill-details-securely/
dsq_thread_id:
  - "3055656122"
Delicacy_difficulty:
  - "1"
categories:
  - Genesys
  - Reporting
tags:
  - CCPulse
  - Genesys
  - Reporting
---
In my post about Genesys [CCPulse&#8217;s powerful and least used feature](http://www.lakshmikanth.com/most-powerful-and-less-popular-feature-in-ccpulse/ "CCPulse – Very powerful but less popular feature"), I showed example of using JScript  language to retrieve skill details from Configuration database. One of the reader **Robert** left me comment about accessing skill details securely as database script will expose configuration database username and password.

## High level data flow

* * *

If we need skill information and don&#8217;t want to access configuration database directly, we need an application which can do this job for us like below

<div id="attachment_4321" style="width: 715px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/AppServer.jpg"><img aria-describedby="caption-attachment-4321" class="wp-image-4321 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/AppServer.jpg" alt="Genesys CCPulse" width="705" height="270" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/AppServer.jpg 705w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/AppServer-300x115.jpg 300w" sizes="(max-width: 705px) 100vw, 705px" /></a>
  
  <p id="caption-attachment-4321" class="wp-caption-text">
    Middleware
  </p>
</div>

In the above architecture, there are two options

  * Use Platform SDK to retrieve details from Configuration Server  &#8211; _**recommended**_
  * Access configuration database and retrieve skill details

In both cases, username and password are not exposed to CCPulse application user and data is returned from Application server.

For my internal testing, I developed application server to access configuration server using Platform SDK and exposed <a title="RESTful API" href="http://en.wikipedia.org/wiki/Representational_state_transfer" target="_blank" rel="noopener noreferrer">RESTful API</a>

<div id="attachment_4341" style="width: 945px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/WebCall.png"><img aria-describedby="caption-attachment-4341" class="wp-image-4341 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/WebCall.png" alt="CCPulse - Web Access" width="935" height="99" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/WebCall.png 935w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/WebCall-300x32.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/WebCall-768x81.png 768w" sizes="(max-width: 935px) 100vw, 935px" /></a>
  
  <p id="caption-attachment-4341" class="wp-caption-text">
    CCPulse &#8211; Web Access
  </p>
</div>

# Sample Script

* * *

Script used to retrieve data from application server is as below

<pre class="lang:js decode:true  " title="WebAccess">var employeeId = state.AgentID;
var strurl="http://localhost:49478/api/agent?employeeid=" + employeeId;
var WinHttpReq = new ActiveXObject("WinHttp.WinHttpRequest.5.1");
//  Create an HTTP request.
var temp = WinHttpReq.Open("GET", strurl, false);
//  Send the HTTP request.
WinHttpReq.Send();
//  Retrieve the response text.
strResult = WinHttpReq.ResponseText;
strResult;</pre>

Personally, I am very excited about this.

Main drawback of CCPulse is that it only provides real-time snapshot and doesn&#8217;t have feature to analyse past events and supervisor have to wait for ETL process to complete for Infomart or CCA reports (anyway, I haven&#8217;t seen anybody using Infomart/CCA for intra-day operations yet).

Having able to communicate using RESTful API opens many possibilities to address above issues. For example, we can record threshold alerts,  send message notifications etc.. to help intra-day operations.