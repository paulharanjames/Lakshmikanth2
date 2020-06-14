---
id: 2771
title: 'Log archiver tool &#8211; Zipper &#8211; New features'
date: 2014-08-15T13:59:58+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2771
permalink: /2014/08/15/zipper-2-0-log-archiver/
dsq_thread_id:
  - "2929592020"
  - "2929592020"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Tools
  - Utilities
tags:
  - Archiver
  - Tools
  - Utilities
  - zipper
---
Last year, I wrote <a title="Zipper– Log Archiver tool" href="http://www.lakshmikanth.com/zipper-log-archiver-tool/" target="_blank" rel="noopener noreferrer">Zipper</a>, a log archiver utility tool to save log files in compressed format (zip). Thanks for all your feedback comments and suggestions for more features.

I picked two common requests from the list, which was as below

  * Scheduling functionality
  * Use 7z format than zip format for compression

I am happy to inform you that next version of Zipper is now available (Download link below)

## 7z Format

* * *

Currently, 7z format uses high level compression. I choose to integrate it using 7z command line utility for the following reasons

  * Integrating 7z using LZMA SDK time consuming process
  * With command line utility, it is easy to support future versions of 7zip as we just need to replace file

Results are clear and 7z format wins. Amazingly, it was able to compress 20 MB log file into 964 KB (screenshot below), which will translate into huge savings in disk space. Just like me, most of you will be using accessing server in WAN and no need to explain time savings in copying file into local system for analysis 🙂

[<img class="aligncenter wp-image-2791 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Compressed.png" alt="Compression difference between 7z and zip format" width="685" height="160" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Compressed.png 685w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Compressed-300x70.png 300w" sizes="(max-width: 685px) 100vw, 685px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Compressed.png)

##  Scheduler

* * *

In previous version of zipper application, we relied on windows task scheduler. Though, it worked fine but it created dependency on user accounts and some of you reported issues around password expiration, user permissions etc.

In this version,  zipper uses inbuilt scheduler functionality using <a title="Quartz Scheduler" href="http://www.quartz-scheduler.net/" target="_blank" rel="noopener noreferrer">quartz scheduler</a>. You can use cron expression to schedule zipper functionality. [CronMaker](http://www.cronmaker.com/ "CronMaker") is an excellent tool to generate cron expressions and in the web site, simply enter your requirements to generate cron expression

Here are few examples below

[table id=1 /]

## Installation and Configuration

* * *

Zipper is simple standard windows installer. Just download and setup.exe to install zipper application.

To configure zipper application, refer to this <a title="Zipper– Log Archiver tool" href="http://www.lakshmikanth.com/zipper-log-archiver-tool/" target="_blank" rel="noopener noreferrer">post</a>  and to configure zipper as windows service, run &#8216;install.bat&#8217; from the installation directory and successful installation of windows service is shown below for reference

[<img class="aligncenter wp-image-2911 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Install.png" alt="Zipper 2.0 Install Sucess Screen" width="709" height="417" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Install.png 709w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Install-300x176.png 300w" sizes="(max-width: 709px) 100vw, 709px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Install.png)

Similarly, run &#8216;uninstall.bat&#8217; to uninstall from windows services

[<img class="aligncenter wp-image-2921 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Uninstall.png" alt="Zipper 2.0 Uninstall success" width="613" height="370" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Uninstall.png 613w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Uninstall-300x181.png 300w" sizes="(max-width: 613px) 100vw, 613px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/08/Uninstall.png)

**Note: **To install or uninstall windows service, you should run &#8216;command&#8217; prompt with Administrator privileges

###### <span style="color: #000000;"><strong>Download latest version of zipper<span style="color: #993300;"> <a title="Download" href="https://app.box.com/s/cegdgm3pr4jntma1xz1z" target="_blank" rel="noopener noreferrer"><span style="color: #993300;">here</span></a></span></strong></span>