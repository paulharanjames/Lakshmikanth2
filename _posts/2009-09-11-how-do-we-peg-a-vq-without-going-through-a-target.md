---
id: 671
title: How do we peg a VQ without going through a target?
date: 2009-09-11T20:28:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=671
permalink: /2009/09/11/how-do-we-peg-a-vq-without-going-through-a-target/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/09/how-do-we-peg-vq-without-going-through.html
  - /2009/09/how-do-we-peg-vq-without-going-through.html
dsq_thread_id:
  - "2967211916"
  - "2967211916"
categories:
  - Genesys
  - Routing
  - Virtual Queue
---
Select VQ in target block with timeout of 0 and a dummy place selected for routing. 

Will get a peg on the VQ and the call will go out of the red port.