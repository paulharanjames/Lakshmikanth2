---
id: 5201
title: 'Design Patterns &#8211; Runtime Reconfiguration Pattern'
date: 2015-03-04T22:08:19+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5201
permalink: /2015/03/04/design-patterns-runtime-reconfiguration-pattern/
dsq_thread_id:
  - "3567696347"
  - "3567696347"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Design Patterns
  - Genesys
tags:
  - Design Patterns
  - Runtime Reconfiguration
---
Currently, I am in the process of design and development of custom server application to generate contact center intraday reports on regular intervals and send it to operations team. As with any other contact center servers, this is critical for business to run their operations. I was working on Microsoft Azure for cloud based services and always want to bring cloud benefits &#8211; however small it is &#8211; to enterprise customers.

One of the main benefit for cloud based solution is &#8216;always on&#8217; and &#8216;Runtime Reconfiguration Pattern&#8217; is used to reduce downtime for this.

### Problem

* * *

### 

  * Agents can be added or removed from reporting group at any time
  * Queues can be added or removed from reporting group at any time
  * Ability to support new reporting templates
  * Ability to change report name and file format

All these changes to be applied while the application is running and should not impact other application functionalities. &#8216;Runtime Reconfiguration Pattern&#8217; is the perfect solution here.

### Pattern overview

* * *

### 

Typically, hosting infrastructure sends notifications for any configuration changes. Application will examine the change and apply them to relevant components. From this point onwards, application will use new configuration value in the application.

More details about this pattern can be found from Microsoft site <a href="https://msdn.microsoft.com/en-us/library/dn589785.aspx" target="_blank" rel="noopener noreferrer">here</a>

<div style="width: 591px" class="wp-caption alignnone">
  <img class="" src="https://i-msdn.sec.s-msft.com/dynimg/IC709510.png" alt="" width="581" height="200" />
  
  <p class="wp-caption-text">
    Runtime Reconfiguration Pattern
  </p>
</div>

### Implementation

* * *

### 

Runtime Reconfiguration Pattern is used heavily by Genesys to support dynamic changes. For example, any changes made by Genesys CME or Administrator are applied dynamically to relevant servers using notifications.

In my application, I used Genesys Platform SDK &#8211; Configuration Server to get notifications and handled changes. Here are design implementation details

  * Store only configuration server details locally
  * On startup, connect to configuration server and retrieve details from application options
  * Subscribe for change notifications from Configuration Server
  * Application is running now
  * When application configuration is changed using CME or Genesys Administrator, Configuration Server sends notification to application
  * Changes are examined and applied to relevant modules within the application

### When to use this in Genesys environment

* * *

### 

I strongly recommend to use this pattern for server applications only as it uses single connection with configuration server. For client applications like Softphone, it is not recommended as it will use one connection for each instance, which will increase load on Configuration server and severely impacts operation when it crosses 2K connection.

If it is absolutely required, I suggest developing custom server application to support this. I will cover the details for this in my next post.