---
id: 5581
title: Handling the leap second
date: 2015-06-23T09:50:46+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5581
permalink: /2015/06/23/handling-the-leap-second/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3871535835"
  - "3871535835"
categories:
  - Genesys
  - How to
  - Tips
tags:
  - Genesys
  - Leap Second
  - Oracle
---
### Leap Second &#8211; What is it?

* * *

From wiki

> _A **leap second** is a one-[second](https://en.wikipedia.org/wiki/Second "Second") adjustment that is occasionally applied to [Coordinated Universal Time](https://en.wikipedia.org/wiki/Coordinated_Universal_Time "Coordinated Universal Time") (UTC) in order to keep its time of day close to the [mean solar time](https://en.wikipedia.org/wiki/Mean_solar_time "Mean solar time"){.mw-redirect}, or [UT1](https://en.wikipedia.org/wiki/UT1 "UT1"){.mw-redirect}. Without such a correction, time reckoned by [Earth&#8217;s rotation](https://en.wikipedia.org/wiki/Earth%27s_rotation "Earth's rotation") drifts away from [atomic time](https://en.wikipedia.org/wiki/Atomic_time "Atomic time"){.mw-redirect} because of [irregularities](https://en.wikipedia.org/wiki/Earth_rotation#Changes_in_rotation "Earth rotation"){.mw-redirect} in the Earth&#8217;s rate of rotation._ 

<div id="attachment_5621" style="width: 401px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/2015-06-23_10-22-36.png"><img aria-describedby="caption-attachment-5621" class="size-full wp-image-5621" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/2015-06-23_10-22-36.png" alt="Leap Time" width="391" height="161" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/2015-06-23_10-22-36.png 391w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/06/2015-06-23_10-22-36-300x124.png 300w" sizes="(max-width: 391px) 100vw, 391px" /></a>
  
  <p id="caption-attachment-5621" class="wp-caption-text">
    Leap Time Jun 30 2015
  </p>
</div>

We will have leap second on Jun 30th this year and it means that this year the last minute of June 30th will be one second longer and “June 30, 2015 23:59:60″ will be a valid and correct time. There may be few issues caused by leap second and below is the summary of my findings

### Genesys

* * *

There will be minor issues on reporting products and can be fixed by adjusting time through NTP. I suggest to synchronize time on server on 01 July 2015 01:00 hours on all Genesys Servers.

### Operating System (Windows, IBM AIX and Redhat LInux)

* * *

Microsoft (<http://blogs.msdn.com/b/mthree/archive/2012/07/01/leap-second-070112.aspx>) and IBM (<http://www-01.ibm.com/support/docview.wss?uid=isg3T1022057>) confirmed that there will not be any issues.

Red hat linux is impacted by leap second and fix is available for this. More details can be found at <https://access.redhat.com/articles/15145>

### Databases (Oracle and SQL Server)

* * *

  * SQL Server &#8211; No impact as it receives time from Windows
  * Oracle &#8211; Oracle notes that there may be multiple issues (System Hang, 100% CPU utilization etc) on LInux environment ([https://blogs.oracle.com/oem/entry/oracle\_support\_note\_for\_leap](https://blogs.oracle.com/oem/entry/oracle_support_note_for_leap)). Refer to the above link for MOS note to fix this issue in your environment