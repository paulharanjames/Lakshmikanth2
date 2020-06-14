---
id: 4681
title: 'MSSQL Server 2008 &#8211; Reset sa password'
date: 2014-12-05T23:01:40+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4681
permalink: /2014/12/05/mssql-server-2008-reset-sa-password/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3301824454"
  - "3301824454"
categories:
  - How to
  - Troubleshooting
tags:
  - SQL Server
  - Troubleshooting
---
In this week, we were implementing PoC environment for voice analytics solution and received VMware image from vendor. After hosting image in our environment, which obviously required server name, IP address and domain changes, they were unable to login into SQL Server 2008 database.

We need to do &#8216;sa&#8217; password reset and followed steps below for the same. Hope this helps.

  * From windows services, stop **SQLServer(MSSQLServer)** service

<div id="attachment_4791" style="width: 646px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQL_Server_Services_001.png"><img aria-describedby="caption-attachment-4791" class="wp-image-4791 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQL_Server_Services_001.png" alt="SQLServer Services" width="636" height="127" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQL_Server_Services_001.png 636w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQL_Server_Services_001-300x60.png 300w" sizes="(max-width: 636px) 100vw, 636px" /></a>
  
  <p id="caption-attachment-4791" class="wp-caption-text">
    SQLServer Services
  </p>
</div>

  * Open SQL Server Configuration Manager ( **Start -> All Programs -> Microsoft SQL Server 2008 R2 -> Configuration Tools -> SQL Server Configuration Manager**)
  * Select **SQL Server Services -> SQL Server(MSSQLServer)**. Right click and select **&#8216;Properties&#8217;**
  * Go to **&#8216;Advanced&#8217;** tab and change startup parameters by prefixing **-m; **as below

[<img class="aligncenter size-full wp-image-4781" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_Properties_001.png" alt="Prefix -m;" width="393" height="434" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_Properties_001.png 393w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_Properties_001-272x300.png 272w" sizes="(max-width: 393px) 100vw, 393px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_Properties_001.png)

  * Click **&#8216;Ok&#8217;** to save the changes
  * Start **&#8216;SQLServer(MSSQLServer)&#8217;** from windows services
  * Open command prompt (**Start -> Run -> cmd** and press **&#8216;Enter&#8217;**)
  * Type **&#8216;sqlcmd&#8217; **to start SQL command window and create new user as below

<div id="attachment_4701" style="width: 679px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/CreateLogin.png"><img aria-describedby="caption-attachment-4701" class="wp-image-4701 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/CreateLogin.png" alt="Create Login" width="669" height="147" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/CreateLogin.png 669w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/CreateLogin-300x66.png 300w" sizes="(max-width: 669px) 100vw, 669px" /></a>
  
  <p id="caption-attachment-4701" class="wp-caption-text">
    sqlcmd
  </p>
</div>

<pre class="lang:tsql decode:true " title="Create Login">create login lucky with password='BeHappy#3'
print 'User lucky is created'
sp_addsrvrolemember ‘lucky’, ‘sysadmin’
go
</pre>

  *  Stop SQLServer(MSSQLService) from windows services
  * Remove **&#8216;-m&#8217; **from startup parameters, click &#8216;Ok&#8217; to apply the changes and start SQLServer(MSSQLService) service

[<img class="aligncenter size-full wp-image-4741" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_default.png" alt="SQLServer_default" width="392" height="433" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_default.png 392w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_default-272x300.png 272w" sizes="(max-width: 392px) 100vw, 392px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/SQLServer_default.png)

  * Open &#8216;**SQL Server Management Studio&#8217;** and login using newly created account (_username : lucky, password=&#8217;BeHappy#3&#8242;_)
  * Right-click login account **&#8216;sa&#8217;** from **&#8216;Security -> Login&#8217; **and select **&#8216;Properties&#8217;**

<div id="attachment_4721" style="width: 443px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/sa_properties.png"><img aria-describedby="caption-attachment-4721" class="wp-image-4721 " src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/sa_properties.png" alt="sa_properties" width="433" height="551" /></a>
  
  <p id="caption-attachment-4721" class="wp-caption-text">
    &#8216;sa&#8217; login properties
  </p>
</div>

  * Change the password

<div id="attachment_4711" style="width: 710px" class="wp-caption aligncenter">
  <img aria-describedby="caption-attachment-4711" class="wp-image-4711 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/sa_password.png" alt="sa_password" width="700" height="285" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/sa_password.png 700w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/sa_password-300x122.png 300w" sizes="(max-width: 700px) 100vw, 700px" />
  
  <p id="caption-attachment-4711" class="wp-caption-text">
    Reset &#8216;sa&#8217; password
  </p>
</div>