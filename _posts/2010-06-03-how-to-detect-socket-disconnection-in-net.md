---
id: 521
title: How to detect socket disconnection in .NET?
date: 2010-06-03T15:35:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=521
permalink: /2010/06/03/how-to-detect-socket-disconnection-in-net/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/06/how-to-detect-socket-disconnection-in.html
  - /2010/06/how-to-detect-socket-disconnection-in.html
dsq_thread_id:
  - "3332715354"
  - "3332715354"
categories:
  - How to
  - Programming
  - Sockets
  - VB.NET
---
After spending few days, finally able to figure socket disconnect detection in .NET 🙂 

 

Public Shared Function IsConnected(ByVal socket As Socket) As Boolean  
        Try  
            Return Not (socket.Poll(1, SelectMode.SelectRead) AndAlso socket.Available = 0)  
        Catch generatedExceptionName As SocketException  
            Return False  
        End Try  
End Function

In Timer_tick event, keep checking for connection status.  If return value is ‘false’, we can say that socket is disconnected now 🙂