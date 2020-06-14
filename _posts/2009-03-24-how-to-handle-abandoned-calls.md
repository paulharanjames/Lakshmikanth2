---
id: 771
title: How to handle Abandoned calls?
date: 2009-03-24T08:50:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=771
permalink: /2009/03/24/how-to-handle-abandoned-calls/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/03/how-to-handle-abandoned-calls.html
  - /2009/03/how-to-handle-abandoned-calls.html
dsq_thread_id:
  - "2789921053"
  - "2789921053"
categories:
  - Genesys
  - How to
  - OnCallAbandoned
  - strategy
  - URS
---
Is your customer worried about increasing number of abandoned calls? No worry.. 🙂  
You can handle the abandoned calls very well in Genesys.  
All you need to do is pay me some 100,000 £ (lol)..

To handle abandoned calls you have to first **create a strategy** that would have the business logic as required to handle abandoned calls. For example, to add the caller’s number to the callback list, or send a mail alert to the supervisor that your golden customer was left alone on the streets i.e., abandoned :). What next? Yes you have to execute this strategy in case of abandoned. For this use the function _**OnCallAbandoned[strategy name]**_ , which sets the strategy to be executed if EventAbandoned is received.. 

Now you will be happy with appreciation mails from customer..lol..

Cheers!!  
Gururaj S