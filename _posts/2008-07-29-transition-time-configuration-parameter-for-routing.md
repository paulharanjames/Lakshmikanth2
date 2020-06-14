---
id: 1021
title: 'transition time: Configuration Parameter for Routing'
date: 2008-07-29T05:28:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=1021
permalink: /2008/07/29/transition-time-configuration-parameter-for-routing/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2008/07/transition-time-configuration-parameter.html
  - /2008/07/transition-time-configuration-parameter.html
dsq_thread_id:
  - "2832937465"
  - "2832937465"
categories:
  - Configuration Parameter
  - Genesys
  - Routing
  - URS
---
**<span>&#8220;transition_time&#8221;</span>** is the important configuration parameter for Genesys routing solution. It defines the minimum time URS waits between routing the interaction to the agent. This option avoids routing multiple interactions to the same agent.

For example, transition_time is configured as **10 seconds**.

</p> 

  * Agent (agent1) logged in and made available by **10:00:00 AM**


  * At 10:05:00, URS receives the interaction and routes the call to the Agent(agent1)


  * At the same time, URS receives another interaction and searching for the target


  * Till the transition time expires i.e) **10:05:10**, URS will not consider the Agent (agent1) is available for the interaction
</ul>