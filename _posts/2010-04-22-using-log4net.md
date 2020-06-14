---
id: 531
title: Using Log4Net
date: 2010-04-22T23:28:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=531
permalink: /2010/04/22/using-log4net/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/04/using-log4net.html
  - /2010/04/using-log4net.html
dsq_thread_id:
  - "3856263908"
  - "3856263908"
categories:
  - How to
  - Programming
---
My search is to find simple way to use Log4Net in .NET application was futile. Finally, I decided to write sample code on my own 🙂

Step 1: Add reference to log4net.dll in your project (Project -> Add Reference -> Browse)  
Step 2: Add application configuration file (Project -> Resources -> Add new item -> app.config)  
Step 3: Add below in your app.config file in tag

The above example shows configuration to the RollingFileAppender to write to the file log.txt. The file written to will always be called log.txt because the StaticLogFileName param is specified. The file will be rolled based on a size constraint (RollingStyle). Up to 10 (MaxSizeRollBackups) old files of 100 KB each (MaximumFileSize) will be kept. These rolled files will be named: log.txt.1, log.txt.2, log.txt.3, etc..

Step 4: Initialize log object as below

dim log as log4Net.ILog

log = log4net.LogManager.GetLogger(&#8220;Emailer&#8221;)  
log4net.Config.XmlConfigurator.Configure()  
log.Debug(&#8220;Debug message&#8221;)

Simple, isn&#8217;t it?