---
id: 321
title: SIP Tutorial for beginners – Part I
date: 2012-09-03T13:49:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=321
permalink: /2012/09/03/sip-tutorial-for-beginners-part-i/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2012/09/sip-tutorial-for-beginners-part-i.html
  - /2012/09/sip-tutorial-for-beginners-part-i.html
dsq_thread_id:
  - "2858886262"
  - "2858886262"
categories:
  - Session Initiation Protocol
  - SIP
  - Tutorial
---
SIP (Session Initiation Protocol) is a signalling protocol used to create, manage and terminate sessions in an IP based network.  SIP makes it possible to implement services like phone call, click-to-dial  or instant messaging in an IP based environment.  Please note that SIP is used only for signalling and session control and actual data exchanges are handled by other protocols like RTP (Real-time transmission protocol).

SIP provides capabilities to 

  * determine the location of end points 
  * determine the media capabilities using SDP and negotiates services between end points
  * determine the status of end point – available/busy etc..
  * establishes session between end points 
  * call management – hold, release, transfer etc. For transfer, it simply establishes session with new end point with the transferee and terminates session with transferring party