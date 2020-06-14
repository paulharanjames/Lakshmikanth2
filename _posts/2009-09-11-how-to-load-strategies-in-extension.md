---
id: 661
title: How to load strategies in Extension?
date: 2009-09-11T20:33:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=661
permalink: /2009/09/11/how-to-load-strategies-in-extension/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2009/09/how-to-load-strategies-in-extension.html
dsq_thread_id:
  - "2970753695"
categories:
  - Uncategorized
---
To load strategies in extension, you need to configure strategy details manually for DN. Let URS_01 is our UR Server, 5001 is our DN and we would like to run our strategy &#8216;Sample&#8217; on &#8216;ringing&#8217; event. Here are the details for the same 

  * Open DN 5001 and go to &#8216;Annex&#8217; Tab
  * Create a section named &#8216;URS_01&#8217; (same as UR Server name)
  * Create options &#8216;event_arrive&#8217; with value as &#8216;ringing&#8217;
  * Create option &#8216;strategy&#8217; with value as &#8216;sample&#8217; (name of the strategy)
  * Create option &#8216;strategy0x65&#8217; with value as &#8216;sample&#8217; (name of the strategy) 

Simple..isn&#8217;t it 🙂