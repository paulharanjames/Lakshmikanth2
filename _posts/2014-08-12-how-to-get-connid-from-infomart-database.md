---
id: 2641
title: 'Genesys Infomart Reporting &#8211; Get ConnID from GIM database'
date: 2014-08-12T14:43:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2641
permalink: /2014/08/12/how-to-get-connid-from-infomart-database/
dsq_thread_id:
  - "2923097113"
  - "2923097113"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - How to
tags:
  - Genesys
  - GIM
  - ICON
  - Infomart
---
Recently, I answered question about <a href="http://www.sggu.com/smf/index.php/topic,8465.0.html" target="_blank" rel="noopener noreferrer">&#8216;Conn Id in Infomart?&#8217;</a> in SGGU(www.sggu.com) forum and referred to the link &#8216;<span style="text-decoration: underline;"><a title="Genesys Reporting – Get ConnID from Infomart database" href="http://www.lakshmikanth.com/how-to-get-connid-from-infomart-database/">Link ConnId In Infomart&#8217;.</a> </span> However, requester want to retrieve Conn ID directly from Genesys Infomart. As Conn Id field is stored in decimal format in Infomart database (GIM), it was not useful as T-Server log uses hexadecimal format.

In C#, you can simply call Int64.ToString(&#8220;X&#8221;) to convert integer into hexadecimal format but there were no inbuilt functions within SQL Server. I wrote SQL Server function to convert decimal to hex as below..

<pre class="font:consolas font-size-enable:false toolbar-overlay:false show-lang:1 whitespace-before:1 whitespace-after:1 lang:tsql decode:true " title="ConvertToHex">CREATE FUNCTION ConvertToBase
(
    @value AS BIGINT
) RETURNS VARCHAR(MAX) 
AS 
BEGIN
    -- some variables
    DECLARE @characters CHAR(36),
            @result VARCHAR(MAX),
        @base int;
 
    -- the encoding string 
    SELECT @characters = '0123456789abcdefghijklmnopqrstuvwxyz',
           @result = '',
           @base = 16;
 
    -- Convert it into hex
    WHILE @value &gt; 0
        SELECT @result = SUBSTRING(@characters, @value % @base + 1, 1) + @result,
               @value = @value / @base;
 
    -- Prefix 0 
    set @result = N'0'+ @result;
    
    -- return our results
    RETURN @result;
 
END</pre>

Above function is Patrick Caldwell blog post about <a href="http://dpatrickcaldwell.blogspot.co.uk/2009/05/converting-decimal-to-hexadecimal-with.html" target="_blank" rel="noopener noreferrer">converting decimals to base numbers</a> and big thanks to him.

**Update 13-Aug-2014:**

SQL query to get Conn ID from Infomart database is as below

<pre class="font:consolas toolbar:1 toolbar-overlay:false whitespace-before:1 whitespace-after:1 lang:tsql decode:true  " title="Get ConnID">select top 1
	interaction_id,
	dbo.converttobase(media_server_ixn_id)
from
	interaction_segment_fact
order by
	interaction_id desc</pre>