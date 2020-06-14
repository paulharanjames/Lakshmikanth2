---
id: 3681
title: 'Genesys CCPulse &#8211; How to show when agent logged in?'
date: 2014-09-10T16:49:29+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=3681
permalink: /2014/09/10/genesys-ccpulse-logged-in/
dsq_thread_id:
  - "3007605356"
  - "3007605356"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - How to
tags:
  - CCPulse
  - Genesys
  - How to
  - Reporting
---
Few months ago, I wrote an post about Genesys CCPulse powerful feature ([Read here](http://www.lakshmikanth.com/most-powerful-and-less-popular-feature-in-ccpulse/ "CCPulse – Very powerful but less popular feature")) and explained how JScript language can be used to show various other details within CCPulse. Last week, I had requirement from contact center supervisor to view agent&#8217;s login time i.e.) when they logged in. We needed this information to analyze default routed calls by looking at load on Genesys servers and WAN bandwidth.

In this post, I will explain the steps to show agent&#8217;s logged in time in CCPulse as below

[<img class="aligncenter wp-image-3701 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png" alt="Genesys CCPulse - lastloggedin" width="726" height="139" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png 726w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin-300x57.png 300w" sizes="(max-width: 726px) 100vw, 726px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png)

&nbsp;

# Step 1 : Configure StatServer to store login data

* * *

&nbsp;

  * Create new database [StatServerDB] and initialize it with scripts from StatServer folder. Refer to StatServer Deployment Guide Appendix A for more information about database and tables
  * Login into CME, create new DAP [RealtimeReportingDAP] application and configure it to use [StatServerDB]
  * Open StatServer application, add [RealtimeReportingDAP] in the connections DAP
  * Go to &#8216;Options&#8217; tab in Statserver application, open section &#8216;statserver&#8217; and set option &#8216;login-table&#8217; to &#8216;true&#8217;

[<img class="aligncenter wp-image-3711 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/StatServerOption.png" alt="Genesys CCPulse - StatServerOption" width="479" height="459" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/StatServerOption.png 479w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/StatServerOption-300x287.png 300w" sizes="(max-width: 479px) 100vw, 479px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/StatServerOption.png)

&nbsp;

# Step 2: Configure CCPulse application

* * *

&nbsp;

  * Open CCPulse application -> Options  -> CustomStatistic section and change &#8216;ExtendedCurrentStatus&#8217; to &#8216;true&#8217;

[<img class="aligncenter wp-image-3721 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/CCPulseCustomStatistic.png" alt="Genesys CCPulse - CustomStatistic" width="578" height="202" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/CCPulseCustomStatistic.png 578w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/CCPulseCustomStatistic-300x105.png 300w" sizes="(max-width: 578px) 100vw, 578px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/CCPulseCustomStatistic.png)

&nbsp;

# Step 3: Create &#8216;LastLoggedIn&#8217; field in CCPulse Template

* * *

  *  Login into CCPulse application and open &#8216;Template Wizard&#8217;
  * Select object type as &#8216;Agent&#8217;, select the template to modify it from the options and click &#8216;Next&#8217;
  * Click &#8216;Formula&#8217; to create new reporting field and click &#8216;Properties&#8217; to open expression editor
  * Copy and paste the code below. Update database details in the code and Click &#8216;Ok&#8217; to complete it.
  * Open agent report using this template and you will see last login time of the agent

[<img class="aligncenter size-full wp-image-3701" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png" alt="Genesys CCPulse - LastLoggedIn" width="726" height="139" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png 726w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin-300x57.png 300w" sizes="(max-width: 726px) 100vw, 726px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/09/lastloggedin.png)

<pre class="toolbar-overlay:false lang:vb decode:true" title="Last Login Script">var objRs=new ActiveXObject("ADODB.Recordset")
var strConn="Provider=SQLOLEDB.1;Data Source=&lt;SQLServer Instance&gt;;Initial Catalog=&lt;Statserver Database&gt;;User Id=&lt;UserName&gt;;Password=&lt;UserPassword&gt;;"
strEmployeeID=state.LoginID
strQuery=" select top 1 dbo.ConvertToLocalTime([Time]) as Logintime from [Login] "
strQuery+="where LOGINID='"+strEmployeeID+"' "
strQuery+=" and left (dbo.ConvertToLocalTime([Time]),11) = left(getdate(),11) "
strQuery+=" and status = '1' order by logintime desc"
objRs.Open(strQuery,strConn,3,1,1)
var resultCount="";
if(!objRs.BOF)
{
objRs.MoveFirst();
while(!objRs.EOF)
{
if(objRs("Logintime").value!=null)
{
	resultCount=objRs("Logintime").value
}
objRs.MoveNext();
}
}
objRs.Close
objRs=null;
resultCount; 
</pre>

StatServer stores time in Unix format and hence, use below SQL script to convert field into local time

<pre class="toolbar-overlay:false lang:tsql decode:true " title="ConvertToLocalTime">create function converttolocaltime (@timestamp int)
returns datetime
as
begin
declare @ret datetime
declare @offset bigint, @localdate bigint;
    set @offset = datediff(second,getdate(),getutcdate());
    set @localdate = @timestamp - @offset;
select @ret = dateadd(second, @localdate, '1970/01/01 00:00:00')
return @ret
end
go</pre>

&nbsp;