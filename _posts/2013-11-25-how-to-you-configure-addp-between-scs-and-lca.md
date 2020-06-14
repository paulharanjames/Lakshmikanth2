---
id: 91
title: How to configure ADDP between SCS and LCA ?
date: 2013-11-25T16:19:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=91
permalink: /2013/11/25/how-to-you-configure-addp-between-scs-and-lca/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2013/11/how-to-you-configure-addp-between-scs.html
dsq_thread_id:
  - "2671897916"
Delicacy_difficulty:
  - "1"
categories:
  - Genesys
tags:
  - ADDP
  - LCA
  - Network Disconnect
  - SCS
---
<div dir="ltr">
  In our environment, we started experiencing false disconnects and failovers of Genesys components. From analysis, I found that due to increased network activity from other projects, we are experiencing temporary delays and have to reconfigure timeout settings.</p> 
  
  <p>
    Although ADDP settings between LCA and SCS was available in previous versions, Genesys made it official from 8.0 onwards.
  </p>
  
  <p>
    To configure ADDP, follow the steps below
  </p>
  
  <ul>
    <li>
      In Genesys Administrator—Host object > Options tab > Advanced View (Annex)
    </li>
    <li>
      In Configuration Manager—Host object > Properties dialog box > Annex tab
    </li>
    <li>
      Configure section <b>&#8216;addp&#8217;</b>
    </li>
    <li>
      Under this section, configure option <b>&#8216;addp-timeout&#8217; </b>with value greater than 10 (recommended). This value is used by Solution Control Server for ADDP timeout. If SCS doesn&#8217;t receive messages within this interval, it sends polling message and waits for response for the same interval. It interprets lack of response as loss of connection
    </li>
    <li>
      Under the same section (&#8216;addp&#8217;), configure option <b>&#8216;addp-remote-timeout&#8217;</b> with value greater than 0. This value is used by LCA for ADDP timeout and passed by SCS after the connection is established. If LCA doesn&#8217;t receive message from SCS within this interval, it sends polling message and waits for response for the same interval. It interprets lack of response as loss of connection. I recommend setting this value as &#8216;addp-timeout&#8217; + 5.
    </li>
    <li>
      configure option <b>&#8216;addp-trace&#8217;</b> to both to enable tracing at both endpoints
    </li>
  </ul>
  
  <p>
    <i><b>Note: </b>If this value is set to 0, LCA will not use ADDP. </i></div>