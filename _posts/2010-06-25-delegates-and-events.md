---
id: 491
title: Delegates and Events
date: 2010-06-25T09:29:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=491
permalink: /2010/06/25/delegates-and-events/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2010/06/delegates-and-events.html
dsq_thread_id:
  - "2863925469"
categories:
  - How to
  - Programming
  - Tips
  - VB.NET
---
Oh…spent lot of time trying to pass values between Parent and Child forms. It is much needed for my SoftPhone application to keep track of call states across windows. Finally, I was able to achieve it using delegates and events (interesting concepts, though)

**To pass value from Parent (Form1) to Child Form (Form2)**

Step 1: Create delegate for function 

_Public Delegate Sub PassData(ByVal Message As String)_

Step 2: Create Object for deleage

_Public frm2PassData As PassData_

Step 3: Create public procedure in child form with same signature as delegate 

_Public Sub GetData(ByVal Message As String)  
    TextBox1.Text = Message  
End Sub_

Step 4: Link Delegate with frm2 function 

_frm = New Form2  
frm2PassData = New PassData(AddressOf frm.GetData)_

_frm.show_

 

Step 5: To pass data from Parent Form to child form, just call delegate object as below

_if frm2passdata isnot nothing then_ 

_frm2passdata(“Hello”)_

_end if_</p> 

**To pass value from Child Form to Parent Form (use Events)**

Step 1: Declare Public event in Child Form 

Public Event Notification(ByVal Message As String)

Step 2: RaiseEvent in Child form, as applicable

Private Sub TextBox1_TextChanged(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles TextBox1.TextChanged  
     RaiseEvent Notification(TextBox1.Text)  
End Sub

Step 3: Create procedure in Parent form with same signature as Event

Public Sub Getdata(ByVal Message As String)  
     Me.Text = Message  
End Sub

Step 4: Add event handler for child form

AddHandler frm.Notification, AddressOf Getdata

Done..easy isn’t it?

_ _