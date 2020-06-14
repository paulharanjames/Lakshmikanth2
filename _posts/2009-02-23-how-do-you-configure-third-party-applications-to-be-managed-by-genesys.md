---
id: 821
title: How do you configure ‘third party applications’ to be managed by Genesys?
date: 2009-02-23T19:23:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=821
permalink: /2009/02/23/how-do-you-configure-third-party-applications-to-be-managed-by-genesys/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/02/how-do-you-configure-third-party.html
  - /2009/02/how-do-you-configure-third-party.html
dsq_thread_id:
  - "2795759390"
  - "2795759390"
categories:
  - Genesys
  - How to
---
You can monitor ‘third party applications’ like Tomcat in Genesys Management Framework. You need to configure new application object using ‘Third Party Application’ Template.

To start and stop using SCI, please configure start and stop command in Annex tab of the application object

To configure start command, **Application** –> **Annex** –> **start_stop** (section) –> **start_command** (option name)

To configure stop command, **Application** –> **Annex** –> **start_stop** (section) –> **stop_command** (option name)

I will be posting more tips & tricks in this site and if you would like to cover any particular topic, kindly let me know