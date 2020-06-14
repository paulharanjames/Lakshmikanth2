---
id: 131
title: Tool to find default routed calls
date: 2013-11-08T10:50:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=131
permalink: /2013/11/08/tool-to-find-default-routed-calls/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/11/tool-to-find-default-routed-calls.html
  - /2013/11/tool-to-find-default-routed-calls.html
dsq_thread_id:
  - "2669988315"
  - "2669988315"
categories:
  - Genesys
  - Tools
tags:
  - Default Routing
  - Platform SDK
  - Troubleshooting
  - URS
---
In our environment, I found that everyday we were having small percentage of calls getting default routed. But how do you find these calls, identify issues and provide better customer service? 

My search for existing tool was in vain and decided to develop it on my own (Genesys Platform SDK makes it easy to develop it too). What I want from this tool is 

  * To visualize call summary for each route point – Entered, Diverted, Abandoned & Default Routed 
  * See live calls for each route point – Time, Conn ID, ANI are must 
  * Generate report for each call result – filter by route point

[<img title="RPMonitor Screenshot" border="0" alt="RPMonitor Screenshot" src="http://lh6.ggpht.com/-hb1PCx2f3qg/UnzB2i0_MPI/AAAAAAAAAJU/CqnWOGcVE2U/RPMonitor%252520Screenshot_thumb%25255B13%25255D.jpg?imgmax=800" width="657" height="433" />](http://lh6.ggpht.com/-4d6NEKtkGv4/UnzB1nijV8I/AAAAAAAAAJM/XVpzSy2c9pQ/s1600-h/RPMonitor%252520Screenshot%25255B15%25255D.jpg)

**Advantages**

  * Identify and solve routing issues 
  * Proactively address performance bottlenecks – Database Timeout, Web Service timeout etc.. 
  * Identify which routing points are used. Having worked with many customers, I observed many of them are not used in production environment and afraid to remove it. This will help to provide data and boost confidence to take correct action 
  * Oh yeah, saves lot of time in troubleshooting