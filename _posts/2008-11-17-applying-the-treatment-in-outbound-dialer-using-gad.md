---
id: 941
title: Applying the treatment in Outbound dialer using GAD
date: 2008-11-17T10:49:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=941
permalink: /2008/11/17/applying-the-treatment-in-outbound-dialer-using-gad/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2008/11/applying-treatment-in-outbound-dialer.html
dsq_thread_id:
  - "3010268838"
categories:
  - GAD
  - Genesys
  - Outbound
  - Tips
---
Recently, a team member asked me whether the agent can apply the treatment only when he wants to.

Answer for it is **&#8220;YES&#8221;**. From version 7.0.201.05 release, new option is available in Genesys to activate this functionality. We need to configure the following values in &#8216;GAD&#8217; application object to enable the agent to select the treatment

Section             : **outbound**

Option Name   : **treatment**

Value               : **agent-selection**

From the next call onwards, there will be drop-down box near the **&#8220;Mark Done&#8221;** button in GAD to select the treatment.

If you have any more tips, please send it to blakshmikath (@) gmail (dot) com