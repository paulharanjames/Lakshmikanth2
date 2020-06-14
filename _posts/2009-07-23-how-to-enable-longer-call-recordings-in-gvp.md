---
id: 691
title: How to enable longer call recordings in GVP ?
date: 2009-07-23T15:08:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=691
permalink: /2009/07/23/how-to-enable-longer-call-recordings-in-gvp/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/07/how-to-enable-longer-call-recordings-in.html
  - /2009/07/how-to-enable-longer-call-recordings-in.html
dsq_thread_id:
  - "2835620765"
  - "2835620765"
categories:
  - Genesys
  - GVP
  - How to
  - Installation
---
To enable longer call recordings in GVP, you need to change the configuration value in GVP and procedure is as follows:

1. Open IIS.  
2. Right-click the server, and then select Properties.  
3. Select the **Enable Direct Metabase Edit** check box, and then click OK.  
4. Open the MetaBase.xml file, which is located in “**C:\WINNT\System32\Inetsrv”  
** 5. Locate the line **AspMaxRequestEntityAllowed**, and change it to 524288000. 

Please note that the above steps was tested in IIS 6.0 version and above