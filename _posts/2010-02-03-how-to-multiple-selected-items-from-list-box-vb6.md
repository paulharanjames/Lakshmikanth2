---
id: 561
title: How to multiple selected items from List Box (VB6)?
date: 2010-02-03T21:50:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=561
permalink: /2010/02/03/how-to-multiple-selected-items-from-list-box-vb6/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/02/how-to-multiple-selected-items-from.html
  - /2010/02/how-to-multiple-selected-items-from.html
dsq_thread_id:
  - "3180768995"
  - "3180768995"
categories:
  - How to
  - Programming
  - Resources
  - VB6
  - Visual Basic 6
---
Ever wondered how to remove multiple selected items from list box in VB6? Trick here is loop through listbox in REVERSE.

Here is the sample and enjoy 🙂

_Dim intCount As Integer_

_For intCount = (lstSample.ListCount -1 1) To 0 Step -1_

> _If lstSample.Selected(intCount) Then_

> _lstSample.RemoveItem intCount_

_End If_

_Next_