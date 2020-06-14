---
id: 331
title: How to find Datasource from Connection String?
date: 2012-03-16T11:42:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=331
permalink: /2012/03/16/how-to-find-datasource-from-connection-string/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2012/03/how-to-find-datasource-from-connection.html
  - /2012/03/how-to-find-datasource-from-connection.html
dsq_thread_id:
  - "2756184325"
  - "2756184325"
categories:
  - 'C#'
  - How to
  - Programming
  - Resources
---
Recently, I stumbled upon request to show data source property from Connection String to the end user. While, we can always split and parse the values, I was wondering about easy options for this and found &#8216;OledbConnectionStringBuilder&#8217; class (Similar class available for SQL too)

To find Connection String parameters, just use it one of its method as below

<span><em>return new OledbConnectionStringBuilder(ConnectionString).DataSource</em><em>;</em></span>

Simple and effective way to get the value..