---
id: 431
title: How to register Hot Keys in VB.net
date: 2010-08-19T12:41:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=431
permalink: /2010/08/19/how-to-register-hot-keys-in-vb-net/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2010/08/how-to-register-hot-keys-in-vbnet.html
dsq_thread_id:
  - "3345408760"
categories:
  - Programming
  - Tips
  - VB.NET
---
**Code sample: Register multiple hotkeys such as Alt+D, Alt+C, etc.**

<pre>Imports System.Runtime.InteropServices<br /><br />Public Class Form1<br /><br />    Public Const MOD_ALT As Integer = &H1 'Alt key<br />    Public Const WM_HOTKEY As Integer = &H312<br /><br />    &lt;DllImport("User32.dll")> _<br />    Public Shared Function RegisterHotKey(ByVal hwnd As IntPtr, _<br />                        ByVal id As Integer, ByVal fsModifiers As Integer, _<br />                        ByVal vk As Integer) As Integer<br />    End Function<br /><br />    &lt;DllImport("User32.dll")> _<br />    Public Shared Function UnregisterHotKey(ByVal hwnd As IntPtr, _<br />                        ByVal id As Integer) As Integer<br />    End Function<br /><br />    Private Sub Form1_Load(ByVal sender As System.Object, _<br />                        ByVal e As System.EventArgs) Handles MyBase.Load<br />        RegisterHotKey(Me.Handle, 100, MOD_ALT, Keys.D)<br />        RegisterHotKey(Me.Handle, 200, MOD_ALT, Keys.C)<br />    End Sub<br /><br />    Protected Overrides Sub WndProc(ByRef m As System.Windows.Forms.Message)<br />        If m.Msg = WM_HOTKEY Then<br />            Dim id As IntPtr = m.WParam<br />            Select Case (id.ToString)<br />                Case "100"<br />                    MessageBox.Show("You pressed ALT+D key combination")<br />                Case "200"<br />                    MessageBox.Show("You pressed ALT+C key combination")<br />            End Select<br />        End If<br />        MyBase.WndProc(m)<br />    End Sub<br /><br />    Private Sub Form1_FormClosing(ByVal sender As System.Object, _<br />                        ByVal e As System.Windows.Forms.FormClosingEventArgs) _<br />                        Handles MyBase.FormClosing<br />        UnregisterHotKey(Me.Handle, 100)<br />        UnregisterHotKey(Me.Handle, 200)<br />    End Sub<br /><br />End Class</pre>