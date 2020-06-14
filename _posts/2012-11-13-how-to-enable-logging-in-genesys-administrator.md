---
id: 261
title: How to enable logging in Genesys Administrator?
date: 2012-11-13T10:48:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=261
permalink: /2012/11/13/how-to-enable-logging-in-genesys-administrator/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2012/11/how-to-enable-logging-in-genesys.html
  - /2012/11/how-to-enable-logging-in-genesys.html
dsq_thread_id:
  - "2703889003"
  - "2703889003"
categories:
  - Genesys
  - Genesys Administrator
  - Tips
---
 

Genesys Administrator tracing can be enabled by changing the following in the <log4net> section (of Web.Config):

_<log4net>  
        <appender name="RollingLogFileAppender" type="log4net.Appender.RollingFileAppender">  
            <file value="logfile"/>  
            <appendToFile value="true"/>  
            <rollingStyle value="Composite"/>  
            <datePattern value="yyyyMMdd"/>  
            <!-- gst: append following to add .txt to file name:  .\\tx\\t -->

  
            <maxSizeRollBackups value="10"/>  
            <maximumFileSize value="1MB"/>  
            <layout type="log4net.Layout.PatternLayout">  
                <conversionPattern value="%date [%thread] %-5level %logger [%property{NDC}] - %message%newline"/>  
            </layout>  
        </appender>  
        <!-- gst added -->

  
        <appender name="TraceAppender" type="log4net.Appender.TraceAppender">  
            <layout type="log4net.Layout.PatternLayout">  
                <!--ConversionPattern value="%d [%t] %-5p %c - %m [%P{InstanceId}]%n" / -->

  
                <ConversionPattern value="%message%newline"/>  
            </layout>  
        </appender>_

> _<root>  
>    <level value="INFO"/>      
>   <!-- appender-ref ref="RollingLogFileAppender"/ -->
> 
>  
>    <appender-ref ref="TraceAppender"/>  
>   </root>_

to:

_<log4net>  
<appender name="RollingLogFileAppender" type="log4net.Appender.RollingFileAppender">  
<file value="galog.log"/>  
<appendToFile value="true"/>  
<rollingStyle value="Composite"/>  
<datePattern value="yyyyMMdd"/>  
<!-- gst: append following to add .txt to file name: .\\tx\\t -->

  
<maxSizeRollBackups value="10"/>  
<maximumFileSize value="1MB"/>  
<layout type="log4net.Layout.PatternLayout">  
<conversionPattern value="%date [%thread] %-5level %logger [%property{NDC}] - %message%newline"/>  
</layout>  
</appender>  
<!-- gst added -->

  
<appender name="TraceAppender" type="log4net.Appender.TraceAppender">  
<layout type="log4net.Layout.PatternLayout">  
<!--ConversionPattern value="%d [%t] %-5p %c - %m [%P{InstanceId}]%n" / -->

  
<ConversionPattern value="%message%newline"/>  
</layout>  
</appender>_  
  _<root>  
   <level value="DEBUG"/>  
   <appender-ref ref="RollingLogFileAppender"/>  
   <appender-ref ref="TraceAppender"/>  
  </root>_ 

For the above changes to take effect, you need to logout and login. You can now see file _**“galog.log”**_ will be created in the same installation path as Genesys Administrator