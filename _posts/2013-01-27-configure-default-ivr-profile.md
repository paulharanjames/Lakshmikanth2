---
id: 221
title: Configure default IVR profile
date: 2013-01-27T20:29:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=221
permalink: /2013/01/27/configure-default-ivr-profile/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/01/configure-default-ivr-profile.html
  - /2013/01/configure-default-ivr-profile.html
dsq_thread_id:
  - "2671901505"
  - "2671901505"
categories:
  - Genesys
  - GVP
  - Tips
---
 

It is best practice to configure default IVR profile in GVP environment, in case, if your regular DN-Profile mapping is not happening. This post will explain step by step instructions to configure default profile

  * select your&#8217; ‘tenant’ object – in most cases, it is ‘Resources’ – under Administrator –> Provisioning –> Tenants
  * Create section gvp.general in options tab and update following values
  * name : _default-application_, value : _DefaultApp_ (Default IVR Profile application name)
  * name : _service-type_, value : _voicexml_

  * Click ‘_Save & Close_’ to save settings