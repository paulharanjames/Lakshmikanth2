---
id: 731
title: How to determine which version of SQL Server 2005 is running
date: 2009-07-13T17:34:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=731
permalink: /2009/07/13/how-to-determine-which-version-of-sql-server-2005-is-running/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/07/how-to-determine-which-version-of-sql.html
  - /2009/07/how-to-determine-which-version-of-sql.html
dsq_thread_id:
  - "3010263726"
  - "3010263726"
categories:
  - DB Server
  - Genesys
  - How to
  - SQL Server 2005
  - SQL Server Express 2005
---
Whenever I raise SR with Genesys, they request for DB Version (exact version) to troubleshoot the problem. Here, I listed one easy way to find SQL Server 2005 version 🙂

To determine which version of Microsoft SQL Server 2005 is running, connect to SQL Server 2005 by using SQL Server Management Studio, and then run the following Transact-SQL statement.

SELECT  SERVERPROPERTY(&#8216;productversion&#8217;), SERVERPROPERTY (&#8216;productlevel&#8217;), SERVERPROPERTY (&#8216;edition&#8217;)

The following results are returned: 

  * The product version (for example, 9.00.1399.06) 
  * The product level (for example, RTM) 
  * The edition (for example, Enterprise Edition)

Reference: [http://support.microsoft.com/kb/321185](http://support.microsoft.com/kb/321185 "http://support.microsoft.com/kb/321185")