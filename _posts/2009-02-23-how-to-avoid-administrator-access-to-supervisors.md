---
id: 831
title: How to avoid ‘Administrator’ access to supervisors?
date: 2009-02-23T18:55:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=831
permalink: /2009/02/23/how-to-avoid-administrator-access-to-supervisors/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/02/how-to-avoid-administrator-access-to.html
  - /2009/02/how-to-avoid-administrator-access-to.html
dsq_thread_id:
  - "2798440611"
  - "2798440611"
categories:
  - Access Group
  - CME
  - Configuration Manager
  - Genesys
  - How to
  - Security
---
In Genesys, if you are configuring non-agent, they are automatically added to the ‘Administrators’ access group. Many times, we have to configure Supervisors and would like to provide access to their agent group only. Prior to 7.6 version, it is achieved by creating new access group and removing the person from Administrators group.

From 7.6, you can disable the default access to the users. For every user, you need to manually assign him to the access group. 

To disable the default access, create section **‘Security’** in Configuration Server ‘**Options’** tab and configure the option to **‘no-default-access’** to **‘0’.** Simple and found it useful to avoid any human errors