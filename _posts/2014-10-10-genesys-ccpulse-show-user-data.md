---
id: 4401
title: 'Genesys CCPulse &#8211; Show User Data'
date: 2014-10-10T12:05:12+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4401
permalink: /2014/10/10/genesys-ccpulse-show-user-data/
dsq_thread_id:
  - "3102975959"
  - "3102975959"
Delicacy_difficulty:
  - "1"
  - "1"
categories:
  - Genesys
tags:
  - CCPulse
  - Genesys
  - Reporting
---
In my recent posts, I talked about Genesys CCPulse and its powerful feature (<a title="CCPulse – Very powerful but less popular feature" href="http://www.lakshmikanth.com/most-powerful-and-less-popular-feature-in-ccpulse/" target="_blank" rel="noopener noreferrer">here</a>, <a title="Genesys CCPulse – How to show when agent logged in?" href="http://www.lakshmikanth.com/genesys-ccpulse-logged-in/" target="_blank" rel="noopener noreferrer">here</a> and <a title="Genesys CCPulse – access skill details securely" href="http://www.lakshmikanth.com/genesys-ccpulse-access-skill-details-securely/" target="_blank" rel="noopener noreferrer">here</a>). Continuing the series, I try to answer one of the most wanted feature in CCPulse.

**_&#8220;Is it possible to show user data in CCPulse?&#8221;_**

### User data in CCPulse &#8211; Why?

* * *

Using CCPulse, Supervisors/Team leaders have visibility call related metrics like talk time, number of calls handled etc only and customer related details like category etc are available only to agent. By having user data in CCPulse, Supervisors can have more information about caller &#8211; just like agent &#8211; and make decisions.

Some use case scenarios are

  * Team leader can get visual or email notifications if agent talk time is higher than normal for high profile customers. This helps them to coach or supervise agents in real time.
  * Team leader want to view ANI, DNIS and Queue of the call each agent is handling to. I found this useful to have it in CCPulse if the calls are overflowing from one group/site to another and manage operations accordingly.

### Possible or not?

* * *

<p style="text-align: left;">
  <strong><em>Can I show user data in CCPulse using out of box templates and solution?</em></strong>
</p>

It is not available in out of box templates and solution.

**_Is it possible to show user data in CCPulse?_**

<span style="color: #003300;">&#8216;</span><span style="color: #008000;"><strong><span style="color: #003300;">YES&#8217;.</span> </strong><span style="color: #000000;">It is possible to show user data in CCPulse using custom solution.</span></span>

### Solution

* * *

For this, you need server application to send Call data to CCPulse. In my previous post to access skill data securely, I developed application to communicate with Configuration Server and extended it to communicate with T-Server and provide user data for the call. Yo can find high level call flow and script used in CCPulse in my [previous post.](http://www.lakshmikanth.com/genesys-ccpulse-access-skill-details-securely/ "Genesys CCPulse – access skill details securely")

Here is the video showing call data in CCPulse



&nbsp;