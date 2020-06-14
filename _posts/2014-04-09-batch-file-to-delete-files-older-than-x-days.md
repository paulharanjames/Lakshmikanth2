---
id: 1711
title: Batch file to delete files older than X days
date: 2014-04-09T07:59:27+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=1711
permalink: /2014/04/09/batch-file-to-delete-files-older-than-x-days/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "2670095873"
  - "2670095873"
categories:
  - How to
  - Tips
tags:
  - How to
  - Tips
  - Windows Batch
---
Quite often, we have an requirement to delete old log files and used powershell scripting in my previous project. With this customer, they are still with Windows 2003 and have to use batch file to achieve the same.

<div>
  <span style="color: #339966;"><code>FORFILES /p "E:\logs" /s /m *.* /d -3 /c "cmd /c if not @isdir==TRUE del @file"&lt;br />
</code></span></p> 
  
  <ul>
    <li>
      <span style="color: #333333; font-family: TitilliumText22LRegular, Arial, sans-serif; font-size: 13px; font-style: inherit; font-weight: inherit; line-height: 1.6em;"> Change &#8216;E:\Logs&#8217; to the directory which you are saving files</span>
    </li>
    <li>
      /d -3  indicates than files older than 3 days and change it, if required
    </li>
    <li>
      if not @isdir == TRUE &#8211; If you have sub directories, it will skip sub directories and only delete files. Otherwise, script will delete sub directories even if you have only one day old file in the sub directory as sub directory last modified data will be greater than 3 days
    </li>
  </ul>
</div>