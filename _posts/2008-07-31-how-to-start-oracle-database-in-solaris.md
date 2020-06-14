---
id: 1001
title: How to start Oracle Database in Solaris
date: 2008-07-31T11:31:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=1001
permalink: /2008/07/31/how-to-start-oracle-database-in-solaris/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2008/07/how-to-start-oracle-database-in-solaris.html
  - /2008/07/how-to-start-oracle-database-in-solaris.html
dsq_thread_id:
  - "3245245033"
  - "3245245033"
categories:
  - How to
---
# <span>Starting the Oracle Database</span>

Follow the below mentioned steps to start the oracle database

</p> 

  * sqlplus /nolog


  * connect username/password as sysdba


  * On sqlplus prompt, type startup
</ul> 

This will start the oracle database instance successfully.

# <span>Starting the Listener</span>

The listener can be started before or after the database instance is started, it doesn&#8217;t matter. You can start the listener with a simple _lsnrctl start_:

<pre><em>bash-2.05$ lsnrctl start<br />LSNRCTL for Solaris: Version 10.1.0.2.0 - Production on 11-OCT-2004 15:42:55<br />Copyright (c) 1991, 2004, Oracle.  All rights reserved.<br />Starting /u01/app/oracle/product/10.1.0/db_1/bin/tnslsnr: please wait...<br /><br />TNSLSNR for Solaris: Version 10.1.0.2.0 - Production<br />System parameter file is /u01/app/oracle/product/10.1.0/db_1/network/admin/listener.ora<br />Log messages written to /u01/app/oracle/product/10.1.0/db_1/network/log/listener.log<br />Listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=10.10.0.130)(PORT=1521)))<br />Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=10.10.0.130)(PORT=1521)))<br />STATUS of the LISTENER<br />------------------------<br />Alias                     LISTENER<br />Version                   TNSLSNR for Solaris: Version 10.1.0.2.0<br />Start Date                11-JUL-2008 15:42:55<br />Uptime                    0 days 0 hr. 0 min. 0 sec<br />Trace Level               off<br />Security                  ON: Local OS Authentication<br />SNMP                      OFF<br />Listener Parameter File   /u01/app/oracle/product/10.1.0/db_1/network/admin/listener.ora<br />Listener Log File         /u01/app/oracle/product/10.1.0/db_1/network/log/listener.log<br />Listening Endpoints Summary...<br />  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=10.5.11.118)(PORT=1521)))<br />Services Summary...<br />Service "genesys" has 1 instance(s).<br />  Instance "genesys", status UNKNOWN, has 1 handler(s) for this service...<br />The command completed successfully</em></pre>