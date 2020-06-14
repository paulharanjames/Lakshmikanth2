---
id: 6101
title: VMware Workstation and Hyper-V are not compatible
date: 2015-12-17T12:34:15+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6101
permalink: /2015/12/17/vmware-workstation-and-hyper-v-are-not-compatible/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "4411564411"
  - "4411564411"
categories:
  - How to
  - Troubleshooting
  - VMWare
tags:
  - Compatability
  - Hyper-V
  - Troubleshooting
  - VMware
---
After I upgraded my workstation to Windows 10,  I am no longer able to power on guest OS on VMware operating system and received error as below

_&#8216;VMware Workstation and Hyper-V are not compatible. Remove the Hyper-V role from the system before running VMware Workstation&#8217;_

After some searching, I found that it is caused by _**&#8216;hypervisorlaunchtype&#8217;**_ on windows loader is set to &#8216;Auto&#8217;.

## Disable Hyper-V

* * *

To disable Hyper-V role, follow the steps below

  *  Open &#8216;cmd&#8217; prompt with elevated privileges i.e.) with Administrator access
  * To disable Hyper-V, run following command

<pre class="lang:default decode:true" title="Disable Hyper-V">bcdedit /set hypervisorlaunchtype off</pre>

  * Restart computer

## Enable Hyper-V

* * *

To enable Hyper-V, follow the steps below

  *  Open &#8216;cmd&#8217; prompt with elevated privileges i.e.) with Administrator access
  * To disable Hyper-V, run following command

<pre class="lang:default decode:true " title="Enable Hyper-V">bcdedit /set hypervisorlaunchtype auto</pre>

  * Restart computer

## References

* * *

  * BCDEdit &#8211; <a href="https://msdn.microsoft.com/en-us/library/windows/hardware/ff542202%28v=vs.85%29.aspx" target="_blank" rel="noopener noreferrer">https://msdn.microsoft.com/en-us/library/windows/hardware/ff542202%28v=vs.85%29.aspx</a>
  * BCDEdit FAQ&#8217;s &#8211; <a href="https://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx" target="_blank" rel="noopener noreferrer">https://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx</a>
  * BCDEdit command line options &#8211; <a href="https://technet.microsoft.com/en-GB/library/cc709667%28v=ws.10%29.aspx" target="_blank" rel="noopener noreferrer">https://technet.microsoft.com/en-GB/library/cc709667%28v=ws.10%29.aspx</a>
  * To run Hyper-V and VMware on same machine &#8211; <a href="https://jorgequestforknowledge.wordpress.com/2012/05/26/using-both-microsoft-hyper-v-and-vmware-workstation-on-the-same-machine/" target="_blank" rel="noopener noreferrer">https://jorgequestforknowledge.wordpress.com/2012/05/26/using-both-microsoft-hyper-v-and-vmware-workstation-on-the-same-machine/</a>