---
id: 2041
title: Virtual Queues and Clear Target Option
date: 2014-05-13T10:41:45+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2041
permalink: /2014/05/13/virtual-queues-and-clear-target-option/
dsq_thread_id:
  - "2681627595"
  - "2681627595"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
  - Reporting
  - Routing
  - Universal Routing
tags:
  - Genesys
  - How to
  - Reporting
  - Routing
  - Tips
  - Virtual Queue
---
In this post, we will see what clear target option is and how it impacts call routing and reporting.

**What is Clear target?  
** 

Clear target sets whether the targets are retained after the interaction moves on through the strategy and encounters other selection objects. If &#8216;Clear Target&#8217; is not selected, targets in this selection object are added to those of the next selection object.

For example, in the strategy below first selection object waits for &#8216;Sales&#8217; agent group for 5 seconds and moves on to &#8216;General&#8217; agent group for 300 seconds.

[<img class="aligncenter wp-image-2031 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/051314_1041_VirtualQueu1.png" alt="051314_1041_VirtualQueu1.png" width="793" height="493" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/051314_1041_VirtualQueu1.png 793w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/051314_1041_VirtualQueu1-300x187.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/051314_1041_VirtualQueu1-768x477.png 768w" sizes="(max-width: 793px) 100vw, 793px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/05/051314_1041_VirtualQueu1.png)

  * Agent Group &#8216;Sales&#8217; contains following agents – sales1, sales2, sales3 and uses virtual queue **&#8216;VQ_Sales&#8217;**
  * Agent Group &#8216;General&#8217; contains following agents &#8211; agent1, agent2, agent3 and uses virtual queue **&#8216;VQ_General&#8217;**

### Scenario 1: Clear Target is checked

In this case, if &#8216;Sales&#8217; agents are not available, strategy will move on to next selection object and target &#8216;General&#8217; agent group only.

Routing Target is now only following agents

  * agent1
  * agent2
  * agent3

After it is moved on, calls will not be routed to &#8216;Sales&#8217; agent even if they become available. In some cases, it is useful as calls are overflowing to &#8216;General&#8217; agent group as &#8216;Sales&#8217; agents are busy and they need breathing space.

### Scenario 2: Clear Target is unchecked

In this case, if &#8216;Sales&#8217; agents are not available, strategy will move on next selection object and <span style="text-decoration: underline;">adds &#8216;General&#8217; agent group in the existing target list.<br /> </span>

Routing target is now &#8216;Sales&#8217; + &#8216;General&#8217; agent group as below

  * sales1
  * sales2
  * sales3
  * agent1
  * agent2
  * agent3

This is useful when you want best skilled agent to handle customer calls but don&#8217;t want your customer to wait forever.

Now, we understand how clear target works, we will see how it impacts reporting.

### How it impacts reporting?

In my previous post, we saw how virtual queues work? and how events are distributed. When calls enters virtual queue, it can follow any of the options below

  * Diverted – Call routed to target (agent) successfully
  * Abandoned – Customer hang up call
  * Cleared – Call is cleared from this virtual queue. If the interaction leaves virtual queue with **_EventDiverted_** with the call state redirected (**_AttributeCallState = 22_**), it is considered as cleared.

Simply,

<div>
  <table style="border-collapse: collapse;" border="0">
    <colgroup> <col style="width: 436px;" /></colgroup> <tr style="height: 28px;">
      <td style="padding-left: 0px; padding-right: 0px; border: solid 1pt;">
        <strong>       Calls Entered</strong> = <strong>Diverted + Abandoned + Cleared<br /> </strong>
      </td>
    </tr>
  </table>
</div>

Let&#8217;s go through some call flow scenarios from reporting perspective

### Scenario 1: Clear Target is checked, Sales agent are available and call routed to Sales agent

In this case, reports are calculated as below

[table id=2 /]

### Scenario 2: Clear Target is checked, Sales agent are unavailable and after 5 seconds – timeout expires for first selection object, call routed to General agent

In this case, reports are calculated as below

[table id=3 /]

### Scenario 3: Clear Target is unchecked, Sales agent are unavailable, after 5 seconds, call queued for both queues and routed to General agent

In this case, reports are calculated as below

[table id=3 /]

### Scenario 4: Clear Target is checked, both Sales and General agents are unavailable after 5 seconds – timeout expires for first selection object, call queued for both agent groups and call routed to &#8216;Sales&#8217; agent

In this case, reports are calculated as below

[table id=4/]