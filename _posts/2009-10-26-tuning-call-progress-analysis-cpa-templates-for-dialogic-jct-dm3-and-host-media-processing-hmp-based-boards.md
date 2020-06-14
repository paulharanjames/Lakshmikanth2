---
id: 591
title: Tuning Call Progress Analysis (CPA) templates for Dialogic® JCT, DM3 and Host Media Processing (HMP)-based boards
date: 2009-10-26T11:59:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=591
permalink: /2009/10/26/tuning-call-progress-analysis-cpa-templates-for-dialogic-jct-dm3-and-host-media-processing-hmp-based-boards/
blogger_blog:
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
blogger_permalink:
  - /2009/10/tuning-call-progress-analysis-cpa.html
dsq_thread_id:
  - "2756703610"
categories:
  - Call Progress Analysis
  - CPA
  - Dialer (OCS)
  - Dialogic
  - OCS
---
##### Reference: [http://www.dialogic.com/support/helpweb/dxall/tn924.aspx](http://www.dialogic.com/support/helpweb/dxall/tn924.aspx "http://www.dialogic.com/support/helpweb/dxall/tn924.aspx")

**Summary:**  
This technote provides instructions for modifying the Positive Answering Machine Detection (PAMD) and Positive Voice Detection (PVD) qualification template parameters on Dialogic® Springware, DM3 and Host Media Processing (HMP)-based boards in seeking higher successful PAMD and PVD rates. 

**Overview:**  
Call Progress Analysis (CPA) is the process used to automatically detect whether an answering machine or live voice answered a call. Dialogic® products have the ability to detect these conditions with audio streams that can come over a Public Switched Telephone Network (PSTN) connection or IP connection. Positive Answering Machine Detection (PAMD) and Positive Voice Detection (PVD) are classifications of the Call Progress Analysis feature that enable the application to determine whether a call has been answered by an answering machine or a live person.  
The original PAMD and PVD algorithms take into account variables such as the length of the greeting and the background noise level. The current business and home environments have significantly shifted from analog to digital / IP phones so that the original algorithms no longer produce satisfactory results. This technote provides instructions for modifying the PAMD and PVD qualification template parameters on Dialogic® Springware, DM3 and Host Media Processing (HMP)-boards to help accomplish higher successful PAMD and PVD rates. The same procedure can be followed for Windows® and Linux service releases as well as the dx_dial or GlobalCall method of initiating Call Progress.  
****

**Qualification Templates:**  
The Call Progress Qualification Templates are a set of parameter definitions that control voice and answering machine detection. The same parameters are present in Dialogic® product lines including Springware, DM3, HMP-based boards and control detections regardless of using the DX or GC method. The Qualification Templates are broken down into two sections: PVD and PAMD. Tables 1 and 2 below contain all the parameters for both PVD and PAMD sections as well as the default and recommended values for each parameter. (Note: default values may change with new Service Updates. Always check System Release Update Guide for more information). 

[<img title="image" border="0" alt="image" src="http://ctiworld.files.wordpress.com/2009/10/image_thumb.png" width="287" height="595" />](http://ctiworld.files.wordpress.com/2009/10/image.png) </p> 

**Modifying Qualification Templates Dialogic Springware:**  
When using a Dialogic® Springware board, PVD and PAMD qualification template modifications are only available via an undocumented API and can be modified without restarting the Dialogic service. In addition, qualification template settings are reset to the defaults each time the Dialogic service is restarted. Thus, it is required that any modifications be done upon application initialization.  
There are two undocumented functions that can be used to view and modify the PVD and PAMD qualification template parameters: dx\_setqualtmplate and dx\_getqualtmplate. To set the parameter values of the PVD and PAMD templates a data structure needs to be created with the values from Tables 1 and 2 above. Pass each of the qualification data structures to the dx_setqualtmplate function with the voice board device and template ID. **NOTE: The dx\_setqualtmplate and dx\_getqualtmplate functions are both undocumented API&#8217;s and should be used at your own risk &#8211; Dialogic may change or remove the usage of these API&#8217;s without written notice.**

> tn\_qlt.pvd\_qual.qminsnr = qminsnr;  
> tn\_qlt.pvd\_qual.qmaxsnr = qmaxsnr;  
> tn\_qlt.pvd\_qual.maxpk = maxpk;  
> tn\_qlt.pvd\_qual.maxring = maxring;  
> tn\_qlt.pvd\_qual.ringthres = ringthres;  
> tn\_qlt.pvd\_qual.pvdwin = pvdwin;  
> tn\_qlt.pvd\_qual.pvdthresh = pvdthresh;  
> tn\_qlt.pvd\_qual.pvdrblow = pvdrblow;  
> tn\_qlt.pvd\_qual.pvdrbhig = pvdrbhig;  
> tn\_qlt.amd\_qual.maxansiz = maxansiz;  
> tn\_qlt.amd\_qual.maxans2 = maxans2;  
> tn\_qlt.amd\_qual.maxans3 = maxans3;  
> tn\_qlt.amd\_qual.lohiss = lohiss;  
> tn\_qlt.amd\_qual.hihiss = hihiss;  
> tn\_qlt.amd\_qual.bhparm = bhparm;  
> tn\_qlt.amd\_qual.cvthr1 = cvthr1;  
> tn\_qlt.amd\_qual.cvthr2 = cvthr2;  
> tn\_qlt.amd\_qual.maxcvth = maxcvth;  
> tn\_qlt.amd\_qual.nmaxbrod = nmaxbrod;  
> tn\_qlt.amd\_qual.nmaxerg = nmaxerg;  
> tn\_qlt.amd\_qual.maxsil = maxsil;  
> tn\_qlt.amd\_qual.voice\_thres = voice\_thres;  
> tn\_qlt.amd\_qual.sil\_thres = sil\_thres;  
> tn\_qlt.amd\_qual.bandf\_low = bandf\_low;  
> tn\_qlt.amd\_qual.bandf\_high = bandf\_high;  
> dx\_setqualtmplate(dev, qual\_template, &tn_qlt)  
> dx\_getqualtmplate(dev, qual\_template, &tn_qlt)  
> where…  
> dev – voice board device handle (dxxxB1)  
> qual_template – qualification template ID- PVD (5) or PAMD (11)  
> tn_qlt – pointer to the qualification template data structure

Please see attached [QUAL.C source code](http://www.dialogic.com/support/helpweb/dxall/tn924/qual.c) for complete usage.  
**DM3:**  
When using a Dialogic® DM3 board, all PVD and PAMD qualification template modifications are ONLY available via config files and can NOT be modified without restarting the Dialogic® service. The following steps will be used to modify DM3 qualification templates: 

  1. As a precaution, save a backup copy of the fcd, pcd and config files which you will be editing 
  2. Scroll down to the bottom of the .config file to the [sigDet] section that begins with “!GENERIC QUAL TEMPLATE – For R4 User Defined Tones. **Note: There are several [sigDet] sections in the .config file so be sure to find the correct one.** 
  3. Add &#8220;init iNNN” immediately below the [sigDet] line where iNNN is the following: Voice Channels iNNN  
    E1 – 60 Voice Channels i60  
    E1 – 120 Voice Channels i120  
    T1 – 48 Voice Channels i48  
    T1 – 96 Voice Channels I96 
  4. Scroll down to the bottom of the [sigDet] section, and add “DeletePvd 128193”. The number represents the default PVD qualification ID defined for DM3 boards. 
  5. On the next line, add the new PVD qualification template parameters followed by &#8220;CreatePvd&#8221;. 
  6. On the next line, add “DeletePamd 106561”. The number represents the default PAMD qualification ID defined for Dialogic® DM3 boards. 
  7. On the next line, add the new PAMD qualification template parameters followed by &#8220;CreatePamd&#8221;.   
    > [sigDet]  
    > init i96  
    > !Delete the default PVD qualification template  
    > DeletePvd 128193  
    > !User defined Pvd template.  
    > PvdDesc signalId 128193  
    > PvdDesc signalLabel 0000  
    > PvdDesc minSnr 50  
    > PvdDesc maxSnr 600  
    > PvdDesc maxPk 2  
    > PvdDesc maxRing 5  
    > PvdDesc ringThresh 10000  
    > PvdDesc PvdWin 8  
    > PvdDesc PvdVthresh 5000  
    > PvdDesc PvdRbLow 380  
    > PvdDesc PvdRbHigh 510  
    > CreatePvd  
    > !Delete the default PAMD qualification template  
    > DeletePamd 106561  
    > !User defined PAMD template.  
    > PamdDesc signalId 106561  
    > PamdDesc signalLabel 0000  
    > PamdDesc minRing 190  
    > PamdDesc mask 1  
    > PamdDesc maxAnsiz1 159  
    > PamdDesc maxAnsiz2 159  
    > PamdDesc maxAnsiz3 159  
    > PamdDesc loHiss 22  
    > PamdDesc hiHiss 16  
    > PamdDesc bhParm 5  
    > PamdDesc cvThresh1 80  
    > PamdDesc cvThresh2 165  
    > PamdDesc maxCvThresh 390  
    > PamdDesc nMaxBroad 2  
    > PamdDesc nMaxErg 65  
    > PamdDesc maxSilence 45  
    > PamdDesc voiceThresh 25  
    > PamdDesc silenceThresh 5000  
    > PamdDesc rjFbandLow 0  
    > PamdDesc rjFbandHigh 0  
    > CreatePamd

  8. Save changes to the .config file and exit text editor. 
  9. Using a text editor, open the .pcd file corresponding to the .config file you just modified. 
 10. Scroll down to the [COMP sigdet] section and change the InitOption value from YES to NO. The section should be revised as follows:  
    > [COMP sigdet]  
    > { 
    > 
    > > Attribute :std_ComponentType:0x07  
    > > NumInstances :96  
    > > StartInstanceNum :1  
    > > ConfigOption :YES  
    > > InitOption :NO                     <\---\---\----- Change from YES to NO  
    > > DependentComp :waveAnalyser
    > 
    > }
    
    **Note: NumInstances will vary depending on the board in use. In this example, the value reflects a T1 board with 96 channels.** </li> 
    
      * Save your changes to the .pcd file and run the fcdgen utility to create an fcd file:  
        fcdgen filename.config 
      * Restart DCM for changes to take effect  
        Please see attached [DM3 Config File](http://www.dialogic.com/support/helpweb/dxall/tn924/ml2_qsa_ni2.config.txt) for complete template changes. </ol> 
    
    **Host Media Processing (HMP):**  
    When using Dialogic® HMP-based boards (i.e., Dialogic® based on or otherwise incorporating Dialogic® HMP software), all PVD and PAMD qualification template modifications are ONLY available via config files and can NOT be modified without restarting the Dialogic® service. The following steps will be used to modify HMP qualification templates:  
    **Note:** 4r4v4e4c4s4f4i\_hib\_pur pcd/fcd/config file will be used as an example in this procedure. Your pcd/fcd/config file names likely will change based on license and system release used. 
    
      1. As a precaution, save a backup copy of the fcd, pcd and config files which you will be editing 
      2. Open the Host&#8217;s PCD file (4r4v4e4c4s4f4i\_hib\_pur.pcd) and search for &#8220;COMP sigdet&#8221; 
      3. Once you&#8217;ve found this section change the InitOption from YES to NO 
      4. Also, while here note the NumInstances, you will need to reference this in the config file.  
        > [COMP sigdet]  
        > { 
        > 
        > > Attribute :std_ComponentType:0x07  
        > > NumInstances :4                      <\---\---\---\----Note this value  
        > > StartInstanceNum :1  
        > > ConfigOption :YES  
        > > InitOption :NO                           <\---\---\----- Change from YES to NO  
        > > DependentComp :waveAnalyser
        > 
        > }
    
      5. Save and exit the PCD file and open the hosts config file (4r4v4e4c4s4f4i\_hib\_pur.config) 
      6. Search for the &#8220;[sigDet]&#8221; section of the config file &#8211; if the section does not exist add it at the bottom of the config file 
      7. Add &#8220;init iNNN” immediately below the [sigDet] line where iNNN is the NumInstances noted in the pcd file 
      8. On the next line add “DeletePvd 128193”. The number represents the default PVD qualification ID defined for HMP. 
      9. On the next line, add the new PVD qualification template parameters followed by &#8220;CreatePvd&#8221;. 
     10. On the next line, add “DeletePamd 106561”. The number represents the default PAMD qualification ID defined for HMP. 
     11. On the next line, add the new PAMD qualification template parameters followed by &#8220;CreatePamd&#8221;.  
        > [sigDet]  
        > init i4  
        > !Delete the default PVD qualification template  
        > DeletePvd 128193  
        > !User defined Pvd template.  
        > PvdDesc signalId 128193  
        > PvdDesc signalLabel 0000  
        > PvdDesc minSnr 50  
        > PvdDesc maxSnr 600  
        > PvdDesc maxPk 2  
        > PvdDesc maxRing 5  
        > PvdDesc ringThresh 10000  
        > PvdDesc PvdWin 8  
        > PvdDesc PvdVthresh 5000  
        > PvdDesc PvdRbLow 380  
        > PvdDesc PvdRbHigh 510  
        > CreatePvd  
        > !Delete the default PAMD qualification template  
        > DeletePamd 106561  
        > !User defined PAMD template.  
        > PamdDesc signalId 106561  
        > PamdDesc signalLabel 0000  
        > PamdDesc minRing 190  
        > PamdDesc mask 1  
        > PamdDesc maxAnsiz1 159  
        > PamdDesc maxAnsiz2 159  
        > PamdDesc maxAnsiz3 159  
        > PamdDesc loHiss 22  
        > PamdDesc hiHiss 16  
        > PamdDesc bhParm 5  
        > PamdDesc cvThresh1 80  
        > PamdDesc cvThresh2 165  
        > PamdDesc maxCvThresh 390  
        > PamdDesc nMaxBroad 2  
        > PamdDesc nMaxErg 65  
        > PamdDesc maxSilence 45  
        > PamdDesc voiceThresh 25  
        > PamdDesc silenceThresh 5000  
        > PamdDesc rjFbandLow 0  
        > PamdDesc rjFbandHigh 0  
        > CreatePamd
    
     12. Save and exit the config file and run the fcdgen utiltiy to create an fcd file:  fcdgen 4r4v4e4c4s4f4i\_hib\_pur.config 
     13. Restart the Dialogic HMP services. 
    
    Please see attached config file [HMP Config File](http://www.dialogic.com/support/helpweb/dxall/tn924/4r4v4e4c4s4f4i_hib_pur.config.txt) for completed template changes.  
    **Related Documentation:**  
    It is also recommended to review the application note: [Call Progress Analysis: Global Call API Usage and Protocol Configuration](http://www.dialogic.com/network/csp/appnots/10117_CPA_SR6_HMP2.pdf)  
    **Glossary of Acronyms and Terms:**  
    Global Call CPA — Global Call API function calls perform CPA using an attached voice device and report CPA results via the GCEV\_MEDIADETECTED and GCEV\_DISCONNECTED events.   
    Voice API CPA — The Voice API dx\_dial() function performs CPA using a voice resource directly and reports results via the TDX\_CALLP event.  
    Qualification template &#8212; Definitions used by the PAMD and PVD algorithms in detecting voice detection
    
    [ ](http://www.dialogic.com/support/helpweb/dxall/tn924.aspx "http://www.dialogic.com/support/helpweb/dxall/tn924.aspx")