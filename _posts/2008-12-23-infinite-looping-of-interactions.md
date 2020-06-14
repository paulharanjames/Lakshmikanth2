---
id: 921
title: Infinite looping of interactions
date: 2008-12-23T15:12:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=921
permalink: /2008/12/23/infinite-looping-of-interactions/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2008/12/infinite-looping-of-interactions.html
  - /2008/12/infinite-looping-of-interactions.html
dsq_thread_id:
  - "2923109629"
  - "2923109629"
categories:
  - chat repeated
  - email
  - email repeated
  - Genesys
  - Genesys chat
  - How to
  - looping chat emails
---
<span><strong>Problem:</strong></span> In this scenario, chat requests are routed to agents perfectly fine. IRD trace view also confirms the same. But when the chat interaction is complete and ended, the same interaction pops up on agent&#8217;s screen. You may have to do all that is possible to stop it from coming again. But even after the &#8220;mark done&#8221; button in agent&#8217;s desktop is clicked and the customer page has the chat interaction properly ended, the flashing new interaction continues. A peculiar fact about the interaction is that as soon as the chat request is answered, it shows the &#8220;calling party: Left session&#8221;.

The same applies to e-mail interactions also. Emails may get routed literally infinite number of times.

![Stop interaction](http://www.esnips.com/nsdoc/ca1c5c7d-789e-49aa-b953-7772a1cc887d) 

<span><strong>Solution:</strong></span> Well, if you encounter this problem, it can be fixed by modifying the routing strategy. Open the routing strategy and wherever there is a &#8220;**stop**&#8221; block, insert a &#8220;**stop interacton**&#8221; block with settings: Check **Notify** and **Delete**. Select option **3rd party server** and in Apllication type choose the **chat server** or email server depending on the type of interaction.