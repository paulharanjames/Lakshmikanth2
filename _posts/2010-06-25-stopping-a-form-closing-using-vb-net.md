---
id: 481
title: Stopping a form closing using vb.net
date: 2010-06-25T16:33:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=481
permalink: /2010/06/25/stopping-a-form-closing-using-vb-net/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/06/stopping-form-closing-using-vbnet.html
  - /2010/06/stopping-form-closing-using-vbnet.html
dsq_thread_id:
  - "3216842142"
  - "3216842142"
categories:
  - How to
  - Programming
  - Resources
  - Tips
  - VB.NET
---
Quick and useful tip..

 

Private Sub MyForm\_Closing(ByVal sender As System.Object, ByVal e As \_  
            System.ComponentModel.CancelEventArgs) Handles MyBase.Closing  
Try  
   Select Case MessageBox.Show(&#8220;Are you sure you want to close this window?&#8221;, _  
      &#8220;Your application&#8221;, MessageBoxButtons.YesNo, MessageBoxIcon.Question)  
    Case MsgBoxResult.Yes  
     &#8216;Do Nothing  
    Case MsgBoxResult.No  
     e.Cancel = True  
   End Select  
Catch ee As Exception  
  Throw ee  
End Try  
End Sub