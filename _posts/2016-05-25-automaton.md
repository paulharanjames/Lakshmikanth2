---
id: 6681
title: 'Automaton &#8211; IT Process Automation'
date: 2016-05-25T13:54:34+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6681
permalink: /2016/05/25/automaton/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "4856601603"
  - "4856601603"
categories:
  - Genesys
  - How to
tags:
  - Automation
  - Automaton
  - Genesys
  - Outbound
---
## What is Automaton?

* * *

Automaton is simple, light-weight application to automate IT processes. Using this application, you can automate many processes &#8211; Directory & File Operations, Database, Genesys Health Check, Genesys Campaign Management, Genesys List Management, FTP, FTPS, SFTP, Email & SMS notifications and many more.

## Brief History

* * *

In our company meeting last year, we decided to focus on our core activities and outsource our internal process as much as we can. After few months, we realized that outsourcing helped us to move little bit faster but not as much as we thought will be. We sooner found that most of the process can be automated and self-serviced and started as internal tool development for us.

Although, it started as internal project, we can actually see that Automaton can be used by our customers as well and Automaton was started in Sep 2015.

## Key Benefits

* * *

  * Quick and easy implementation.Helps business to address market and customer needs in efficient manner
  * Reduce incident response and resolution time
  * Cuts cost of service operations

## Design Principles

* * *

From the beginning, we know that Automaton have to be open for extension as each customer will have different set of requirements to automate process and hence, we designed Automaton to be opened for extension i.e.) to add more functionality without modifying core application.

### <span style="color: #3366ff;"><em>&#8230;. And Reports</em></span>

As tasks will be automated, we understood that we need effective way of monitoring the tasks and hence, developed real time and historical reporting solution. Unlike traditional reporting, we want user to customize/apply filters on existing report and export them in PDF or Excel format. I will cover more details about this later

### <span style="color: #3366ff;"><em>&#8230; And Failover</em></span>

We built active-active failover functionality for this application. For Genesys related deployments, it can be integrated directly with the framework so that each instance can be monitored using SCI or Genesys Administrator and user can configure alarms for log messages.

## Some sample tasks

* * *

  * Automate FTP/FTPS/SFTP download and upload 
      * supports public/private key authentication, Kerberos, X-509, NTLM authentication types. I can safely say 100% of FTP/SFTP operations used in enterprises
  * Monitor application or windows service. Send email or sms alert if application stopped
  * File Operations &#8211; Copy, Move or Delete files, Zip and Archive files
  * Database &#8211; Import and Export data from Oracle, MS SQL and My SQL
  * Genesys &#8211; Configuration backup (hourly/daily or custom schedule), Health Check (hourly/daily or custom schedule)
  * Genesys Outbound 
      * Campaign Management &#8211; Schedule start and stop timings
      * Calling List Management &#8211; Import, Export and Purge calling list data
      * Do not call list &#8211; Import, Export and Purge calling list data

## You are invited

* * *

We are planning to officially release this product in July this year and you are invited to join the beta program of this launch.

As a early bird user, you will get full version of the software and support free of cost. We expect you to receive your feedback and suggestions every week and it may take only 15 to 30 minutes of your time.

If you are interested, please contact me by leaving a comment or email me at beta@flexicontact.com

Looking forward to work with you and hope, it will be good opportunity to network with other members as well 🙂

**Note :**

  * It will be exclusive group of members and will be limited to 5 members only
  * We will do installation, configuration and training free of cost to these members.