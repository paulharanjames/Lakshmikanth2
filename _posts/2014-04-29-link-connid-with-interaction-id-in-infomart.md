---
id: 1781
title: Link ‘ConnID’ with Interaction Id in Infomart
date: 2014-04-29T14:25:04+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: https://lakshmikanth.azurewebsites.net/?p=1781
permalink: /2014/04/29/link-connid-with-interaction-id-in-infomart/
dsq_thread_id:
  - "2670096447"
  - "2670096447"
categories:
  - Genesys
  - ICON
  - Infomart
  - Tips
tags:
  - Genesys
  - ICON
  - Infomart
---
<font size="3" face="Calibri">In Genesys environment, most of us are still used to track call information using Connection Id (ConnID). However, Genesys Infomart (GIM), core subject areas are linked with interaction id and this post will help you to get interaction id using connid or vice versa.</font>

### To get interaction id using conn id

  * <font size="3" face="Calibri">Login into Genesys Icon database and query ‘g_call’ table using your conn id as below. </font>

<font color="#008000" face="Calibri">select&nbsp; id, callid, connid, irid, rootirid from g_call where connid = <strong><em>< your conn id here></em></strong></font>

<font face="Calibri">From the results, take note of rootirid. A call can have multiple conn id due to transfers and column ‘rootirid’ links call records like below</font>

[<img title="clip_image001" style="display: inline" alt="clip_image001" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/04/clip_image001_thumb2.jpg" width="769" height="257" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/04/clip_image0012.jpg)

  * <font face="Calibri">Now, login into Genesys Infomart database and query ‘interaction_fact’ using query below</font>

<font color="#008000" face="Calibri">select * from interaction_fact where media_server_ixn_guid = <strong><em><your root irid here></em></strong></font>

[<img title="image" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="image" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/04/image_thumb.png" width="701" height="316" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/04/image.png)<font face="Calibri"></font>