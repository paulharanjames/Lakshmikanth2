---
id: 901
title: How to find DBID of Applications in Genesys?
date: 2009-01-26T23:14:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=901
permalink: /2009/01/26/how-to-find-dbid-of-applications-in-genesys/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/01/how-to-find-dbid-of-applications-in.html
  - /2009/01/how-to-find-dbid-of-applications-in.html
dsq_thread_id:
  - "2684258639"
  - "2684258639"
categories:
  - CME
  - Configuration Manager
  - Genesys
  - How to
  - Tricks
---
In Genesys, you need to know DBID of applications to configure alarms/blocking logs from Message Server.  Ever wondered to find out DBID of the application&#8230; Here is the trick&#8230;

Open configuration manager (CME) from command prompt, using the **-d** command line parameter. For example, &#8220;D:\GCTI\SCE.exe -d&#8221;.. That&#8217;s it 🙂

Now you will find the application DBID in the Application Properties Dialog box.

If you want to view the DBID by default, right click the CME shortcut and add &#8220;-d&#8217; in target text box.