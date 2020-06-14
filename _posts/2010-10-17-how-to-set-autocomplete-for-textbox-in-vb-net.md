---
id: 411
title: How to set AutoComplete for Textbox in VB.net
date: 2010-10-17T09:57:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=411
permalink: /2010/10/17/how-to-set-autocomplete-for-textbox-in-vb-net/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/10/how-to-set-autocomplete-for-textbox-in.html
  - /2010/10/how-to-set-autocomplete-for-textbox-in.html
dsq_thread_id:
  - "3121791417"
  - "3121791417"
categories:
  - How to
  - Tips
  - VB.NET
---
Ever wondered how to set up auto complete for Textbox and Combo box in VB.net.  In Windows Form 2.0 and higher, some of the controls support this feature including the combo box and textbox controls. By using these feature, we can easily build auto completion functionality and here is the sample code for text box control

 

> _Dim Companies As AutoCompleteStringCollection  
> Companies = New AutoCompleteStringCollection  
> Companies.Add(“Ferrari”)_
> 
> _Companies.Add(“Ferrari2”)  
> txtAuto.AutoCompleteMode = AutoCompleteMode.Suggest  
> txtAuto.AutoCompleteSource = AutoCompleteSource.CustomSource  
> txtAuto.AutoCompleteCustomSource = Companies_

Simple and very useful end user experience…