---
id: 541
title: Unable to find manifest signing certificate in the certificate store
date: 2010-04-15T09:53:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=541
permalink: /2010/04/15/unable-to-find-manifest-signing-certificate-in-the-certificate-store/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2010/04/unable-to-find-manifest-signing.html
  - /2010/04/unable-to-find-manifest-signing.html
dsq_thread_id:
  - "3194098561"
  - "3194098561"
categories:
  - Programming
---
While developing Softphone application using VS 2008, I moved a project from one computer to a different one. When I then tried to rebuild the solution I received the following error:

&#8220;Unable to find manifest signing certificate in the certificate store&#8221;

As I was sure that I wasn&#8217;t using any certificate to sign the assembly I couldn&#8217;t understand the reason for this error message. It turned out that I had to manually go into the *.vbproj file and remove the following four lines that were apparently left over from some past experiments with signing using a certificate:

<manifestcertificatethumbprint>&#8230;</manifestcertificatethumbprint>  
<manifestkeyfile>&#8230;</manifestkeyfile>  
<generatemanifests>&#8230;</generatemanifests>  
<signmanifests>&#8230;</signmanifests>

After I had removed those lines I reloaded the project and the solution rebuilt just fine.