---
id: 81
title: Purge log records–excluding audit level logging
date: 2014-02-10T16:38:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=81
permalink: /2014/02/10/purge-log-records-excluding-audit-level-logging/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2014/02/purge-log-recordsexcluding-audit-level.html
  - /2014/02/purge-log-recordsexcluding-audit-level.html
dsq_thread_id:
  - "2670913944"
  - "2670913944"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
tags:
  - Log Database
  - Purge Records
  - Tips
---
Some time back, I wrote blog to delete log records older than 15 days from Genesys log database (<a href="http://ccxps.blogspot.co.uk/2013/01/deleting-log-records-from-log-database.html" target="_blank" rel="noopener noreferrer">here</a>) From our support team, we had request to delete log records older than 15 days but want to retain audit level logging for 90 days.

To achieve this, add category filter in the purge query as below

<div>
  <p>
    <span style="color: #339966;">&#8212; To delete attribute records which doesn&#8217;t have parent record</span>
  </p>
  
  <p>
    <span style="color: #0000ff;">delete from</span> G_LOG_ATTRS <span style="color: #0000ff;">where</span> LRID <span style="color: #0000ff;">not in</span> (<span style="color: #0000ff;">select</span> G_LOG_MESSAGES.ID <span style="color: #0000ff;">from</span> G_LOG_MESSAGES)
  </p>
  
  <p>
    <span style="color: #339966;">&#8212; To delete log attribute records older than 90 days excluding audit level logging</span>
  </p>
  
  <p>
    <span style="color: #0000ff;">delete from</span> G_LOG_ATTRS <span style="color: #0000ff;">where</span> LRID <span style="color: #0000ff;">in</span> (<span style="color: #0000ff;">select</span> G_LOG_MESSAGES.ID <span style="color: #0000ff;">from</span> G_LOG_MESSAGES <span style="color: #0000ff;">where</span> TIMEGENERATED < DATEADD(<span style="color: #0000ff;">DAY</span>, -90, GETDATE())<span style="color: #0000ff;">and</span> CATEGORY = 0)
  </p>
  
  <p>
    <span style="color: #339966;">&#8212; To delete log records older than 90 days excluding 90 days</span>
  </p>
  
  <p>
    <span style="color: #0000ff;">delete from</span> G_LOG_MESSAGES <span style="color: #0000ff;">where</span> TIMEGENERATED < DATEADD(DAY, -90, <span style="color: #0000ff;">GETDATE()</span>) <span style="color: #0000ff;">and</span> CATEGORY = 0
  </p>
  
  <pre></pre>
</div>