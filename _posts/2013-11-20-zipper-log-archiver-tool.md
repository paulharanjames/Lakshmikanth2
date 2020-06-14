---
id: 101
title: Zipper– Log Archiver tool
date: 2013-11-20T16:42:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=101
permalink: /2013/11/20/zipper-log-archiver-tool/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/11/zipper-log-archiver-tool.html
  - /2013/11/zipper-log-archiver-tool.html
dsq_thread_id:
  - "2669990800"
  - "2669990800"
categories:
  - Genesys
  - Tools
tags:
  - Archiver
  - Tools
  - Troubleshooting
  - Utilities
---
 

**Zipper** is log archiving utility that compresses and archives application log files. I developed it to use it to archive Genesys application logs but can be used for other application logs, as well. 

**Why we need zipper utility?** 

* * *

Have you ever heard these conversations from your support team? 

‘We don’t have log files for this particular time frame’

‘Log files rolled over. Have to wait for next occurrence’

Even though, both engineer and customer know that there is an issue, they can’t do anything due to lack of log files. Also, you can compress log file to 90% of its original size i.e) you can store 9 times more than your current configuration. This led me to develop tool on my own to scan for log files on predefined intervals, compress and store it in different folder. 

**Design Considerations </p> 

* * *

</strong>

Initially, I designed to watch log file directory for changes to start archiving activity but decided against it as there is no need to have this application running (& utilizing system resources) for log archiving. Now, zipper can be configured in windows scheduled tasks so that user can configure to schedule it as per their requirements.

You can download and install Zipper from <a href="https://dl.dropboxusercontent.com/u/3031443/Software/setup.zip" target="_blank" rel="noopener noreferrer">here</a>. 

**How to configure? </p> 

* * *

</strong>

Zipper can be configured to scan log files in multiple directories and easily configured using any text editor. To configure, follow the steps below

  * Open ‘zipper.exe.config’ from installation directory in any text editor
  * Go to section ‘zipper’ as shown in screenshot below

[<img title="image" border="0" alt="image" src="http://lh6.ggpht.com/-4BUWK0cnt7s/UozmYQQETHI/AAAAAAAAAJw/C4hswtgvjYI/image_thumb%25255B16%25255D.png?imgmax=800" width="722" height="93" />](http://lh3.ggpht.com/-2IdhNI3CIW0/UozmX0pb11I/AAAAAAAAAJo/7YEJ-LC7HHM/s1600-h/image%25255B32%25255D.png)

<table cellspacing="0" cellpadding="2" width="720" border="1">
  <tr>
    <td valign="top" width="156">
      <a href="http://lh3.ggpht.com/-y4A4gC3h4qo/UozmZJQmr8I/AAAAAAAAAJ4/Epq03TaL4TA/s1600-h/image%25255B19%25255D.png"><img title="image" border="0" alt="image" src="http://lh3.ggpht.com/-EbXYR9_gV14/UozmZiqECDI/AAAAAAAAAKA/WcCGrVMFawo/image_thumb%25255B11%25255D.png?imgmax=800" width="30" height="30" /></a>
    </td>
    
    <td valign="top" width="564">
      <strong>name</strong> – Unique identifier for each directory
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="156">
      <a href="http://lh4.ggpht.com/-vPyOJAdmdGk/UozmaEzX5GI/AAAAAAAAAKE/QepAwjtp7TM/s1600-h/image%25255B22%25255D.png"><img title="image" border="0" alt="image" src="http://lh3.ggpht.com/-LG6TSCPpn60/Uozmamg4cqI/AAAAAAAAAKQ/vdogegsCiGg/image_thumb%25255B12%25255D.png?imgmax=800" width="34" height="34" /></a>
    </td>
    
    <td valign="top" width="564">
      <strong>sourcedirectory</strong> – Directory path where log files will be available. Zipper application will scan this directory for files
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="156">
      <a href="http://lh4.ggpht.com/-JfyskWD0778/Uozmbu8trCI/AAAAAAAAAKY/exySB9QA4ks/s1600-h/image%25255B25%25255D.png"><img title="image" border="0" alt="image" src="http://lh4.ggpht.com/-9bnK47b7zI4/UozmcLo3ZLI/AAAAAAAAAKg/4Pd4d85AHJA/image_thumb%25255B13%25255D.png?imgmax=800" width="34" height="35" /></a>
    </td>
    
    <td valign="top" width="564">
      <strong>targetdirectory</strong> – Directory path where log files will be compressed and stored by zipper application
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="156">
      <a href="http://lh4.ggpht.com/-zmGUWFQVVuc/Uozmcs_FvWI/AAAAAAAAAKk/hhhHD6WhADM/s1600-h/image%25255B28%25255D.png"><img title="image" border="0" alt="image" src="http://lh6.ggpht.com/-aUQi3yLOkcc/UozmdP6FInI/AAAAAAAAAKw/4dzmhoIXb6w/image_thumb%25255B14%25255D.png?imgmax=800" width="34" height="34" /></a>
    </td>
    
    <td valign="top" width="564">
      <strong>filepattern</strong> – Used to define file extensions. For Genesys logs, use “*.log”
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="156">
      <a href="http://lh3.ggpht.com/-pvVLld7O1XY/Uozme1aTbKI/AAAAAAAAAK4/k6Jck8JwMZU/s1600-h/image%25255B31%25255D.png"><img title="image" border="0" alt="image" src="http://lh4.ggpht.com/-w-IKGFcRYtQ/UozmfUDOjwI/AAAAAAAAALA/NaJMeFnL7VE/image_thumb%25255B15%25255D.png?imgmax=800" width="34" height="34" /></a>
    </td>
    
    <td valign="top" width="564">
      <strong>deleteoriginal</strong> – Setting this option to <strong>‘true’ </strong>will delete log file once it is compressed and archived. <strong>‘false’ </strong>will keep original file in the source directory
    </td>
  </tr>
</table>

I am looking to expand functionality by adding scheduling functionality within the application and will release it in next version. For any feedback, feel free to comment me and will try to add it.

<a href="https://dl.dropboxusercontent.com/u/3031443/Software/setup.zip" target="_blank" rel="noopener noreferrer"><strong>Download zipper.setup</strong></a>