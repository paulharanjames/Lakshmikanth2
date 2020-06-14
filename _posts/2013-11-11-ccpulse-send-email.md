---
id: 111
title: 'Genesys CCPulse &#8211; How to send email notification?'
date: 2013-11-11T10:52:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=111
permalink: /2013/11/11/ccpulse-send-email/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2013/11/how-to-send-email-notification-using_11.html
dsq_thread_id:
  - "2702201754"
Delicacy_difficulty:
  - "1"
categories:
  - Genesys
  - How to
tags:
  - CCPulse
  - Email
  - Scripting
---
  * Create threshold using Genesys CCPulse threshold wizard

  * Download &#8216;vbSendEmail.dll&#8217; from <http://www.freevbcode.com/ShowCode.Asp?ID=109> and copy it in CCPulse+ folder (typically, &#8216;GCTI\CCPulse+&#8217;)
  * Using command prompt, navigate to CCPulse+ folder and register dll using the following command

> **regsvr32** vbSendMail.dll

  * Create action script as below

<pre class="lang:vb decode:true">Set poSendMail = CreateObject("vbSendMail.clsSendMail")
poSendMail.SMTPHost = ""
poSendMail.From = ""
poSendMail.FromDisplayName = ""
poSendMail.Recipient = ""
poSendMail.RecipientDisplayName = ""
poSendMail.ReplyToAddress = ""
poSendMail.Subject = "CCPulse Notification"
poSendMail.Attachment = ""
poSendMail.Message = ""
poSendMail.Send
Set poSendMail = Nothing</pre>

&nbsp;