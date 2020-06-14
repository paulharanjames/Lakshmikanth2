---
id: 4951
title: 'Genesys Customer Care &#8211; Auto follow-up'
date: 2015-01-07T15:45:11+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4951
permalink: /2015/01/07/genesys-customer-care-auto-follow/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3398832754"
  - "3398832754"
categories:
  - Genesys
tags:
  - Auto follow-up process
  - Customer Care
  - Genesys
---
Recently, Genesys re-designed their auto follow-up process for customer care tickets. As per new process, follow-up process is triggered whenever Genesys proposes a solution or requests information for an open case as below

  * First follow-up &#8211; After 2 business days without response
  * Second follow-up &#8211; After 5 business days without response
  * After 10 business days, ticket will be closed and notification sent to user.

In many cases, even though I provided response to Genesys & waiting for feedback, I still got auto follow-up messages and tickets were getting closed. As an user, it was frustrating experience and raised it with Genesys about this process

Now I received clarification on how this process works and thought will share it with you

  * We need to provide response by using web interface only. Unlike old ticketing system, replying to emails doesn&#8217;t change ticket status
  * I used to update ticket by using ‘Post Update’ button. Genesys confirmed that it doesn&#8217;t change ticket status and we should use ‘Provide response’ button from top of the page. Screenshots below for reference.

<div id="attachment_4971" style="width: 743px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC1.jpg"><img aria-describedby="caption-attachment-4971" class="wp-image-4971 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC1.jpg" alt="Add " width="733" height="224" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC1.jpg 733w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC1-300x92.jpg 300w" sizes="(max-width: 733px) 100vw, 733px" /></a>
  
  <p id="caption-attachment-4971" class="wp-caption-text">
    Use &#8216;Provide Response&#8217; button
  </p>
</div>

<div id="attachment_4991" style="width: 669px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC21.jpg"><img aria-describedby="caption-attachment-4991" class="wp-image-4991 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC21.jpg" alt="Don't use 'Post Update'" width="659" height="175" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC21.jpg 659w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/01/GC21-300x80.jpg 300w" sizes="(max-width: 659px) 100vw, 659px" /></a>
  
  <p id="caption-attachment-4991" class="wp-caption-text">
    Don&#8217;t use &#8216;Post Update&#8217;
  </p>
</div>

&nbsp;

My opinion &#8211; and I shared it with Genesys &#8211; it doesn&#8217;t help end user/customer. As such, Genesys environment is complex to understand for any new comer and always encourage support engineers to use phone conversation to seek clarifications. Auto follow-up process should be triggered only when the solution is provided & agreed by customer or when support engineer enables it.

Hope Genesys will improve process to help customers 🙂