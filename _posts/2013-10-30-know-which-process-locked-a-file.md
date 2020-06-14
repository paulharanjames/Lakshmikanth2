---
id: 151
title: Know which process locked a file
date: 2013-10-30T17:18:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=151
permalink: /2013/10/30/know-which-process-locked-a-file/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/10/know-which-process-locked-file.html
  - /2013/10/know-which-process-locked-file.html
dsq_thread_id:
  - "2756228012"
  - "2756228012"
categories:
  - ICON
  - Tips
  - Troubleshooting
---
<div dir="ltr" trbidi="on">
  <span>Due to ICON issue, I need to unlock .pq file and want to ensure that it is not locked by any other process. SysInternals tool (Process Explorer) is really helpful to find which processes are having lock on the file</span></p> 
  
  <ul>
    <li>
      <span>Download process explorer from </span><a href="http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx">Microsoft Site</a><span> and run application</span>
    </li>
    <li>
      <span>Click &#8216;Find&#8217; menu and choose &#8216;Find Handle or DLL&#8217;</span>
    </li>
    <li>
      <span>Type the file name. In my case, it was icon_531.pq and click Search button</span>
    </li>
    <li>
      <span>Search results will show the process, process id and application path having handle on the file</span>
    </li>
  </ul>
</div>