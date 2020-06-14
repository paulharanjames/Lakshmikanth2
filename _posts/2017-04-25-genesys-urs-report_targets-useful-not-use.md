---
id: 6984
title: 'Genesys URS report_targets : Why is it useful but should not use it?'
date: 2017-04-25T16:28:50+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6984
permalink: /2017/04/25/genesys-urs-report_targets-useful-not-use/
Delicacy_difficulty:
  - "1"
dsq_thread_id:
  - "5758673020"
categories:
  - Genesys
  - How to
  - Tips
tags:
  - Genesys
  - How to
  - Tips
---
In some cases, we want to understand the routing decision by URS, especially if an interaction is queued for multiple targets like agent groups. In this post, you will learn about &#8216;report_targets&#8217; option, how it works and recommended way to use it in production environment.

From version 7.x onwards,  Genesys URS expose routing decision using key value pairs.  If enabled, URS will attach following informatio for each interaction

  *  Routing Rule, Target Group (Agent Group or Place Group), Skill Expression while waiting and after the call is routed to
  * Agent
  * Place
  * Tenant
  * Strategy

## How to enable routing decision information?

* * *

To enable routing decision information, set report_targets value to true.

**Note:**  Due to high resource usage, it is not recommended to enable this functionality in production environment.

## How it works?

* * *

If enabled, URS attaches high level target information (Routing Rules, Skill Expressions, Agent Groups, Place Groups) while waiting.

<pre class="lang:default decode:true" title="While Waiting">request to 65200(TServer) message RequestAttachUserData
    AttributeReferenceID    13
    AttributeUserData    [34] 00 01 00 00..
        'RTargetAgentGroup'    'VAG_Skill1'
    AttributeConnID    006c029a6685d004
    AttributeThisDN    '9001'

</pre>

[table id=9 /]

When the interaction is routed, URS attaches information about target object

<pre class="lang:default decode:true">request to 65200(TServer) message RequestUpdateUserData
	AttributeReferenceID	14
	AttributeUserData	[561] 00 14 00 00..
		'RVQID'	'SQBENM69RP39R22KR9QUBT1RQO000002'
		'RTargetTypeSelected'	'2'
		'RTargetRuleSelected'	''
		'RTargetObjectSelected'	'VAG_Skill1'
		'RTargetObjSelDBID'	'115'
		'RTargetAgentSelected'	'agent01'
		'RTargetPlaceSelected'	'Place_6001'
		'RTenant'	'Resources'
		'RStrategyName'	'Route2ChicagoAgentsLowPriority'
		'RStrategyDBID'	'264'
		'CBR-actual_volume'	''
		'CBR-Interaction_cost'	''
		'CBR-contract_DBIDs'	''
		'CBR-IT-path_DBIDs'	''
		'RRequestedSkillCombination'	''
		'RRequestedSkills'(list) 
		'RTargetRequested'	'VAG_Skill1'
		'CustomerSegment'	'default'
		'ServiceType'	'default'
		'ServiceObjective'	''
	AttributeConnID	006c029a6685d004
	AttributeThisDN	'9001'</pre>

[table id=10 /]

## What if you want to use it anyway in production environment?

* * *

If you want to enable it anyway for production environment, I recommend to use &#8216;SetCallOption&#8217; function and list objects configuration to enable it for particular service /interaction type.

For more information about &#8216;report_targets&#8217; and &#8216;SetCallOption&#8217; function, refer to [Genesys URS reference manual.](https://docs.genesys.com/Documentation)