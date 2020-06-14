---
id: 341
title: Restore Windows State from minimized to previous state
date: 2011-08-06T11:17:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=341
permalink: /2011/08/06/restore-windows-state-from-minimized-to-previous-state/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2011/08/restore-windows-state-from-minimized-to.html
dsq_thread_id:
  - "3216834861"
categories:
  - How to
  - Programming
  - Tips
---
To restore windows state from minimized to previous state, use the following

_SendMessage(docView.Handle, WM\_SYSCOMMAND, SC\_RESTORE, 0);_

 