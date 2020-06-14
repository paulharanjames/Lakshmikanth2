---
id: 1501
title: How to generate file name with timestamp in windows batch file?
date: 2014-04-08T13:39:43+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: https://lakshmikanth.azurewebsites.net/?p=1501
permalink: /2014/04/08/how-to-generate-file-name-with-timestamp-in-windows-batch-file/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "2756183865"
  - "2756183865"
categories:
  - How to
tags:
  - How to
  - Scripting
  - Timestamp
  - Windows Batch
---
<span id="lnum1" style="color: #606060;"><span style="font-size: small;"><span style="font-family: Verdana;">Recently, we had requirement to generate unique file name to transfer data to another DC in an encrypted format from Windows 2003 server. As a POC and to keep costs down, we decided to use windows batch file scripting to do this. We suffixed data file name with timestamp to make it unique as below</span></span></span>

<span style="color: #339966;">set local<br /> REM Preparing Timestamp Information<br /> set year=%date:~6,4%<br /> set month=%date:~3,2%<br /> set day=%date:~0,2%<br /> set hour=%time:~0,2%<br /> set minute=%time:~3,2%<br /> set seconds=%time:~6,2%<br /> set timestamp=%year%%month%%day%%hour%%minute%%seconds%<br /> set data_file=C:\%timestamp%.txt</span>

<span style="font-family: Verdana;">However, above script failed to generate file if hour is less than 10 as it returns ‘ 8’ for example with leading space and Windows 2003 rejects file name with space. Fortunately, it is easy to fix by checking hour field and replacing space with 0 as below</span>

<span style="color: #339966;"><br /> set local<br /> REM Preparing Timestamp Information<br /> set year=%date:~6,4%<br /> set month=%date:~3,2%<br /> set day=%date:~0,2%<br /> set hour=%time:~0,2%<br /> <b>REM Replace leading space with zero<br /> if &#8220;%hour:~0,1%&#8221; ==&#8221; &#8221; set hour=0%hour:~1,1%</b><br /> set minute=%time:~3,2%<br /> set seconds=%time:~6,2%<br /> set timestamp=%year%%month%%day%%hour%%minute%%seconds%<br /> set data_file=C:\%timestamp%.txt<br /> </span>