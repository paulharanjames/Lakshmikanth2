---
id: 5271
title: 'Design Patterns &#8211; External Configuration Store Pattern'
date: 2015-03-05T11:52:01+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5271
permalink: /2015/03/05/design-patterns-external-configuration-store-pattern/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3583212386"
  - "3583212386"
categories:
  - Architecture
  - Design Patterns
  - Genesys
tags:
  - Architecture
  - Design Patterns
  - External Configuration Store
---
In my previous post, I discussed about [&#8216;Runtime Reconfiguration Pattern&#8217; ](http://www.lakshmikanth.com/design-patterns-runtime-reconfiguration-pattern/ "Design Patterns – Runtime Reconfiguration Pattern") and how it can be applied in Genesys environment.It is easy to implement &#8216;Runtime Reconfiguration Pattern&#8217; in Genesys and realize benefits for server applications. For client applications,  I recommend to use &#8216;External Configuration Store&#8217; pattern along with &#8216;Runtime Reconfiguration&#8217; to improve availability and scalability.

### Problem

* * *

### 

The majority of application runtime environments include configuration information that is held in files deployed with the application, located within the application folders. In some cases it is possible to edit these files to change the behavior of the application after it has been deployed. However, in many cases, changes to the configuration require the application to be redeployed, resulting in unacceptable downtime and additional administrative overhead. For example, if you want to change log folder location for Softphone and you need to make changes in all agent desktops.

Local configuration files also limit the configuration to a single application, whereas in some scenarios it would be useful to share configuration settings across multiple applications. Examples include database connection strings, Phone book, Transfer directory etc and storage used by a related set of applications.

In addition, updates to applications and components may require changes to configuration schemas.

### Solution

* * *

Most of the problems can be addressed by using Configuration Server to store information. On large contact centers with 2K+ agents,  it overloads configuration server and any load on core servers should be avoided.

### Solution #1 : Use Configuration Server Proxy

* * *

Straightforward solution. Install Configuration Server Proxy and direct client application traffic to proxy

### Solution #2 : Use custom application

* * *

Use custom application to store and provide configuration data as below

<div id="attachment_5281" style="width: 797px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/External-Configuration-Store.png"><img aria-describedby="caption-attachment-5281" class="wp-image-5281 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/External-Configuration-Store.png" alt="External Configuration Store" width="787" height="328" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/External-Configuration-Store.png 787w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/External-Configuration-Store-300x125.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/03/External-Configuration-Store-768x320.png 768w" sizes="(max-width: 787px) 100vw, 787px" /></a>
  
  <p id="caption-attachment-5281" class="wp-caption-text">
    External Configuration Store Pattern
  </p>
</div>

&nbsp;

My personal preference is to use custom application to store configuration data for the following reasons

  * Flexibility to store different types of data like collections, XML document etc. Particularly useful, if you want to store phone book, personal speed dials etc.
  * Easy to store multiple versions of configuration settings. For example, user may want to use different set of transfer directory numbers for holiday period only
  * Implement business rules &#8211; Depending on user, machine, site or IP address range allows you to present different configuration settings
  * Can be used as load balancing solution. In many cases &#8211; almost in all scenarios, client applications are configured to use dedicated instance of server applications like CS Proxy or Stat Server. For example, when agent logs in,  custom application can provide CS proxy details from pool instead of dedicated instance, which increases availability and performance

In my next post, I will cover another interesting pattern &#8216;Cache Aside&#8217; to improve application performance.