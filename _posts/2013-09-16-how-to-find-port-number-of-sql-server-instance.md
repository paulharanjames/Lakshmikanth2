---
id: 191
title: How to find port number of SQL Server instance?
date: 2013-09-16T14:10:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=191
permalink: /2013/09/16/how-to-find-port-number-of-sql-server-instance/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/09/how-to-find-port-number-of-sql-server.html
  - /2013/09/how-to-find-port-number-of-sql-server.html
dsq_thread_id:
  - "2970650558"
  - "2970650558"
categories:
  - Tips
---
<div dir="ltr" trbidi="on">
  </p> 
  
  <ul>
    <li>
      Click <strong>Start </strong>> <strong>All Programs </strong>> <strong>Microsoft SQL Server <2005 / 2008 / 2012> </strong>> <strong>Configuration Tools </strong>><strong>SQL Server Configuration Manager</strong>
    </li>
    <li>
      Go to <strong>SQL Server Configuration Manager </strong>> <strong>SQL Server Network Configuration </strong>><strong>Protocols for <Instance Name></strong>
    </li>
    <li>
      Right Click on <strong>TCP/IP </strong>and select <strong>Properties</strong>
    </li>
  </ul>
  
  <p>
  </p>
  
  <div>
  </div>
  
  <p>
  </p>
  
  <div>
    <a href="http://2.bp.blogspot.com/-grmoPvzT6L0/UjcSbMB6DTI/AAAAAAAAAGw/y53N9-AB8Kk/s1600/Protocol+Configuration.JPG" imageanchor="1"><img border="0" height="328" src="http://2.bp.blogspot.com/-grmoPvzT6L0/UjcSbMB6DTI/AAAAAAAAAGw/y53N9-AB8Kk/s640/Protocol+Configuration.JPG" width="640" /></a>
  </div>
  
  <ul>
    <li>
      In <strong>TCP/IP Properties </strong>dialog box, go to <strong>IP Addresses </strong>tab and scroll down to <strong>IPAll </strong>group.
    </li>
  </ul>
  
  <div>
    <a href="http://4.bp.blogspot.com/-sENLK98d8as/UjcSbJqZ7PI/AAAAAAAAAG8/UDkQQZD3uog/s1600/TCP+IP+Properties.JPG" imageanchor="1"><img alt="" border="0" height="400" src="http://4.bp.blogspot.com/-sENLK98d8as/UjcSbJqZ7PI/AAAAAAAAAG8/UDkQQZD3uog/s400/TCP+IP+Properties.JPG" title="" width="366" /></a>
  </div>
  
  <ul>
    <li>
      If SQL Server if configured to run on a static port it will be available in <strong>TCP Port </strong>textbox. If it is configured on dynamic port then current port will be available in <strong>TCP Dynamic Ports </strong>textbox
    </li>
  </ul>
</div>