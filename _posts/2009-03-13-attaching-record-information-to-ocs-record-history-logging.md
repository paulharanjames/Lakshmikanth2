---
id: 781
title: Attaching Record information to OCS Record History logging
date: 2009-03-13T00:33:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=781
permalink: /2009/03/13/attaching-record-information-to-ocs-record-history-logging/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/03/attaching-record-information-to-ocs.html
  - /2009/03/attaching-record-information-to-ocs.html
dsq_thread_id:
  - "2927831623"
  - "2927831623"
categories:
  - Configuration
  - Dialer (OCS)
  - Genesys
  - How to
  - OCS
  - Record History
---
Record History logging provides you with additional reporting options for

calling lists. This logging process does not use database access to write logs;

instead it uses flat (text) files that the customer defines. You can turn enable this logging for selective calling lists.

**How to configure Record history logging:**

  * In CME, select the calling list 
  * Go to Annex Tab and create section **‘default’**, if not available already 
  * Create option **‘dial\_log\_destination’** with value as **‘Folder Path’** to store record history log files 
  * Create Option **‘dial\_log\_delimiter’** with value as **‘,’** to create comma separated delimiter between the fields 

By default, it attaches the below mentioned mandatory fields

  * record_id 
  * contact_info 
  * contact\_info\_type 
  * record_type 
  * record_status 
  * call_result 
  * attempt 
  * dial\_sched\_time 
  * call_time 
  * daily_from 
  * daiy_till 
  * tz_dbid 
  * agent_id 
  * chain_id 
  * chain_n 

If you want to attach user-defined fields in the record history logging, please follow the steps below

  * In CME, select the field . 
  * Go to Annex Tab and create section ‘default’, if not available already. 
  * Create Option ‘send_attribute’ with value as field name. 

Record History log will then have the value with key as field name and value.. 🙂 

I am playing with Genesys 8.0 and planned to cover the details in the coming weeks.. keep watching this space..