---
id: 381
title: Best way to convert seconds into (Hour:Minutes:Seconds:Milliseconds) time?
date: 2011-06-20T20:21:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=381
permalink: /2011/06/20/best-way-to-convert-seconds-into-hourminutessecondsmilliseconds-time/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2011/06/best-way-to-convert-seconds-into.html
  - /2011/06/best-way-to-convert-seconds-into.html
dsq_thread_id:
  - "2756187035"
  - "2756187035"
categories:
  - How to
  - Programming
  - VB.NET
---
Just use the TimeSpan class.

    TimeSpan t = TimeSpan.FromSeconds(secs);<br><br>string answer = string.Format("{0:D2}h:{1:D2}m:{2:D2}s:{3:D3}ms", <br> t.Hours, <br> t.Minutes, <br> t.Seconds, <br> t.Milliseconds);<br>