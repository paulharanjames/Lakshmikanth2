---
id: 6251
title: VMware Workstation shows network cable unplugged
date: 2015-12-31T14:25:44+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6251
permalink: /2015/12/31/vmware-workstation-shows-network-cable-unplugged/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "4451387460"
  - "4451387460"
categories:
  - How to
  - Troubleshooting
  - VMWare
tags:
  - Tips
  - Troubleshooting
  - VMware
---
Yesterday, I updated Windows 10 and came across &#8216;VMware workstation and Hyper-V are not compatible&#8217; issue. I had this issue previously and fixed it (Read: <a href="http://www.lakshmikanth.com/vmware-workstation-and-hyper-v-are-not-compatible/" target="_blank" rel="noopener noreferrer">http://www.lakshmikanth.com/vmware-workstation-and-hyper-v-are-not-compatible/</a> for details). Second issue is that all of my virtual machines were showing &#8216;Network Cable Unplugged&#8217; message

### Network Cable Unplugged

* * *

Luckily, it was again to easy to fix. Please find the steps below

  * Shutdown all instances of virtual machines
  * In VMware workstation, select Edit -> Virtual Network Editor
  * Click &#8216;Change Settings&#8217; button as shown below

<a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/12/VMWare-Network-Editor-1-1-1.png" rel="attachment wp-att-6271"><img class="aligncenter wp-image-6271 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/12/VMWare-Network-Editor-1-1-1.png" alt="VMWare Network Editor" width="590" height="554" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/12/VMWare-Network-Editor-1-1-1.png 590w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/12/VMWare-Network-Editor-1-1-1-300x282.png 300w" sizes="(max-width: 590px) 100vw, 590px" /></a>

  * Click &#8216;Restore Defaults&#8217; as shown below. Restart your VMware workstation and it came up good.

<a href="/wp-content/uploads/2015/12/VMWare-Network-Editor-2-1.png" rel="attachment wp-att-6281"><img class="aligncenter size-full wp-image-6281" src="/wp-content/uploads/2015/12/VMWare-Network-Editor-2-1.png" alt="Network Editor - Restore Defaults" width="590" height="526" /></a>