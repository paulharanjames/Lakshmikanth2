---
id: 851
title: Configure Configuration Server in CME
date: 2009-02-23T18:39:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=851
permalink: /2009/02/23/configure-configuration-server-in-cme/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2009/02/configure-configuration-server-in-cme.html
dsq_thread_id:
  - "2901901352"
categories:
  - CME
  - Configuration Manager
  - Configuration Server
  - Genesys
  - How to
  - Management Layer
---
The Configuration Server Application object is preconfigured in the Configuration Database. You need to make the below changes in the Configuration  
Server Application in CME for Management Layer to control Configuration Server:

  1. Open Configuration Manager aka CME
  2. Create a ‘**Host’** object for the computer on which Configuration Server runs
  3. Open the Properties dialog box of the ‘**Configuration Server’** Application (named **‘confserv’**)
  4. Click the **‘Server Info’** tab
  5. Click Browse to select the Host that you created in **Step 2**
  6. On the ‘**Start Info’** tab, define the **‘Working Directory’** and **‘Command Line’** properties for the primary Configuration Server
  7. Click **OK** to save the changes.