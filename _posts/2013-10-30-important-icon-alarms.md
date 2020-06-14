---
id: 161
title: Important Icon Alarms
date: 2013-10-30T16:57:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=161
permalink: /2013/10/30/important-icon-alarms/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/10/important-icon-alarms_30.html
  - /2013/10/important-icon-alarms_30.html
dsq_thread_id:
  - "2756229442"
  - "2756229442"
categories:
  - ICON
  - Tips
  - Troubleshooting
---
<div dir="ltr" trbidi="on">
  <p>
    I listed important ICON alarms below to be configured in every environment to reduce data loss for reporting application
  </p>
  
  <table border="1" cellpadding="2" cellspacing="0">
    <tr>
      <td valign="top" width="108">
        <strong>Detect Event</strong>
      </td>
      
      <td valign="top" width="264">
        <strong> Alarm Condition</strong>
      </td>
      
      <td valign="top" width="341">
        <strong> Description</strong>
      </td>
    </tr>
    
    <tr>
      <td valign="top" width="108">
        <strong>09-25005</strong>
      </td>
      
      <td valign="top" width="269">
        ICON_DATABASE_QUEUE_ERROR
      </td>
      
      <td valign="top" width="337">
        Database queue [ID]: database error received: status [errnum], description: [errtxt] <br />[<strong>ID</strong>]<br />Identifier of the database queue. One of the following values: CFG, GCC, GLS, GOS, or GUD. <br />[<strong>errnum</strong>]<br />The database error status number as reported by Database Server. <br />[<strong>errtxt</strong>]<br />The database error description as reported by Database Server <br /><strong>Recommended Actions:</strong><br /> The error may be triggered by internal conditions on your SQL Server, such as temporary unavailability or exhaustion of the disk space. Interaction Concentrator will try to resubmit failed transactions until SQL Server returns a positive response. </p>
      </td>
    </tr>
    
    <tr>
      <td valign="top" width="107">
        <strong>09-25012</strong>
      </td>
      
      <td valign="top" width="274">
        ICON_PERSISTENT_QUEUE_ERROR
      </td>
      
      <td valign="top" width="334">
        Persistent Queue operation error: [<strong>errtxt</strong>]<br />[<strong>errtxt</strong>]<br />Persistent queue error description. <br />An error occurred during the operations with the persistent queue <br /><strong>Recommended Actions:</strong><br /> Interaction Concentrator will rename the database that caused an error and recreate a new one. The problem database file should be sent to Genesys Technical Support. </p>
      </td>
    </tr>
    
    <tr>
      <td valign="top" width="106">
        <strong>09-25131</strong>
      </td>
      
      <td valign="top" width="278">
        ICON_CONFIG_SYNCH_REQUIRED
      </td>
      
      <td valign="top" width="332">
        Configuration data inconsistency is detected; reason: [reason]. Waiting for customer command&#8230;. <br />[<strong>reason</strong>]<br />Specific details as to why data inconsistency is suspected. <br />Indicates that Interaction Concentrator has detected a discrepancy between the configuration data in Interaction Database (IDB) and Configuration Database <br /><strong>Recommended Actions:</strong> <br />Use the Interaction Concentrator resynchronization functionality (in particular, the start-cfg-sync configuration option) to synchronize the configuration data in IDB with the data in Configuration Database.  Make sure the resynchronization process is complete before you run your ETL engine to extract data from IDB <br />Cancel Event is <strong>09-25017</strong></p> 
        
        <p>
          </td> </tr> 
          
          <tr>
            <td valign="top" width="106">
              <strong>09-25024</strong>
            </td>
            
            <td valign="top" width="281">
              ICON_PRESERVE_ERROR
            </td>
            
            <td valign="top" width="330">
              ICON cannot preserve or store the data: [errtxt] <br />[errtxt]<br />Specific details regarding the error <br />Interaction Concentrator cannot preserve or store the data. There are many events that could cause ICON to generate this error, including operating systems errors, disk full, insufficient memory, system queue corruption, or internal software errors. Manual intervention is required <br /><strong>Recommended Actions:</strong></p> 
              
              <ol>
                <li>
                  Check for and correct any operating system errors.
                </li>
                <li>
                  Check that your disk is not full.
                </li>
                <li>
                  If either step does not resolve the problem, contact Genesys Technical Support for investigation of possible internal error
                </li>
              </ol>
            </td>
          </tr>
          
          <tr>
            <td valign="top" width="105">
              <strong>09-25025</strong>
            </td>
            
            <td valign="top" width="283">
              ICON_STORAGE_THRESHOLD_REACHED
            </td>
            
            <td valign="top" width="328">
              Persistent storage backlog threshold reached: [<strong>errtxt</strong>] <br />[<strong>errtxt</strong>]<br />Specific details regarding the backlog <br />Using the pq-backlog-alarm-threshold configuration option, you have defined a threshold that ICON is to observe when it is unable to write records to IDB. If this event appears, this limit has been reached and ICON can no longer backlog records to memory. <br />It is common for ICON to log this event following 09-25024 <br /><strong>Recommended Actions:</strong><br /> One of the configured backlog thresholds of persistent storage has been reached. </p> 
              
              <ol>
                <li>
                  Check that threshold parameter is properly set.
                </li>
                <li>
                  Check the ICON and related T-Server logs for errors.
                </li>
                <li>
                  Correct any problems that you discover.
                </li>
              </ol>
              
              <p>
                The amount of time it takes to clear the backlog depends on how much data from the abnormal condition must be flushed. <br />Cancel Event is <strong>09-25026</strong>
              </p>
            </td>
          </tr></tbody> </table> </div>