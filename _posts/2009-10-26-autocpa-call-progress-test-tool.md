---
id: 581
title: AutoCPA Call Progress test tool
date: 2009-10-26T12:04:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=581
permalink: /2009/10/26/autocpa-call-progress-test-tool/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2009/10/autocpa-call-progress-test-tool.html
  - /2009/10/autocpa-call-progress-test-tool.html
dsq_thread_id:
  - "2957245473"
  - "2957245473"
categories:
  - AutoCPA
  - Call Progress Analysis
  - CPA
  - Dialer (OCS)
  - Dialogic
---
#####  

**Reference: [http://www.dialogic.com/support/helpweb/dxall/iw1365.aspx](http://www.dialogic.com/support/helpweb/dxall/iw1365.aspx "http://www.dialogic.com/support/helpweb/dxall/iw1365.aspx")**

**Issue overview:**

**** 

The [AutoCPA](http://www.dialogic.com/support/dld.aspx?id=iw1365) tool allows the testing and tuning of various call progress parameters outside of a production environment by using a set of recordings that represent a real site. This type of information may be useful when troubleshooting call progress analysis issues, for example.    
The AutoCPA tool performs call progress analysis (CPA) using the dx_dial API method with two voice resources (one voice resource for playing the file and the other for performing CPA) and recorded PCM files. The tool does not require any network resources and can be configured for various test scenarios. The tool can be loaded with multiple recorded PCM files and logs detection results directly to a command window and output text file for analysis.  
****

**Recordings:** 

Users of the [AutoCPA](http://www.dialogic.com/support/dld.aspx?id=iw1365) tool must gather recordings themselves for testing – the AutoCPA tool does not make the recordings itself. Recordings are normally gathered from another system in PCM 8K. The recordings should commence when the application starts call progress analysis and should end when the call has completed such that all the audio is captured.  
Alternatively, the Dialogic<sup>®</sup> SC Record tool can be used to record ALL the call activity on a particular voice channel for a certain amount of time. The user must then separate the calls into individual files using an audio editor. Note all recordings must have the PCM extension – otherwise the AutoCPA tool will not recognise the files.    A link to SC Record utility can be found [here.](http://www.dialogic.com/support/helpweb/dxall/tn183.aspx)  
Once completed, the PCM recordings can then be moved into the PCM directory of the AutoCPA tool (or where specified in the config.inf file – PCMdir field)  
****

**Configuration:** 

The AutoCPA configuration (where applicable) is done through config.inf file, which is loaded upon initialization. Not all the parameters in the config.ini file are common between Dialogic® DM3 series Media Boards and Dialogic® JCT series Media Boards; for more information, visit the programming library documentation. The settings include:  
• General config: PCM directory, log output, voice resources.  
• DX_CAP Struct Settings  
• CPA Qualification Templates (JCT Media Boards only – configuration of DM3 Media Boards is done manually through the protocol  configuration file)  
• Global Tone Definitions (user and pre-defined)  
The following settings are required to run the AutoCPA tool – all remaining settings will be set to their default values if commented out.  
PCMdir = PCM                 # Directory where PCM recorded files are stored  
LogFile = Results.txt      # Filename to log output  
PlayDev = dxxxB1C1     # Voice device used for playing recorded PCM file  
CallpDev = dxxxB1C2    # Voice device used for call progress  
Usage and output**:**  
Once the recordings have been gathered and the configuration file has been saved, run the [AutoCPA](http://www.dialogic.com/support/dld.aspx?id=iw1365) tool in a command prompt or double-click the file &#8211; no command line arguments are needed.  
Once the tool has processed the PCM recordings in the specified PCM directory, the results will be written to the Results.txt file (or the location specified in the config.inf file – LogFile field). The results log file will contain the detected result for each recording in the following format:  
[Recording directory] \ [recorded filename] \* [detection result] \* [detection time]  
For example, the detection result:  PCM\test.pcm \* CON_PVD \* 6.360 means: test.pcm was detected as a Positive Voice Detection (PVD) at 6.360 seconds into the file.  The detection time can be useful, for example, to diagnose mis-detection issues that may have been caused by background noise.  
****

**What are the problem types that [AutoCPA](http://www.dialogic.com/support/dld.aspx?id=iw1365)can be used for?**

  * Mis-detections and tuning while using the DX method of CPA 
  * DTMF mis-detections and tuning 
  * Tone Definitions mis-detections and tuning 

   **  
Product list:  
**  
Dialogic® DMV Media Boards  
Dialogic® JCT Media Boards  
Dialogic® Host Media Processing (HMP) Software for Windows®  
   **  
GLOSSARY OF ACRONYMS / TERMS  
** CPA – Call Progress Analysis  
PVD – Positive Voice Detection  
PAMD – Positive Answering Machine Detection