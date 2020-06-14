---
id: 501
title: 'Iterating through a Dictionary Object&#8217;s Items in VB.NET'
date: 2010-06-24T14:41:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=501
permalink: /2010/06/24/iterating-through-a-dictionary-objects-items-in-vb-net/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/06/iterating-through-dictionary-object.html
  - /2010/06/iterating-through-dictionary-object.html
dsq_thread_id:
  - "3216842209"
  - "3216842209"
categories:
  - How to
  - Programming
  - Resources
  - VB.NET
---
Good example for iterating through dictionary object…

> Dim DictObj As New Dictionary(Of Integer, String)  
> 
> DictObj.Add(1, &#8220;ABC&#8221;)  
> 
> DictObj.Add(2, &#8220;DEF&#8221;)  
> 
> DictObj.Add(3, &#8220;GHI&#8221;)  
> 
> DictObj.Add(4, &#8220;JKL&#8221;)  
> 
> For Each kvp As KeyValuePair(Of Integer, String) In DictObj  
> 
> Dim v1 As Integer = kvp.Key  
> 
> Dim v2 As String = kvp.Value  
> 
>      Debug.WriteLine(&#8220;Key: &#8221; + v1.ToString _  
> 
>             + &#8221; Value: &#8221; + v2)  
> 
> Next

For more information, please refer to [http://msdn.microsoft.com/en-us/library/xfhwa508.aspx](http://msdn.microsoft.com/en-us/library/xfhwa508.aspx "http://msdn.microsoft.com/en-us/library/xfhwa508.aspx")