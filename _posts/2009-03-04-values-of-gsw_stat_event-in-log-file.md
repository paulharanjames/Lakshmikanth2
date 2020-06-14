---
id: 801
title: Values of GSW_STAT_EVENT in log file
date: 2009-03-04T16:49:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=801
permalink: /2009/03/04/values-of-gsw_stat_event-in-log-file/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/03/values-of-gswstatevent-in-log-file.html
  - /2009/03/values-of-gswstatevent-in-log-file.html
dsq_thread_id:
  - "2749272669"
  - "2749272669"
categories:
  - Canned Reports
  - Dialer (OCS)
  - Genesys
  - OCS
  - Stat Server
  - Troubleshooting
---
Last week, customer reported an issue &#8216;Campaign Callback rescheduled call details are missing&#8217; in the canned reports. After few hours of log analysis, it seems to be a defect in Genesys Dialer (OCS) and raised SR with support team.

  I found this tabular list very useful while debugging reports for dialer solution and hope you will find it useful too

 CampaignActivated = 1,

CampaignDeactivated = 2,

DialingStarted = 3,

DialModeChanged = 4,

DialingStopped = 5,

WaitingAgentStart = 6,

WaitingAgentOver = 7,

WaitingPortsStart = 8,

WaitingPortsOver = 9,

WaitingRecordsStart = 10,

WaitingRecordsOver = 11,

SystemErrorStart = 12,

SystemErrorOver = 13,

CallCompleted = 14,

LeadProcessed = 15,

CallbackScheduled = 16,

CallbackCompleted = 17,

CallbackMissed = 18,

AgentError = 19,

RecordScheduled = 20,