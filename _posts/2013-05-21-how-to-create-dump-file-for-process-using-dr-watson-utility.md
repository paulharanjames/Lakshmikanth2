---
id: 211
title: How to create dump file for process using Dr.Watson utility?
date: 2013-05-21T13:14:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=211
permalink: /2013/05/21/how-to-create-dump-file-for-process-using-dr-watson-utility/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2013/05/how-to-create-dump-file-for-process.html
  - /2013/05/how-to-create-dump-file-for-process.html
dsq_thread_id:
  - "3132509083"
  - "3132509083"
categories:
  - Uncategorized
---
 

This article describes how to create dump file for process using dr.watson utility



  * Verify the PID of the service or process from Task Manager.
  * Click the **Processes** tab.

[<img title="SNAGHTMLc88ad5" border="0" alt="SNAGHTMLc88ad5" src="http://lh5.ggpht.com/-H_Qg0U6LqjY/UZtzEieHovI/AAAAAAAAADM/pNQFC4ytR0I/SNAGHTMLc88ad5_thumb%25255B1%25255D.png?imgmax=800" width="381" height="416" />](http://lh3.ggpht.com/-5kE7w_tgPKg/UZtzDElX6FI/AAAAAAAAADI/UGUiB0v9kXo/s1600-h/SNAGHTMLc88ad5%25255B4%25255D.png)



  * If you do not have a PID column, click **View**, click **Select Columns**, and then click to select the PID (Process Identifier) check box.
  * [<img title="SNAGHTMLc5d8a6[4]" border="0" alt="SNAGHTMLc5d8a6[4]" src="http://lh3.ggpht.com/-YFpvMOh6YQU/UZtzGkgtIcI/AAAAAAAAADg/ouEC9mGAKxU/SNAGHTMLc5d8a6%25255B4%25255D_thumb%25255B1%25255D.png?imgmax=800" width="330" height="335" />](http://lh4.ggpht.com/-1fGEeFSFKrE/UZtzFXNfdAI/AAAAAAAAADY/F6o8tRzts4I/s1600-h/SNAGHTMLc5d8a6%25255B4%25255D%25255B3%25255D.png)
  * At the Run Command, run the following command **  
    drwtsn32**
  * Set the **Crash Dump Type** to **Full** and click **OK**.
  * From the command prompt execute the following command: **  
    drwtsn32 -p XXXX**  
    (XXXX is replaced with the PID for that process or service).  
    This captures a dump and terminate the process or service.
  * You might need to manually restart the process or service that was dumped.

By default the dump file created by Dr. Watson is named user.dmp and is saved in the following location: drive:\Documents and Settings\Administrator\Local Settings\Application Data\Microsoft\Dr Watson