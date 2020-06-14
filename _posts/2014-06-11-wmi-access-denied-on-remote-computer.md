---
id: 2321
title: 'WMI &#8216;Access Denied &#8216; on remote computer'
date: 2014-06-11T08:42:55+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=2321
permalink: /2014/06/11/wmi-access-denied-on-remote-computer/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "2754844824"
  - "2754844824"
categories:
  - How to
  - Programming
  - Tips
tags:
  - Permission Error
  - Remote Server Monitor
  - Troubleshooting
  - WMI
---
In my current project, I would like to monitor windows 2008 servers remotely and planned to use WMI. While my code worked locally, I got &#8216;Access Denied&#8217; error while trying to access Windows 2008 servers.

Although, I enabled DCOM remote activation, I still received error and close to pulling my hair. Finally, I figured that permissions are not propagated and was set only at root level, causing an issue.

For everyone&#8217;s benefit, I listed steps below to configure DCOM and WMI to monitor remote servers

### **Configure DCOM**

* * *

&nbsp;

<div>
  <ul style="color: #000000;">
    <li>
      On the server to be managed click Start, click Run, type <strong>dcomcnfg</strong>, and then click OK.
    </li>
    <li>
      In the Component Services dialog box, expand Component Services, expand Computers, and then right-click <strong>My Computer</strong> and click <strong>Properties</strong>.
    </li>
    <li>
      In the My Computer Properties dialog box, click the <strong>COM Security tab.</strong>
    </li>
  </ul>
  
  <p>
    <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Dcom-Properties.png"><img class="aligncenter size-full wp-image-2341" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Dcom-Properties.png" alt="Dcom Properties" width="414" height="564" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Dcom-Properties.png 414w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Dcom-Properties-220x300.png 220w" sizes="(max-width: 414px) 100vw, 414px" /></a>
  </p>
  
  <ul style="color: #000000;">
    <li>
      Under Launch and Activation Permissions, click <strong>Edit Limits</strong>.
    </li>
    <li>
      In the Launch Permission dialog box, select &#8216;<strong>Distributed COM Users</strong>&#8216;. In the Allow column under Permissions for User, select <strong>Remote Launch</strong> and select <strong>Remote Activation</strong>, and then click OK.
    </li>
    <li>
      Under <strong>Access Permissions</strong>, click <strong>Edit Limits</strong>.
    </li>
    <li>
      In the Access Permission dialog box, select &#8216;<strong>Distributed COM Users</strong>&#8216;. In the Allow column under Permissions for User, select <strong>Remote Access</strong>, and then click OK.
    </li>
    <li>
      Add the user account to the Distributed COM Users Group in Computer Management, Local Users and Groups on the Server to be managed.
    </li>
    <li>
      Add the user account to the Performance Log Users Group in Computer Management, Local Users and Groups on the Server to be managed.
    </li>
  </ul>
  
  <h3 style="color: #000000;">
    <strong>Configure WMI</strong>
  </h3>
  
  <hr />
  
  <ul style="color: #000000;">
    <li>
      On the server to be managed click Start, click Run, type <strong>wmimgmt.msc</strong>, and then click OK.
    </li>
    <li>
      In the console tree, right-click WMI Control, and then click Properties.
    </li>
    <li>
      Click the Security tab.
    </li>
    <li>
      Select the Root namespace and then click Security.
    </li>
    <li>
      In the Security dialog box, click Add.
    </li>
    <li>
      In the Select Users, Computers, or Groups dialog box, enter the user account. Click the Check Names button to verify your entry and then click OK.
    </li>
    <li>
      In the Security dialog box, under Permissions, select &#8216;Enable Account&#8217; and &#8216;Remote Enable&#8217; for the user account.
    </li>
    <li>
      <span style="text-decoration: underline;">Ensure the permissions propagate to all subnamespaces.</span> <ul>
        <li>
          Under Security, Click Advanced and double click user/group to open properties
        </li>
        <li>
          Select &#8216;This namespaces and subnamespaces&#8217; to propagate permissions
        </li>
      </ul>
    </li>
  </ul>
  
  <p>
    <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Permission-Settings.png"><img class="aligncenter size-full wp-image-2331" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Permission-Settings.png" alt="Permission Settings" width="377" height="481" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Permission-Settings.png 377w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/06/Permission-Settings-235x300.png 235w" sizes="(max-width: 377px) 100vw, 377px" /></a>
  </p>
</div>