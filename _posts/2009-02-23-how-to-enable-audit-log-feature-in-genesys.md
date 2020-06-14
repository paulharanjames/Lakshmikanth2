---
id: 841
title: How to enable Audit log feature in Genesys?
date: 2009-02-23T18:43:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=841
permalink: /2009/02/23/how-to-enable-audit-log-feature-in-genesys/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/02/how-to-enable-audit-log-feature-in.html
  - /2009/02/how-to-enable-audit-log-feature-in.html
dsq_thread_id:
  - "2691207191"
  - "2691207191"
categories:
  - Audit Log
  - Configuration
  - Configuration Server
  - Genesys
  - How to
  - Message Server
  - SCS
---
I have been asked many ‘how to’ questions by junior team members and thought that I will share it with everyone here..

You can enable ‘Audit logs’ in just three steps

  * Configure **‘Configuration Server’** to be managed by Management Framework. For assistance on configuring configuration server, please refer to post **[‘Configure Configuration Server in CME’](http://ctiworld.wordpress.com/2009/02/23/configure-configuration-server-in-cme/)** 
  * Enable **network** logging for **trace** level for **‘Configuration Server’** and **‘SCS’**. 
  * As always for network logging, add connection to ‘Message Server’ from Configuration Server and SCS 

I will be posting other tips and tricks shortly. If you have any tips to share or would like to know about tips on any components, let me know