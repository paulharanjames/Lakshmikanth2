---
id: 681
title: What is the best means to report on Voice Mails?
date: 2009-08-27T13:02:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=681
permalink: /2009/08/27/what-is-the-best-means-to-report-on-voice-mails/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2009/08/what-is-best-means-to-report-on-voice.html
Delicacy_difficulty:
  - "1"
dsq_thread_id:
  - "3051208028"
categories:
  - Uncategorized
---
Regarding our conversation on monitoring and tracking your environment for voice mail calls, the most common approach is to place a virtual queue in front of VM target in strategy. When the interaction passes through the virtual queue to the VM DN, the event which takes place is EventDiverted. EventDiverted occurs immediately prior to the Target establishing on an interaction. Placing a VQ on the Target will then will permit you to identify how many calls hit that particular target- be it an Agent Group, Place Group, or Voice Mail DN.

You can track this real time, and create a historical view of same, in CCPulse (6.5+). Simply create a template which tracks on the &#8220;Virtual Queue&#8221; object under the Switch folder. Your template will likely track on &#8220;TotalNumber&#8221;, say CallsEntered (for the Virtual Queue). Ensure when you create the template that in the &#8220;Pre-defined Statistics&#8221; dialog, where you move the &#8220;Available Statistics&#8221; over to the &#8220;Requested Statistics&#8221; column, once you move &#8220;CallsEntered&#8221; over, you double click it to expose its definition. There you will see 2 tabs, &#8220;Properties&#8221; and &#8220;Historical Association&#8221;. As per our conversation, you mentioned you would like this to be both real-time and historical, so in this definition make sure to make an association with a statistic (likely N_ENTERED). Later, this will enable you to apply this template for real-time OR historical use (otherwise, CCPulse won&#8217;t allow you to track it HISTORICALLY).

Once the template is created, in the left hand panel of CCPulse, right click the appropriate VQ you want to track and then &#8220;Create Real-Time View&#8221; or &#8220;Create Historical View&#8221;.

&#8220;Create Real-Time View&#8221;

This permits you to view the number of calls passing through this particular VQ real-time throughout a business day. This would enable your users to view how many calls were being directed to voicemail at any given point in the day.

&#8220;Create Historical View&#8221;

This permits you to view the number of calls passing through this particular VQ on a historical basis (Daily/Weekly/Monthly). For example, you can specify you want to track how many interactions went to voicemail for the last 7 days, or the last month (as examples). You can tweak this to your business requirements.

**Note:** _I don’t know the source of this info. It was in my archive and posted here for reference 🙂_