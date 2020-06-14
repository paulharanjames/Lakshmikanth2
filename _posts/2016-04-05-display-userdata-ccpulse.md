---
id: 6621
title: 'Genesys CCPulse &#8211; Display UserData using Custom Stat and Filters'
date: 2016-04-05T16:03:53+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6621
permalink: /2016/04/05/display-userdata-ccpulse/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "4722378810"
  - "4722378810"
categories:
  - CCPulse
  - Genesys
tags:
  - CCPulse
  - Custom Statistic
  - Formula
  - Genesys
---
Previously, I wrote post about <a href="http://www.lakshmikanth.com/genesys-ccpulse-show-user-data/" target="_blank" rel="noopener noreferrer">displaying user data in CCPulse using custom solution</a> and user &#8216;<span class="post-byline"><span class="author publisher-anchor-color"><a href="https://disqus.com/by/moshelezerovitz/" data-action="profile" data-username="moshelezerovitz" data-role="username">Moshe Lezerovitz</a></span></span>&#8216; enquired about displaying user data using CCPulse application only.

I found two options to display user data in CCPulse

### Option 1: Display User Data using Custom Stat

* * *

**Step 1:** Configure Custom Statistic as below

<span id="j_id0:j_id8"><span id="j_id0:j_id8:j_id9:j_id253:j_id255:0:j_id256:j_id257">[CustomUserData]<br /> Category = CurrentCustomValue<br /> Formula = GetGlobalNumber(&#8220;Account&#8221;,-1)&#8221;<br /> MainMask = *<br /> Objects = Agent, Place, GroupAgents, GroupPlaces<br /> Subject = DNAction</span></span>

In CCPulse, configure template to display this custom statistic. Please note that this will work only if key value is numeric. To display string value, use option 2 below

### Option 2: Display User Data using Filters

* * *

You need CCPulse 8.0.101.27 or higher to display user data using filters.<span id="j_id0:j_id8"><span id="j_id0:j_id8:j_id9:j_id253:j_id255:6:j_id256:j_id257"><span id="j_id0:j_id1:j_id3:j_id5:j_id12:j_id14"> Please find the CCPulse release notes below<br /> </span></span></span>

_<span id="j_id0:j_id8"><span id="j_id0:j_id8:j_id9:j_id253:j_id255:6:j_id256:j_id257"><span id="j_id0:j_id1:j_id3:j_id5:j_id12:j_id14">CCPulse+ now displays by default only hardware or software reason codes, without User Data. A new CCPulse+ option, ReasonCodeData, in the [CustomStatistic] section enables you to control which values are displayed.</span></span></span>_

**ReasonCodeData**

Valid Values: Hardware; Software; Userdata  
Separate with semicolons the values to be displayed. Enter all three values if you use User Data values with reason codes in Formulas or to display them in the Extended Status window or in a view.

_[CustomStatistic]_  
 _ReasonCodeData=Userdata (optional values: Hardware; Software)_

Previously, starting with release 8.0.000.41, CCPulse+ appended some values from User Data to the reason codes. (ER# 317914454)

To display user data **&#8216;Account&#8217;,** follow steps below

**Step 1:** Create Filter &#8216;Account = PairExist(&#8220;Account&#8221;, &#8220;*&#8221;) under [Filters] section in Stat Server

**Step 2:** Create statistical type [CustomAgentState] in Stat Server as below

_[CustomAgentState]_

_<span id="j_id0:j_id8"><span id="j_id0:j_id8:j_id9:j_id253:j_id255:5:j_id256:j_id257">Category=CurrentState<br /> MainMask=*<br /> Objects=Agent<br /> Subject=DNAction</span></span>_

Step 3: Set CCPulse application options, set &#8216;ExtendedCurrentStatus&#8217; to &#8216;true under [CustomStatistic]

Step 4: Add below formula to display

<pre class="lang:js decode:true" title="Formula">result.Text = state.type == "AgentState" ? GetUserData() : "";
function GetUserData()
{
var data = "";
for(var e = new Enumerator(state.CallData.Filter("Key=Account")); !e.atEnd(); e.moveNext())
  { if (e.item().Key=='Account')
      data = e.item().Value;
   }
   return data;
}</pre>

<span id="j_id0:j_id8"><span id="j_id0:j_id8:j_id9:j_id253:j_id255:5:j_id256:j_id257"> </span></span>