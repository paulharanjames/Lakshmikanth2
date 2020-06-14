---
id: 571
title: 'Agent Callback Error: Agent moved to another campaign'
date: 2009-10-26T21:16:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=571
permalink: /2009/10/26/agent-callback-error-agent-moved-to-another-campaign/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/10/agent-callback-error-agent-moved-to.html
  - /2009/10/agent-callback-error-agent-moved-to.html
dsq_thread_id:
  - "2703883718"
  - "2703883718"
categories:
  - Callback
  - Dialer (OCS)
  - Genesys
  - Genesys outbound
  - How to
  - OCS
---
What happens if the agent has personal callback in Campaign A and moved to campaign B…? Interesting question from the customer..

Tested and found that OCS fails with Agent Callback error in this scenario 🙁 What can we do now?

Fortunately, got workaround solution using treatments..

  * Configured treatment for Agent Callback error and assigned to Group

My customer is happy with this work around solution..if you have any other solution, let us know..