---
id: 2531
title: 'Genesys GPlus &#8211; Aspect eWFM Simulator'
date: 2014-08-07T15:22:32+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2531
permalink: /2014/08/07/aspect-ewfm-simulator/
dsq_thread_id:
  - "2923943926"
Delicacy_difficulty:
  - "1"
categories:
  - Genesys
  - Tools
tags:
  - Aspect
  - eWFM
  - Genesys
  - GPlus
  - Simulator
---
In my current project, I am working on integrating Genesys G+ Adapter with Aspect eWFM (Workforce Management solution). We completed internal testing and wrote blog about configuring alarms for GPlus Adapter here (<a title="How to configure alarm conditions for GPlus Adapter?" href="http://lakshmikanth.azurewebsites.net/how-to-configure-alarm-conditions-for-gplus-adapter/" target="_blank" rel="noopener noreferrer">how-to-configure-alarm-conditions-for-gplus-adapter?</a>)

To verify configuration and successful integration, I realized that I need to have RTA Server simulator for the following reasons

  * **Dependency on Aspect engineer** &#8211; Aspect eWFM is hosted and managed by third party vendor. Even for minor changes like agent id to login id, aspect engineer&#8217;s availability became an issue as it extended project timelines and naturally, increased cost
  * **Network & Firewall Issues** &#8211; Our environment is complex where real time data need to traverse through multiple networks & firewalls and each segment, source & destination IP address are <a title="NAT" href="http://en.wikipedia.org/wiki/Network_address_translation" target="_blank" rel="noopener noreferrer">NAT</a>&#8216;ed for security purpose. We need to identify whether packets are sent from GPlus Adapter and if yes, what is sent. Unfortunately, GPlus Adapter logs doesn&#8217;t have this information
  * **Fail over and Load testing** &#8211; We had single eWFM environment for both production and testing and can&#8217;t be used for fail over & load testing

With little bit of help from Aspect documents and my own analysis to understand Aspect RTA server, I completed development of RTA Simulator.

[<img class="aligncenter wp-image-2541 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Aspect-RTA-Debugger.png" alt="Aspect RTA Debugger" width="958" height="705" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Aspect-RTA-Debugger.png 958w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Aspect-RTA-Debugger-300x221.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Aspect-RTA-Debugger-768x565.png 768w" sizes="(max-width: 958px) 100vw, 958px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Aspect-RTA-Debugger.png)

[<img class="alignleft wp-image-2581" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/1-filled-32.png" alt="1-filled-32" width="24" height="24" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/1-filled-32.png)

&nbsp;

Message Packet timestamp &#8211; To identify network disconnects in the environment

[<img class="alignleft wp-image-2591" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/2-filled-32.png" alt="2-filled-32" width="24" height="24" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/2-filled-32.png)

Actual message packet &#8211; I parsed message packet to check timestamp , agent state record etc. Clicking &#8216;StateRecordMessage&#8217; shows agent state details as below<a style="font-style: normal;" href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Agent-State-Record-Alone.png"><img class="aligncenter  wp-image-2551" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Agent-State-Record-Alone.png" alt="Agent State Record Alone" width="424" height="310" /></a>

[<img class="alignleft wp-image-2601" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/3-filled-32.png" alt="3-filled-32" width="24" height="24" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/3-filled-32.png)Log message &#8211; For reference, I logged messages into file but needed quick way to check message packet

&nbsp;

With simulator

  * I can modify GPlus Adapter configuration and confirm results immediately saving lot of time & money
  * Allowed me to complete fail over and load testing successfully
  * GPlus Adapter allows to configure multiple RTA streams. I configured two streams, one for simulator running locally and another one for Aspect RTA Server. It helped us to identify not only network and firewall issues & also security configurations for GPlus Adapter

**Note:** Application size is nearly 60 MB and hence, not attached with this post. If you need this tool, feel free to contact me.