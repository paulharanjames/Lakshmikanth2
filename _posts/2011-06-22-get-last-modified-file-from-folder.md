---
id: 371
title: Get Last Modified File from Folder
date: 2011-06-22T12:29:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=371
permalink: /2011/06/22/get-last-modified-file-from-folder/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2011/06/get-last-modified-file-from-folder.html
  - /2011/06/get-last-modified-file-from-folder.html
dsq_thread_id:
  - "2756185873"
  - "2756185873"
categories:
  - How to
  - Programming
  - VB.NET
---
Here is sample code to get last modified file from folder

<span>Dim directory As DirectoryInfo = New DirectoryInfo(&#8220;C:\Temp&#8221;)</span>  
<span>Dim filter As String = txtFileName.Text</span>

<span>If directory.GetFiles(txtFileName.Text).Count > 0 Then</span>  
<span>    Dim myFile As FileInfo = directory.GetFiles(filter).OrderByDescending(Function(f) f.LastWriteTime).First()</span>  
<span>    MsgBox(myFile.Name)</span>  
<span>Else</span>  
<span>    MsgBox(&#8220;No files found&#8221;)</span>  
<span>End If</span>

 