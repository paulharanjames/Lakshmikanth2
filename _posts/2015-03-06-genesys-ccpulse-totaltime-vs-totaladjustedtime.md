---
id: 5331
title: 'Genesys CCPulse &#8211; TotalTime vs TotalAdjustedTime'
date: 2015-03-06T16:24:28+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5331
permalink: /2015/03/06/genesys-ccpulse-totaltime-vs-totaladjustedtime/
dsq_thread_id:
  - "3573147423"
  - "3573147423"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - Reporting
tags:
  - CCA
  - CCPulse
  - Reporting
---
Have you ever seen 15 minute interval report in CCPulse or Datamart contains more than 900 seconds like below ?

[<img class="aligncenter size-full wp-image-5421" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/937.png" alt="Datamart Screenshot" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/937.png 786w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/937-300x67.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/937-768x171.png 768w" sizes="(max-width: 786px) 100vw, 786px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/937.png)

In this case above, T_WAIT value is 937 seconds for 15 minute interval report, which is only 900 seconds. Strange isn&#8217;t it?

If you analyze configuration details, you will find that &#8216;T\_WAIT&#8217; uses &#8216;Total\_Wait_Time&#8217; statistics in out of box solution &#8211; which uses &#8216;TotalAdjustedTime&#8217; category on subject &#8216;AgentStatus&#8217; as below

[<img class="aligncenter  wp-image-5431" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/totalwaittime.png" alt="totalwaittime" width="406" height="445" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/totalwaittime.png 439w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/totalwaittime-273x300.png 273w" sizes="(max-width: 406px) 100vw, 406px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/totalwaittime.png)

If you use &#8216;Total\_Ready\_Time&#8217; which uses &#8216;TotalTime&#8217;, you will get actual time spent by agent on &#8216;wait status&#8217; in reporting interval period.

[<img class="aligncenter  wp-image-5441" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalReadyTime.png" alt="TotalReadyTime" width="423" height="461" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalReadyTime.png 442w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalReadyTime-275x300.png 275w" sizes="(max-width: 423px) 100vw, 423px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalReadyTime.png)

Below is brief explanation how this works..

Scenario : Agent &#8216;A&#8217; was in Ready state from 14:55 to 15:05 i.e) 10 minutes and across two reporting intervals 14:45 &#8211; 15:00 and 15:00 &#8211; 15:15

In this case, &#8216;TotalTime&#8217; and &#8216;TotalAdjustedTime&#8217; will be calculated as below.

[<img class="aligncenter size-full wp-image-5401" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalTime.png" alt="TotalTime" width="671" height="104" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalTime.png 671w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalTime-300x46.png 300w" sizes="(max-width: 671px) 100vw, 671px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/TotalTime.png)

&nbsp;

For more information about reporting categories, refer to Genesys documentation <a href="http://docs.genesys.com/Documentation/RTME/8.5.0/User/HistoricalCategories" target="_blank" rel="noopener noreferrer">here</a>