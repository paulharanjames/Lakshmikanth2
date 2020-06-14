---
id: 4861
title: Report Abandoned calls in Routing Strategy
date: 2014-12-23T15:18:29+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4861
permalink: /2014/12/23/report-abandoned-calls-routing-strategy/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3352652739"
  - "3352652739"
categories:
  - Genesys
  - How to
  - Routing
tags:
  - Customer Experience
  - Routing
---
Last month, I attended workshop from Genesys and BT  and found an interesting trend. One of the customer shared that they were able to customer satisfaction and revenue by tracking and linking customer journey through multiple channels. For example, if customer selected products online for purchase and initiates call, they were able to link this and able to provide service. Simple and effective strategy.

Linking transactions across multiple channels is very big & interesting topic and will restrict to only voice channels in this post.

From my experience, I observed that many companies focus on active and answered calls by agent only. For example, C-SAT (Customer Satisfaction) survey are sent to customers which were answered by agent. What happens to customer disconnecting the call while waiting in queue? Most likely, these people are either looking for new service and simply switch to other provider. Others are left with no other option than wait 🙁 Imagine the potential loss of new customers and revenue..

In this post, I will explain how to record abandoned calls for reporting from the strategy (Francesc &#8211; Thanks for sharing this idea).

  * Database &#8211; Create Stored Procedure and Table
  * Configure DAP in CME
  * Create routing strategy for Abandoned Calls
  * Modify existing strategy to record abandoned calls

### Database &#8211; Create Stored Procedure and Table

* * *

In my environment, I made decision to record ANI, DNIS, Conn ID and Timestamp and in most cases, it is sufficient for analysis or to schedule call backs.

Script to create table &#8216;CallDetails&#8217;

<pre class="theme:monokai lang:tsql decode:true" title="calldetails">create table [dbo].[calldetails](
	[callerani] [nvarchar](50) null,
	[callerdnis] [nvarchar](50) null,
	[timestamp] [datetime] null,
	[connectionid] [nvarchar](50) null
) on [primary]

go
</pre>

Script to create stored procedure &#8216;SP_UpdateCallDetails&#8217;

<pre class="theme:monokai lang:tsql decode:true" title="sp_updatecalldetails">create procedure [dbo].[sp_updatecalldetails] 
	@varani nvarchar(30),
	@vardnis nvarchar(30),
	@varconnid nvarchar(30)
as
begin
	insert into calldetails values(@varani,@vardnis, getdate(),@varconnid)
end

go</pre>

###  Configure DAP in CME

* * *

Using Genesys Administrator or Configuration Manager, create new DAP &#8216;CustomDAP&#8217; to point to reporting database

### Create routing strategy for Abandoned Calls

* * *

  * Open IRD and create new routing strategy &#8216;RecordAbandonedCalls&#8217; as below

[<img class="size-full wp-image-4871" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/RoutingStrategy.png" alt="Routing Strategy to store abandoned calls" width="649" height="346" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/RoutingStrategy.png 649w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/RoutingStrategy-300x160.png 300w" sizes="(max-width: 649px) 100vw, 649px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/RoutingStrategy.png)

Routing Strategy

  * In function block, store Conn ID, ANI and DNIS values into variables varConnID, varANI and varDNIS
  * In database block, select &#8216;Custom DAP&#8217;  which was created in first step, select stored procedure and follow the wizard
  * In stored procedure screen, enter name as &#8216;sp_updatecalldetails&#8217; and add arguments as below 
      * Key = @varConnID and value = varConnID
      * Key = @varANI and value = varANI
      * Key = @varDNIS and value = varDNIS
  * Click next and select &#8216;Do not use output values&#8217;

### Modify existing strategy to record abandoned calls

* * *

In main strategy, add new function block after Entry and Target block as below

<div id="attachment_4891" style="width: 798px" class="wp-caption alignnone">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/FunctionProperties.png"><img aria-describedby="caption-attachment-4891" class="wp-image-4891 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/FunctionProperties.png" alt="OnCallAbandoned" width="788" height="536" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/FunctionProperties.png 788w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/FunctionProperties-300x204.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/12/FunctionProperties-768x522.png 768w" sizes="(max-width: 788px) 100vw, 788px" /></a>
  
  <p id="caption-attachment-4891" class="wp-caption-text">
    OnCallAbandoned
  </p>
</div>

Make test call and abandon it while waiting in queue. Now, you can see records in the database .You can use these records to create calling list for outbound campaign or schedule callback 🙂