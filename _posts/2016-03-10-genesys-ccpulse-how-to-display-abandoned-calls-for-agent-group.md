---
id: 6551
title: 'Genesys CCPulse : How to display abandoned calls for Agent Group?'
date: 2016-03-10T15:30:25+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6551
permalink: /2016/03/10/genesys-ccpulse-how-to-display-abandoned-calls-for-agent-group/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "4650738655"
  - "4650738655"
categories:
  - Genesys
  - How to
tags:
  - Abandoned
  - CCPulse
  - Genesys
  - Reporting
---
In our application, we want to find out how calls are reported and handled if the calls are abandoned at agent i.e.) customer disconnects call while it is ringing at agent station.

It is not available at &#8216;out of box&#8217; definitions but fortunately easy to implement it.

## Configure Abandoned Calls for Agent Groups

* * *

  * Configure below stat definition in your Reporting Stat Server

<div id="attachment_6561" style="width: 730px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2016/03/Abandoned-1.png" rel="attachment wp-att-6561"><img aria-describedby="caption-attachment-6561" class="wp-image-6561 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2016/03/Abandoned-1.png" alt="Genesys CCPulse : Abandoned" width="720" height="281" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2016/03/Abandoned-1.png 720w, http://localhost/newlakshmikanth3/wp-content/uploads/2016/03/Abandoned-1-300x117.png 300w" sizes="(max-width: 720px) 100vw, 720px" /></a>
  
  <p id="caption-attachment-6561" class="wp-caption-text">
    Abandoned Call Definition
  </p>
</div>

  * Create/Modify agent group template to show this statistics

<div id="attachment_6581" style="width: 649px" class="wp-caption aligncenter">
  <a href="/wp-content/uploads/2016/03/Abandoned-Agent-Group-1.png" rel="attachment wp-att-6581"><img aria-describedby="caption-attachment-6581" class="wp-image-6581 size-full" src="/wp-content/uploads/2016/03/Abandoned-Agent-Group-1.png" alt="Genesys CCPulse : Abandoned Agent Group" width="639" height="487" /></a>
  
  <p id="caption-attachment-6581" class="wp-caption-text">
    Abandoned Agent Group
  </p>
</div>

  * Open configured view in CCPulse and make test calls to verify the result

As you can see from the stat definition, you can use this statistics to track abandoned calls for agents and places as well.