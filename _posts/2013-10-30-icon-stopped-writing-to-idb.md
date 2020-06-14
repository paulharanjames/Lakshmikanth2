---
id: 171
title: ICON Stopped writing to IDB
date: 2013-10-30T16:05:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=171
permalink: /2013/10/30/icon-stopped-writing-to-idb/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2013/10/icon-stopped-writing-to-idb.html
dsq_thread_id:
  - "2970646716"
categories:
  - ICON
  - Issue
  - SQLite Issue
---
<div dir="ltr" trbidi="on">
  In our environment, ICON stopped writing interaction data to database and noticed following error in interaction server logs</p> 
  
  <p>
    <b>Std 25024 ICON cannot preserve or store the data: &#8216;[SQLITE] Error</b>
  </p>
  
  <p>
    This can happen due to various reasons and listed different scenarios below
  </p>
  
  <p>
    <b><span>[SQLITE] Error [1], text [SQL logic error or missing database]</span></b>
  </p>
  
  <p>
    PQ file is locked by Microsoft index service or antivirus. Refer <a href="http://ccxps.blogspot.com/2013/10/know-which-process-locked-file.html" target="_blank" rel="noopener noreferrer">here </a>to find process having a lock in the file
  </p>
  
  <p>
    <b><span>[SQLITE] Error [7], text [out of memory]  </span></b>
  </p>
  
  <p>
    Memory leak during processing userdata key-value pairs that were defined in call-custN section of adata_spec file. Fixed in 7.6.100.31 version.
  </p>
  
  <p>
    <b><span>[SQLITE] Error [1], text [table q_db_info2 already exists], q_db_info2 table can not be created</span>  </b>
  </p>
  
  <p>
    During ICON startup, PQ file is locked by some application. Refer <a href="http://ccxps.blogspot.com/2013/10/know-which-process-locked-file.html" target="_blank" rel="noopener noreferrer">here</a> to find process having a lock in the file
  </p>
  
  <p>
    <b><span>[SQLITE] Error [1], text [cannot start a transaction within a transaction]</span> </b>
  </p>
  
  <p>
    Option &#8216;dss-no-data-tout&#8217; has too small value to allow ICON to start
  </p>
  
  <p>
    <b><span>[SQLITE] Error [1], text [Invalid db handle]: Limitation</span> </b>
  </p>
  
  <p>
    Genesys recommends that you only start re-synchronizing configuration data after Interaction Concentrator has completed its startup process. If Interaction Concentrator reports the above error, do the following to resolve the issue:
  </p>
  
  <ul>
    <li>
      Stop Interaction Concentrator.
    </li>
    <li>
      Delete the persistent queue (*.pq) file.
    </li>
    <li>
      Restart Interaction Concentrator.
    </li>
    <li>
      Interaction Concentrator should start and perform resynchronization automatically.
    </li>
  </ul>
  
  <div>
    To minimize data loss due to this issue, you can set up alarm condition and alarm reaction in SCI for ICON as below
  </div>
  
  <div>
    <ul>
      <li>
        Create alarm condition for Detect Event : 09-25024 for ICON
      </li>
      <li>
        For this alarm, assign alarm reaction &#8220;Restart the application that generated the alarm&#8221;
      </li>
    </ul>
  </div>
  
  <div>
    For list of other useful ICON alarms, refer <a href="http://ccxps.blogspot.com/2013/10/important-icon-alarms_30.html" target="_blank" rel="noopener noreferrer">here</a>
  </div>
</div>