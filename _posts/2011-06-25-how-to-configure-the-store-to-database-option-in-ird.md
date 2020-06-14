---
id: 351
title: How to configure the Store to Database option in IRD
date: 2011-06-25T16:11:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=351
permalink: /2011/06/25/how-to-configure-the-store-to-database-option-in-ird/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2011/06/how-to-configure-store-to-database.html
  - /2011/06/how-to-configure-store-to-database.html
dsq_thread_id:
  - "2789918793"
  - "2789918793"
categories:
  - Genesys
  - How to
  - IRD
  - Routing
---
Here is what to do:

1. Run Sql script against configuration Database. [ird\_create\_tables_sql](http://ctiworld.files.wordpress.com/2011/06/ird_create_tables_sql.doc)

2. Created a New DBServer Application in CME

3. Installed DB Server (As a Client of Configuration server)

4. Created New Database Access Point, which uses new DBServer

5. In IR Designer I made a connection to the Database Access Point

6. Database access Point needs to point to the Configuration Database (Or where you ran the Script)

NOTE:

You do not have to create a New DBServer, you can use the existing one.