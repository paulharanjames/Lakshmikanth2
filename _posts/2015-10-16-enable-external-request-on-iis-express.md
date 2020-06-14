---
id: 6041
title: Enable external request on IIS Express
date: 2015-10-16T13:11:47+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=6041
permalink: /2015/10/16/enable-external-request-on-iis-express/
dsq_thread_id:
  - "4230616283"
Delicacy_difficulty:
  - "1"
dsq_needs_sync:
  - "1"
categories:
  - Genesys
---
I was working on Asp.net MVC application and had to test it from another machine. By default, IIS Express doesn&#8217;t allow remote connections and you will get an error &#8216;Bad Request &#8211; Invalid Host Name&#8217; .In this post, I will explain how to enable external access to IIS express

## Step 1 : Configure IIS Express

* * *

For Visual Studio 2015,  open file _**<solution>/.vs/config/applicationhost.config**_ and _**localhost**_ in **&#8216;bindingInformation&#8217;** to **&#8216;*&#8217;. ** After making changes, it should like below

[<img class="aligncenter wp-image-6001 size-full" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/HTTP_Bindings.png" alt="HTTP Binding" width="781" height="101" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/HTTP_Bindings.png 781w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/HTTP_Bindings-300x39.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/HTTP_Bindings-768x99.png 768w" sizes="(max-width: 781px) 100vw, 781px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/HTTP_Bindings.png)

## Step 2: Allow URL Access

* * *

  * Open command prompt in &#8216;Administrator&#8217; mode
  *  Run following command

<pre class="lang:batch decode:true">netsh http add urlacl url=http://*:51603/ user=everyone</pre>

**Note:** Run this command with your IIS listening port. In my case above, application was listening on port 51603

## Step 3: Configure Firewall Port

* * *

  *  Go to the “Control Panel\Windows Firewall”
  * Click “Advanced settings”
  *  Select “Inbound Rules”
  * Click on “New Rule …” button
  * Select “Port”, click “Next
  * Fill your IIS Express listening port number, click “Next”

[<img class="aligncenter size-full wp-image-6011" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/Inbound_Rule.png" alt="Inbound Rule" width="714" height="581" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/Inbound_Rule.png 714w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/Inbound_Rule-300x244.png 300w" sizes="(max-width: 714px) 100vw, 714px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2015/10/Inbound_Rule.png)

  * Select “Allow the connection”, click “Next”
  * Check where you would like allow connection to IIS Express (Domain, Private, Public), click “Next”
  * Enter rule name and click “Finish”

&nbsp;

**IMPORTANT:** For latest version of visual studio, please read solution details in comments below