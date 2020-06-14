---
id: 871
title: Test Post
date: 2009-02-01T19:04:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=871
permalink: /?p=871
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /feeds/7723976789736156511/posts/default/5035773368469313162
categories:
  - Uncategorized
---
In last week, I received nearly 10 queries from users to configure SCS to use SMTP to send emails. It is very simple and straight-forward configuration and requires restart of SCS Open or Create ‘mailer’ section in SCS and configure the following values \* smtp\_host: host name of the SMTP Server \* smpt\_port: port number of the SMTP Server * smtp\_from: From email address Any changes to smtp\_host and smtp\_port requires SCS restart for changes to take effect. Changes to smtp\_from effects immediately and no restart required.