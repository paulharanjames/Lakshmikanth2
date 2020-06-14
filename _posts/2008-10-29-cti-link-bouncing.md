---
id: 991
title: CTI link bouncing
date: 2008-10-29T19:36:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=991
permalink: /2008/10/29/cti-link-bouncing/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2008/10/cti-link-bouncing.html
  - /2008/10/cti-link-bouncing.html
dsq_thread_id:
  - "2740552036"
  - "2740552036"
categories:
  - Avaya
  - CTI link
  - disconnects often
  - Genesys
  - service unavailable
  - t-server
---
Yes.. This could be a rare scenario as you think. But if you have used T-server with switch simulator,chances are more that you could have encountered this problem.

In this case, the T-server disconnects from the switch and status changes to &#8220;**_Service Unavailable_**&#8220;.But after a while, the switch &#8211; Tserver connection is restored and the status becomes &#8220;started&#8221;. Again, this doesn&#8217;t last for much time. Just wait for some 45 seconds and the link goes down. And this game continues to give the same trouble.

**Solution**: In T-server, the option **ts-tp-enabled** should be set to **false** and this will fix the problem if you are as lucky as i am.. 🙂