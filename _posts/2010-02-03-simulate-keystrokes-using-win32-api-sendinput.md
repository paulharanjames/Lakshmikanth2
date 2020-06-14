---
id: 551
title: Simulate Keystrokes using Win32 API (SendInput)?
date: 2010-02-03T21:59:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=551
permalink: /2010/02/03/simulate-keystrokes-using-win32-api-sendinput/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/02/simulate-keystrokes-using-win32-api.html
  - /2010/02/simulate-keystrokes-using-win32-api.html
dsq_thread_id:
  - "3059868919"
  - "3059868919"
categories:
  - How to
  - Programming
  - Resources
  - VB6
  - Visual Basic 6
---
Recently, I was modifying the old softphone source code (written in VB6) and encountered error using ‘SendKeys’ function. Sometimes, it sends multiple keystrokes for the same char resulting in application errors. Thought of using WinAPI’s to simulate keystrokes and got this one..works really well…

 

_Const KEYEVENTF_KEYUP = &H2  
Const INPUT_MOUSE = 0  
Const INPUT_KEYBOARD = 1  
Const INPUT_HARDWARE = 2  
Private Type MOUSEINPUT  
    dx As Long  
    dy As Long  
    mouseData As Long  
    dwFlags As Long  
    time As Long  
    dwExtraInfo As Long  
End Type  
Private Type KEYBDINPUT  
    wVk As Integer  
    wScan As Integer  
    dwFlags As Long  
    time As Long  
    dwExtraInfo As Long  
End Type_ 

_Private Type HARDWAREINPUT  
    uMsg As Long  
    wParamL As Integer  
    wParamH As Integer  
End Type_ 

_Private Type GENERALINPUT  
    dwType As Long  
    xi(0 To 23) As Byte  
End Type_ 

_Private Declare Function SendInput Lib &#8220;user32.dll&#8221; (ByVal nInputs As Long, pInputs As GENERALINPUT, ByVal cbSize As Long) As Long  
Private Declare Sub CopyMemory Lib &#8220;kernel32&#8221; Alias &#8220;RtlMoveMemory&#8221; (pDst As Any, pSrc As Any, ByVal ByteLen As Long)_

__

_Private Sub SendKey(bKey As Byte)_ 

_Dim GInput(0 To 1) As GENERALINPUT  
Dim KInput As KEYBDINPUT  
      _ 

_       KInput.wVk = bKey_ _&#8216;the key we&#8217;re going to press  
       KInput.dwFlags = 0 &#8216;press the key_ 

_       &#8216;copy the structure into the input array &#8216;s buffer.  
       GInput(0).dwType = INPUT_KEYBOARD &#8216; keyboard input  
       CopyMemory GInput(0).xi(0), KInput, Len(KInput)_ 

_&#8216;do the same as above, but for releasing &#8216; the key_ 

_        KInput.wVk = bKey &#8216; the key we&#8217;re going to realease  
        KInput.dwFlags = KEYEVENTF_KEYUP &#8216; release the key  
        GInput(1).dwType = INPUT_KEYBOARD_ _&#8216; keyboard input  
       CopyMemory GInput(1).xi(0), KInput, Len(KInput)  
       _ _&#8216;send the input now  
        Call SendInput(2, GInput(0), Len(GInput(0)))  
End Sub_

To simulate “H” Keystroke, just call **SendKey(CByte(asc(“H”))**