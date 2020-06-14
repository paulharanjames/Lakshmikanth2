---
id: 971
title: Predictive outbound in Genesys(Avaya pbx)
date: 2008-10-31T12:31:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=971
permalink: /2008/10/31/predictive-outbound-in-genesysavaya-pbx/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2008/10/predictive-outbound-in-genesysavaya-pbx.html
dsq_thread_id:
  - "2724521007"
categories:
  - Avaya
  - Genesys
  - genesys avaya outbound
  - Genesys outbound
  - How to
  - OCM
  - Predictive dialing
  - VDN
---
<span><strong>Intended Audience:</strong></span> If you want to configure outbound in predictive mode in Genesys CTI and Avaya pbx.

<span><strong>Prerequisites</strong></span>: Genesys framework and Outbound solution (OCS and OCM)

Before beginning the work, ensure that your Avaya pbx has Call classifier card configured with enough number of call classifier ports.

Predictive dialing needs Vector Destination Numbers (VDNs) to be configured both in the switch and Genesys CME.

You can verify with Avaya personnel to create a VDN on the switch.Make a note of the VDN created. Now create and configure the same VDN on CME. VDN in CME is  a DN of type **route point** with **switch-specific type** as **2**. Done ? now you can consider as half way through!

Make sure from the Avaya personnel that the VDN has Class of Restriction (COR) configured to allow outbound dialing. You can test the same by making a call from that VDN manually.

Now we will go to the routing part. In IRD, create a simple strategy to route the calls to an agent group. Load the strategy on to the VDN.

Now create a calling list with outbound numbers. Logon your agents. Start your OCM and run the campaign. In IRD&#8217;s monitoring view of the strategy,[polldaddy poll=1061554] see if the calls are routed.

Can you see the call in agent desktop?. Cheers! 🙂

NO ? Post your error code in this blog and Lakshmi is there to help you :))