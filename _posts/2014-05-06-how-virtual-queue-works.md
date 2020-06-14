---
id: 1941
title: How Virtual Queue works?
date: 2014-05-06T16:57:48+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=1941
permalink: /2014/05/06/how-virtual-queue-works/
Delicacy_difficulty:
  - "1"
dsq_thread_id:
  - "2665474637"
categories:
  - Genesys
  - IRD
  - Reporting
  - Routing
tags:
  - Genesys
  - Routing
  - Tips
  - Virtual Queue
---
### What is Virtual Queue?

* * *

Virtual Queue is a logical queue where an interaction is queued if the target is not available. Virtual queues can be associated with any target type like agent, agent groups, place and place groups and commonly used for reporting purpose.

Events on virtual queues are similar to those on actual queues and URS simply uses T-Server to distribute queue events (**_EventQueued_, _EventDiverted_** and **_EventAbandoned_)** to the Stat Server for reporting purpose.

### How it works?

* * *

When an interaction is waiting for a target, URS requests T-Server to distribute an &#8216;**_EventQueued_**&#8216; for the virtual queue. For Stat Server, this means that interaction is queued for target and will start calculating stats.

When target is available and interaction is routed to target, URS requests T-Server to distribute &#8216;**_EventDiverted_**&#8216; for the virtual queue.

If the customer hangs up while waiting for the target, URS requests T-Server to distribute **_&#8216;EventAbandoned_**&#8216; for the virtual queue.

To understand it better, I developed sample routing strategy where call is simply routed to agent &#8216;agent01&#8217;. Let&#8217;s see all the above scenarios from URS and T-Server log files.

From URS logs, we can see that call with ConnID **_&#8216;006c02462a161006&#8217;_** is now entering strategy **_&#8216;VQDemo&#8217;_** and immediately targeting agents with Skill **_&#8216;Skill1&#8217;_**

\_I\_I_<span style="background-color: yellow;">006c02462a161006 </span>[14:33] strategy: <span style="background-color: yellow;">*0x65*VQDemo</span> is attached to the call

 <span style="font-family: Courier New; font-size: 8pt;">16:56:45.741 Int 20001 interaction 006c02462a161006 is started<br /> _I_I_006c02462a161006 [01:14] current call classification: media=voice(100), service=default(200), segment=default(300)<br /> 16:56:45.741_I_I_006c02462a161006 [09:06] >>>>>>>>>>>>start interpretator<br /> _I_I_006c02462a161006 [09:04] ASSIGN: __Return(SCRIPT) <- STRING:<br /> _I_I_006c02462a161006 [07:46] no error mode for this call<br /> _I_I_006c02462a161006 [09:04] ASSIGN: __Return(SCRIPT) <- STRING:<br /> _I_I_006c02462a161006 [09:04] ASSIGN: __DBReturn(SCRIPT) <- STRING:<br /> _I_I_006c02462a161006 [09:04] ASSIGN: __DBStrReturn(SCRIPT) <- STRING:<br /> _I_I_006c02462a161006 [09:04] ASSIGN: __TargetVar(SCRIPT) <- STRING:<br /> _I_I_006c02462a161006 [07:14] expression translating: Skill1 > 1 -> Skill1 > 1<br /> 16:56:45.741_I_I_006c02462a161006 [07:07] HERE IS TARGETS<br /> <span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">TARGETS: ?:Skill1 > 1@RoutingStatServer.GA</span></span>

### EventQueued message while waiting for target

* * *

URS now requests T-Server to send **&#8216;EventQueued&#8217;** message for this virtual queue as seen below

<span style="font-family: Courier New; font-size: 8pt;">request to 65200(TServer) message RequestDistributeEvent<br /> AttributeCallUUID    &#8216;AM5D3AE9D90757BKTSVJTCIAR4000014&#8217;<br /> AttributeTimeout    60<br /> AttributeExtensions    [194] 00 07 00 00..<br /> &#8216;SIGNATURE&#8217;    &#8216;router&#8217;<br /> &#8216;NAME&#8217;    &#8216;URS76&#8217;<br /> &#8216;VERSION&#8217;    &#8216;Version: 7.6.200.11&#8217;<br /> &#8216;CLUSTER&#8217;    &#8216;URS76&#8217;<br /> &#8216;VQID&#8217;    &#8216;N6NKOJMDT16I93HFG6V041D9L0000001&#8217;<br /> &#8216;Location&#8217;    &#8216;AvayaSwitch&#8217;<br /> &#8216;CallUUID&#8217;    &#8216;AM5D3AE9D90757BKTSVJTCIAR4000014&#8217;<br /> AttributeDNIS    &#8216;0800123456&#8217;<br /> AttributeOtherDNRole    1<br /> AttributeOtherDN    &#8216;20005&#8217;<br /> AttributeThisDNRole    2<br /> AttributeThisQueue    &#8216;VQ_Sales&#8217;<br /> <span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">AttributeThisDN    &#8216;VQ_Sales&#8217;</span><br /> AttributeCallType    2<br /> AttributeCallID    16<br /> AttributeConnID    006c02462a161006<br /> AttributeCustomerID    &#8216;Resources&#8217;<br /> AttributeReferenceID    4294967295<br /> <span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">AttributeUserEvent    EventQueued</span><br /> </span>

### EventDiverted Request to T-Server &#8211; When it will be sent?

* * *

When the target is available, URS requests T-Server to route to the target using **&#8216;RequestRouteCall&#8217;**. After receiving event **&#8216;EventRouteUsed&#8217;,** URS requests T-Server to send **&#8216;EventDiverted&#8217;** event as seen below

 <span style="font-family: Courier New; font-size: 8pt;"><span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">16:56:45.834_T_I_006c02462a161006 [14:0c] EventRouteUsed(normal) is received for tserver TServer[AvayaSwitch] (this dn=9001) </span><br /> _T_I_006c02462a161006 [14:0a] del DN (TServer[AvayaSwitch] 9001) truly(ref.id=12)<br /> _T_I_006c02462a161006 [14:0a] there is no DNs for call, delivering in progress<br /> request to 65200(TServer) message RequestDistributeEvent<br /> AttributeCallUUID    &#8216;AM5D3AE9D90757BKTSVJTCIAR4000014&#8217;<br /> AttributeTimeout    60<br /> AttributeExtensions    [194] 00 07 00 00..<br /> &#8216;SIGNATURE&#8217;    &#8216;router&#8217;<br /> &#8216;NAME&#8217;    &#8216;URS76&#8217;<br /> &#8216;VERSION&#8217;    &#8216;Version: 7.6.200.11&#8217;<br /> &#8216;CLUSTER&#8217;    &#8216;URS76&#8217;<br /> &#8216;VQID&#8217;    &#8216;N6NKOJMDT16I93HFG6V041D9L0000001&#8217;<br /> &#8216;Location&#8217;    &#8216;AvayaSwitch&#8217;<br /> &#8216;CallUUID&#8217;    &#8216;AM5D3AE9D90757BKTSVJTCIAR4000014&#8217;<br /> AttributeReason    [14] 00 01 01 00..<br /> &#8216;RTR&#8217;    115<br /> AttributeUserData    [598] 00 16 00 00..<br /> &#8216;RTargetAgentGroup&#8217;    &#8216;?:Skill1 > 1&#8217;<br /> &#8216;RVQID&#8217;    &#8216;N6NKOJMDT16I93HFG6V041D9L0000001&#8217;<br /> &#8216;RTargetTypeSelected&#8217;    &#8216;2&#8217;<br /> &#8216;RTargetRuleSelected&#8217;    &#8221;<br /> &#8216;RTargetObjectSelected&#8217;    &#8216;?:Skill1 > 1&#8217;<br /> &#8216;RTargetObjSelDBID&#8217;    &#8221;<br /> &#8216;RTargetAgentSelected&#8217;    &#8216;agent01&#8217;<br /> &#8216;RTargetPlaceSelected&#8217;    &#8216;Place_6001&#8217;<br /> &#8216;RTenant&#8217;    &#8216;Resources&#8217;<br /> &#8216;RStrategyName&#8217;    &#8216;VQDemo&#8217;<br /> &#8216;RStrategyDBID&#8217;    &#8216;107&#8217;<br /> &#8216;CBR-actual_volume&#8217;    &#8221;<br /> &#8216;CBR-Interaction_cost&#8217;    &#8221;<br /> &#8216;CBR-contract_DBIDs&#8217;    &#8221;<br /> &#8216;CBR-IT-path_DBIDs&#8217;    &#8221;<br /> &#8216;RRequestedSkillCombination&#8217;    &#8221;<br /> &#8216;RRequestedSkills'(list)<br /> &#8216;RTargetRequested&#8217;    &#8216;?:Skill1 > 1&#8217;<br /> &#8216;CustomerSegment&#8217;    &#8216;default&#8217;<br /> &#8216;ServiceType&#8217;    &#8216;default&#8217;<br /> &#8216;ServiceObjective&#8217;    &#8221;<br /> &#8216;PegAG?:Skill1 > 1&#8217;    1<br /> AttributeDNIS    &#8216;0800123456&#8217;<br /> AttributeThirdPartyDNRole    2<br /> AttributeThirdPartyDN    &#8216;6001&#8217;<br /> AttributeOtherDNRole    1<br /> AttributeOtherDN    &#8216;20005&#8217;<br /> AttributeThisDNRole    2<br /> AttributeThisQueue    &#8216;VQ_Sales&#8217;<br /> <span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">AttributeThisDN    &#8216;VQ_Sales&#8217;</span><br /> AttributeCallType    2<br /> AttributeCallID    16<br /> AttributeConnID    006c02462a161006<br /> AttributeCustomerID    &#8216;Resources&#8217;<br /> AttributeReferenceID    4294967295<br /> <span style="background-color: yellow; font-family: Courier New; font-size: 8pt;">AttributeUserEvent    EventDiverted</span></span>

### StatServer Calculation

* * *

Since Stat Server registers for virtual queues, it will receive event messages &#8211; EventQueued and EventDiverted &#8211; for virtual queues just like physical queues and calculates statistics accordingly.

In the next post, we will see how &#8216;Clear Target&#8217; option in Target block works for Virtual Queue

<div style="width: 455px" class="wp-caption alignnone">
  <img src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/050614_1656_HowVirtualQ1.png" alt="" width="445" height="536" />
  
  <p class="wp-caption-text">
    Target Block
  </p>
</div>