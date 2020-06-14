---
id: 251
title: Difference between SIP REFER and (RE)INVITE
date: 2012-11-13T15:22:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=251
permalink: /2012/11/13/difference-between-sip-refer-and-reinvite/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2012/11/difference-between-sip-refer-and.html
  - /2012/11/difference-between-sip-refer-and.html
dsq_thread_id:
  - "2858897034"
  - "2858897034"
categories:
  - SIP
  - Uncategorized
---
What is this and when it is used? When I started working in SIP environment, it was confusing to me, as well.

But after reading RFC3261, it became clear to me. Simply said, REFER method is used for transferring a call and INVITE is used to change session media information. 

Refer to the example below to understand it more clearly.

**REFER – Example** 

* * *

Suppose Alice and Bob are on call and Alice wants to transfer call to Carol, Alice will send REFER to Bob with Carol information. 

> <pre><a href="http://lh4.ggpht.com/-keIazLIPNU0/UKYdWjqnvpI/AAAAAAAAABU/5QFW3C_TiPw/s1600-h/Transfer-Unattended%25255B9%25255D.gif"><img title="Transfer-Unattended" border="0" alt="Transfer-Unattended" src="http://lh5.ggpht.com/-mnrVuKxQqpM/UKYdXhjYT2I/AAAAAAAAABc/3yTD6Z3YNlQ/Transfer-Unattended_thumb%25255B4%25255D.gif?imgmax=800" width="684" height="593" /></a></pre>
> 
> <pre>REFER sips:bob@client.biloxi.example.com SIP/2.0<br />Via: SIP/2.0/TLS client.biloxi.example.com:506;branch=z9hG4bKnashds8  <br />Max-Forwards: 70<br />From: Alice &lt;sips:alice@atlanta.example.com>;tag=1234567<br />To: Bob &lt;sips:bob@biloxi.example.com>;tag=314159<br />Call-ID: <a href="mailto:12345601@atlanta.example.comCSeq">12345601@atlanta.example.com<br />CSeq</a>: 101 REFER<br />Refer-To: &lt;sips:carol@chicago.example.com><br />Referred-By: &lt;alice@atlanta.example.com><br />Contact: &lt;sips:alice@client.atlanta.example.com><br />Content-Length: 0</pre>

<pre><strong>(RE)INVITE – Example</strong> </pre>



* * *

If Bob wants to session media information, then INVITE is sent again with updated information. Consider, call on hold as an example for this.

In this scenario, Alice calls Bob, then Bob places the call on hold.Bob then takes the call off hold, then Alice hangs up the call.



> 
<pre><a href="http://lh4.ggpht.com/-XAA5x3vTPVE/UKYdZAAxGNI/AAAAAAAAABg/aI9fEtofCkY/s1600-h/Call%252520Hold%25255B6%25255D.gif"><img title="Call Hold" border="0" alt="Call Hold" src="http://lh4.ggpht.com/-w_gsiJbTqVw/UKYdahavQkI/AAAAAAAAABs/VvEVHtRxKlA/Call%252520Hold_thumb%25255B4%25255D.gif?imgmax=800" width="576" height="560" /></a></pre>



**F1 INVITE Alice -> Proxy 1**

      INVITE sips:bob@biloxi.example.com SIP/2.0  
      Via: SIP/2.0/TLS client.atlanta.example.com:5061;branch=z9hG4bK74bf9  
      Max-Forwards: 70  
      From: Alice <sips:alice@atlanta.example.com>;tag=1234567  
      To: Bob <sips:bob@biloxi.example.com>  
      Call-ID: 12345601@atlanta.example.com  
      CSeq: 1 INVITE  
      Contact: <sips:alice@client.atlanta.example.com>  
      Allow: INVITE, ACK, CANCEL, OPTIONS, BYE, REFER, NOTIFY  
      Supported: replaces  
      Content-Type: application/sdp  
      Content-Length: &#8230;

      v=0  
      o=alice 2890844526 2890844526 IN IP4 client.atlanta.example.com  
      s=  
      c=IN IP4 client.atlanta.example.com  
      t=0 0  
      m=audio 49170 RTP/AVP 0  
      a=rtpmap:0 PCMU/8000

<pre><strong>F10 INVITE Bob -> Proxy 1</strong></pre>

<pre>INVITE sips:alice@client.atlanta.example.com SIP/2.0<br />      Via: SIP/2.0/TLS client.biloxi.example.com:5061;branch=z9hG4bKnashds7<br />      Route: &lt;sips:ss1.example.com;lr><br />      Max-Forwards: 70<br />      From: Bob &lt;sips:bob@biloxi.example.com>;tag=314159<br />      To: Alice &lt;sips:alice@atlanta.example.com>;tag=1234567<br />      Call-ID: 12345601@atlanta.example.com<br />      CSeq: 1 INVITE<br />      Contact: &lt;sips:bob@client.biloxi.example.com>;+sip.rendering="no"<br />      Allow: INVITE, ACK, CANCEL, OPTIONS, BYE, REFER, NOTIFY<br />      Supported: replaces<br />      Content-Type: application/sdp<br />      Content-Length: ...<br /><br />      v=0<br />      o=bob 2890844527 2890844528 IN IP4 client.biloxi.example.com<br />      s=<br />      c=IN IP4 client.biloxi.example.com<br />      t=0 0<br />      m=audio 3456 RTP/AVP 0<br />      a=rtpmap:0 PCMU/8000<br />a=sendonly</pre>



Here, you can see Bob changed SDP session attribute as ‘sendonly’ to place the call on hold and to retrieve the call, this will be changed to ‘sendrecv’.