---
id: 1431
title: Public Key Authentication–What it is and how to use it?
date: 2014-03-18T14:12:57+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: https://lakshmikanth.azurewebsites.net/?p=1431
permalink: /2014/03/18/public-key-authenticationwhat-it-is-and-how-to-use-it/
dsq_thread_id:
  - "2789937343"
  - "2789937343"
categories:
  - Security
  - Tips
tags:
  - Security
  - SFTP
  - Tips
  - WinSCP
---
<font size="2" face="Verdana"><strong>What it Public Key Authentication?</strong></font>

<font size="2" face="Verdana">Public Key Authentication (PKA) is more secure way to authenticate to a server than using passwords. Using username/password authentication method, you prove your identity using password but if the server is hacked, an attacker can learn your password. Public Key Authentication solves this problem.</font>

<p align="justify">
  <font size="2" face="Verdana">In PKA, you generate a key pair, consisting of public key, which everybody is allowed to know and private key, which should be kept secret. Private key is able to generate signature and anybody who has your public key can verify that particular signature is genuine.</font>
</p>

<font size="2" face="Verdana">After you generated key pair, public key is copied into server while private key is stored on your local machine. When the server asks you to verify your identity, client generates signature using your private key, server can verify your signature and allow you to login. If the server is hacked or spoofed, attacker only gets your one signature. As signatures cannot be reused, an attacker gains nothing.</font>

<font face="Verdana"><strong>How to use it?</strong></font>

<font face="Verdana">WinSCP is excellent open source tool to transfer files using FTP, SFTP, FTPS and SCP for windows. In this article, I will explain how to setup WinSCP for Public Key Authentication (PKA)</font>

  * <font face="Verdana">Download WinSCP from site (<a title="http://winscp.net/eng/download.php" href="http://winscp.net/eng/download.php">http://winscp.net/eng/download.php</a>)</font>
  * <font face="Verdana">From login dialog box, click ‘Tools’ to open ‘PuttyGen’ application</font>

<img style="float: none; margin-left: auto; display: block; margin-right: auto" alt="puttygen resized 600" src="http://www.jscape.com/Portals/26878/images/puttygen-resized-600.png" /> 

<font face="Verdana"><font size="2">Click ‘Generate’ button to generate a public/private key pair. Enter valid values for ‘Key Passphrase’ and ‘Confirm Passphrase’ fields and remember passphrase values. Now, you can save public and private key by clicking respective buttons on the screen.</font></font>

  * <font face="Verdana"><font size="2">Send public key to your system administrator to include your keys into authorized list</font></font>
  * <font face="Verdana"><font size="2">From WinSCP login dialog box, enter hostname, username and port no (if different from 22). Instead of using password authentication, click ‘Advanced’ button, go to ‘SSH/Authentication’ and select ‘Private Key File’ from your system</font></font>

<img style="float: none; margin-left: auto; display: block; margin-right: auto" src="http://791840461.r.cdn77.net/data/media/screenshots/login.png?v=39" /> <font face="Verdana"></font>

  * <font face="Verdana">If you are going to connect to this server, click ‘Save as’ to save the details.</font>
  * <font face="Verdana"><font size="2">Now click ‘Login’ to login into SFTP server. When prompted to enter ‘passphrase for private key’, enter passphrase generated earlier using ‘PuttyGen’ application</font></font>