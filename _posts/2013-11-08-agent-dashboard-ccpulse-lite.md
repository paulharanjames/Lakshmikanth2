---
id: 121
title: 'Genesys Pulse &#8211; CCPulse Lite &#8211; Bespoke version'
date: 2013-11-08T14:57:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=121
permalink: /2013/11/08/agent-dashboard-ccpulse-lite/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/11/your-browser-does-not-support-iframes.html
  - /2013/11/your-browser-does-not-support-iframes.html
dsq_thread_id:
  - "2669992519"
  - "2669992519"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
tags:
  - CCPulse
  - Dashboard
  - Genesys
---
<div dir="ltr">
  <div dir="ltr">
    <p>
      In my previous project, customer would like to have thin client application &#8211; minimized version of CCPulse &#8211; for agents and supervisors to view current queue status and agent state. This was required to minimize queue time especially while doing internal transfers and improve customer experience.Using dashboard application, agent can view queue status and agent status (&#8216;Presence&#8217; or &#8216;Search&#8217; tab) before initiating transfer and without any doubt, improved customer experience immensely.
    </p>
    
    <p>
      So, I developed application using ASP.NET, WCF and Genesys Platform SDK and really happy about it. Had few challenges in supporting different browser versions and security policies within the organisation but it went well at the end.
    </p>
    
    <p>
      You can see the demo of the application below and it is actually hosted in Windows Azure with Genesys Stat Server simulator.
    </p>
    
    <p>
      <b>Note :</b> It is working version and you can actually select different themes and tabs. Depending on your network connection speed, it may take upto 1 minute to load application.
    </p>
  </div>
  
  <p>
  </p>
</div>