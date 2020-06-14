---
id: 391
title: 'Outbound : Convert seconds to UTC Time and vice versa'
date: 2011-06-01T15:55:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=391
permalink: /2011/06/01/outbound-convert-seconds-to-utc-time-and-vice-versa/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2011/06/outbound-convert-seconds-to-utc-time.html
  - /2011/06/outbound-convert-seconds-to-utc-time.html
dsq_thread_id:
  - "2758282366"
  - "2758282366"
categories:
  - Genesys
  - Genesys outbound
  - How to
  - VB.NET
---
To convert date from export file to seconds passed after 01/01/1970 in Genesys format)

<span><em>       Dim sDate As String = &#8220;01/06/2011 16:46:44&#8221;</em></span>  
<span><em>       Dim date1 As Date = #1/1/1970#</em></span>

<span><em>       Dim date2 As Date = DateTime.Parse(sDate).ToUniversalTime</em></span>

<span><em>       inSeconds = DateDiff(&#8220;s&#8221;, date1, date2))</em></span>

<span>To convert seconds from database to date and time</span>

<span>        Dim localTime As Date</span>

<span>        Dim date1 As Date = #1/1/1970#</span>

<span>        localTime = date1.AddSeconds(1306943204).ToLocalTime</span>

<span>        Debug.Print localtime.ToString</span>