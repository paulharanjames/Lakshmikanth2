---
id: 911
title: How to open the second interaction automatically?
date: 2009-01-19T18:59:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=911
permalink: /2009/01/19/how-to-open-the-second-interaction-automatically/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/01/how-to-open-second-interaction.html
  - /2009/01/how-to-open-second-interaction.html
dsq_thread_id:
  - "2923108745"
  - "2923108745"
categories:
  - GAD
  - Genesys
  - Screen pop
---
An interesting problem & solution again..

In Genesys Outbound Dialer solution, if the agent is doing post call work in GAD and receives new outbound interaction, they are not getting any screen POP. Agent has to manually click the phone button to get the customer details.. Very annoying..isn’t it?

After reading lot of documents and trying to modify JSP files, I found that the solution is available already and is available in Genesys 7.5 Release notes.

From Genesys GAD 7.5 release notes

_A new `auto-open` configuration option has been added to the appropriate section of every supported media type (voice, e-mail, chat, and open-media). The default values are `false`. If the option is set to `true`, a ringing interaction is opened automatically (without the agent clicking on the batch icon). This enables the agent to preview the interaction before deciding to accept it (Note: all action buttons will be unavailable). The agent must click the ringing batch icon to accept the interaction (ER# 80592)_