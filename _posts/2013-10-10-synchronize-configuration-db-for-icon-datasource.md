---
id: 181
title: Synchronize Configuration DB for ICON Datasource
date: 2013-10-10T09:53:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=181
permalink: /2013/10/10/synchronize-configuration-db-for-icon-datasource/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/10/synchronize-configuration-db-for-icon.html
  - /2013/10/synchronize-configuration-db-for-icon.html
dsq_thread_id:
  - "2941714366"
  - "2941714366"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - ICON
  - Infomart
  - Tips
---
This is interesting and saved hours for me.

During migration or upgrade of ICON components, as ICON application is not running, it will not be collecting configuration changes from the environment. So, once the installation is completed, we need to resync configuration database for accurate reporting.

Follow the below procedure to re-sync your Config IDB with configuration server

  * Verify that the ICON application with the configuration option **role=cfg** is started.
  * In Configuration Manager, set the **start-cfg-sync** option under **callconentrator** section from -1 to 0 in the Application Properties window of this ICON application.
  * Click **OK** in the option properties window.
  * Click **Apply** in the ICON Application Properties window to enable this setting.
  * Change the option value to 1.
  * Click **OK** in the option properties window.
  * Click Apply in the ICON Application Properties window to enable this new setting.

**Verify Status from log and Database**

When ICON retrieves from Configuration Server all the data necessary for resynchronization, ICON generates the following Standard-level log event:

_09-25017 Configuration objects are reloaded in IDB_

Run the following query against your configuration IDB

<pre class="lang:tsql decode:true ">select eventid from G_SYNC_CONTROL where providertag = 5</pre>

&nbsp;

If the above statement returns no records or eventID = 0, the resynchronization is still in progress.

If the above statement returns a non-zero value of eventID, the resynchronization is completed, and it is safe to run your GIM process