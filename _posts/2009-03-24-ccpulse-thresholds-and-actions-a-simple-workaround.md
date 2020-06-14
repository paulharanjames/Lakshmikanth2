---
id: 741
title: 'CCpulse Thresholds and Actions &#8211; A simple workaround.'
date: 2009-03-24T08:54:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=741
permalink: /2009/03/24/ccpulse-thresholds-and-actions-a-simple-workaround/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/03/ccpulse-thresholds-and-actions-simple.html
  - /2009/03/ccpulse-thresholds-and-actions-simple.html
dsq_thread_id:
  - "2720371893"
  - "2720371893"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - CCPulse
  - color change ccpulse
  - Genesys
  - How to
  - Reporting
  - threshold
---
CCPulse is not as boring as CCplus you know? (Now C++ guys plz dont curse me 🙁 ) Its worth playing around&#8230; We will look at a small example which uses thresholds and actions..

**The requirement is:**  
CCPulse has a view which shows State of the agent. When agent in on state &#8216;Call inbound&#8217; for:  
0-24 seconds = The state &#8216;callinbound&#8217; should be in normal colour  
25-85 seconds = Yellow Colour  
85 and above = Red colour

**Solution:**  
To begin with, go to threshold wizard (asking me where is it? Goto tools menu) and on the object type side, select &#8216;Agent&#8217;. Then select Newscript and click next. Give the name for the threshold say Yellow. In the Threshold script box, type the condition required:

_**if Threshold.Statvalue >= 25 and Threshold.Statvalue <= 84 then  
Threshold.Result = true  
End If**_

Test and finish. (If you dont test you may not get the finish button.. so dont break your head with the disabled button 🙂 ) .  
Now its time to get into action.. I mean action wizard. Create a new action script say yellow and in the &#8216;Action Script&#8217; type as:

**_CCPulseNotifier.SetColor(Color.Yellow)_**

Now repeat the same for Red script except that the condition and color in action should differ:

_**if Threshold.Statvalue > 85 then  
Threshold.Result = true  
End IF**_  
For the &#8216;Red&#8217; action:  
**_CCPulseNotifier.SetColor(Color.Red)_**

Now go to the CCpulse view and right-click on the statistic &#8216;CallInbound&#8217;, select &#8216;set threshold&#8217;. Apply Yellow threshold and yellow action and similar for Red. Drop a inbound call on the agent and watch the statistic. It should change the colour like a chameleon 🙂 .

Cheers!!  
Gururaj S