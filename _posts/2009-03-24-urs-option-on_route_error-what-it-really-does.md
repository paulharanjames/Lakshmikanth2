---
id: 761
title: URS option on_route_error.. what it really does?
date: 2009-03-24T08:53:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=761
permalink: /2009/03/24/urs-option-on_route_error-what-it-really-does/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2009/03/urs-option-onrouteerror-what-it-really.html
dsq_thread_id:
  - "2832841690"
categories:
  - Genesys
  - on_route_error
  - options
  - URS
---
Option **on\_route\_error** defines what to do when an attempt to route a call resulted in an error, which is thrown by the Tserver to URS. If you are used to logs, you will find the EventError after RequestRouteCall. 

Possible choices include:  
default – Route the call to default destination  
ignore – Ignore the error  
delete – Delete the call from URS memory  
reroute – Repeat the request  
try_other – Find another target

Cheers!!  
Gururaj S