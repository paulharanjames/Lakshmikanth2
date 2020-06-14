---
id: 881
title: Configure SCS to use SMTP for sending emails
date: 2009-01-26T23:32:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=881
permalink: /2009/01/26/configure-scs-to-use-smtp-for-sending-emails/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/01/configure-scs-to-use-smtp-for-sending.html
  - /2009/01/configure-scs-to-use-smtp-for-sending.html
dsq_thread_id:
  - "3010267568"
  - "3010267568"
categories:
  - Alarms
  - Genesys
  - How to
  - SCS
  - SMTP
---
In last week, I received nearly 10 queries from users to configure SCS to use SMTP to send emails. It is very simple and straight-forward configuration and requires restart of SCS

Open or Create  **&#8216;mailer&#8217;** section in SCS and configure the following values

</p> 

  * **smtp_host**: host name of the SMTP Server


  * **smpt_por**t: port number of the SMTP Server


  * **smtp_from**: From email address
</ul> 

Any changes to smtp\_host and smtp\_port requires SCS restart for changes to take effect.  Changes to smtp_from effects immediately and no restart required.