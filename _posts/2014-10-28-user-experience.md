---
id: 4521
title: User experience
date: 2014-10-28T14:19:16+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=4521
permalink: /2014/10/28/user-experience/
Delicacy_difficulty:
  - "1"
  - "1"
dsq_thread_id:
  - "3168514493"
  - "3168514493"
categories:
  - User Interface
tags:
  - User Interface
  - UX
---
Currently, <a title="Customer Experience" href="http://en.wikipedia.org/wiki/Customer_experience" target="_blank" rel="noopener noreferrer">Customer Experience </a>(abbreviated as CX) is the buzz word in the industry. In my opinion before embarking customer experience journey, companies should focus on improving user experience of their IT systems.

# What is user experience?

* * *

User experience (UX) is simply how user feels about the system like

  * Look and feel of the user interface
  * Ease of use
  * Ease of finding and managing information

Though, both customer experience and user experience sounds similar, user experience is about anyone internal or external) using the system where as customer experience is mostly external. In the post, I will focus on user experience for internal users and developers.

If having good design saves you 5 seconds per call, it is worth looking at it.  Also, improving user experience is a process and can&#8217;t be achieved by one single roll-out. We can learn valuable lessons to rolling out to selected set of users like internal users before launching it to public (Practice commonly used in web development and unfortunately not yet used in contact center domain).

# User Interface &#8211; Look and Feel

* * *

Look and feel plays important role in improving the usability of your application. Nowadays, applications are very complex and need to be feature rich but at the same time, it need to be easy to use.

For example, <a title="Bulk rename utility" href="http://www.bulkrenameutility.co.uk/Screenshots.php" target="_blank" rel="noopener noreferrer">bulk rename utility tool</a> below is feature rich and have got lot of options to rename files. My personal opinion is that it is excellent tool but it feels like extra work to make this work.

[<img class="aligncenter size-full wp-image-4551" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/bulk-rename.png" alt="Bulk Rename utility" width="500" height="332" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/bulk-rename.png 500w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/bulk-rename-300x199.png 300w" sizes="(max-width: 500px) 100vw, 500px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/bulk-rename.png)

# Usability

* * *

From wikipedia,

> _[Usability](http://en.wikipedia.org/wiki/Usability "Usability") is the extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use.<sup id="cite_ref-9" class="reference"><a href="http://en.wikipedia.org/wiki/User_experience_design#cite_note-9">[9]</a></sup>_
> 
> _Usability is attached with all tools used by humans and is extended to both digital and non-digital devices. Thus it is a subset of user experience but not wholly contained. The section of usability that intersects with user experience design is related to human’s ability to use a system or application. Good usability is essential to a positive user experience but does not alone guarantee it_

As a developer, I thought and believed,  bulk edit tool was an excellent tool but as I started using this (and other tools developed for my own purpose), I realized the difference between developer and user 🙂

Let me explain this with my personal experience. Recently, one of my team member was working to get list of directory numbers from CME and their folder path. CME doesn&#8217;t allow you to export search results and it sound simple to develop.

I offered to help and developed below application using Genesys Platform SDK.

[<img class="aligncenter size-full wp-image-4581" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Original-Design.jpg" alt="Get Directory Number Path" width="782" height="503" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Original-Design.jpg 782w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Original-Design-300x193.jpg 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Original-Design-768x494.jpg 768w" sizes="(max-width: 782px) 100vw, 782px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Original-Design.jpg)

&nbsp;

Simple application 🙂 Connect to configuration server, search for directory number (search box and button available) and output will be written in delimited format in box below. Developer mind within me said &#8220;Great, it meets the requirements. Results are in delimited format which user can copy and paste it in excel for further analysis. Bonus :-)&#8221;

When I started using this tool as user, I realized the hard truth and difference between developer and business user mindset.

As business user

  * I don&#8217;t want to copy and paste to do analysis.Still it doesn&#8217;t save me time as I expected
  * I want to group directory number by the folders
  * If I searched for 6\* already, 65\* should search within the results. I have this information already in my search result and don&#8217;t want to query configuration server again (I know, it is developer again).
  * User interface looks different in different machines

Truth is the above tool only helped me to copy results and doesn&#8217;t help me to the extent as my developer mind imagined 🙁

# Updated version

* * *

I redeveloped user interface design as below

[<img class="aligncenter size-full wp-image-4571" src="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Modified.jpg" alt="Get directory numbers" width="818" height="491" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Modified.jpg 818w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Modified-300x180.jpg 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Modified-768x461.jpg 768w" sizes="(max-width: 818px) 100vw, 818px" />](http://localhost/newlakshmikanth3/wp-content/uploads/2014/10/Modified.jpg)

To improve usability, I updated application as below

  * Used themes &#8211; to have consistent look and feel in different machines (XP/Win 7/ Win 8.1 or Windows 2003/2008)
  * Removed &#8216;Maximize button&#8217; to keep it simple
  * Listed results in grid, which can be sorted and filtered. You can see &#8216;Edit Filter&#8217; button on the bottom and it is fast
  * Grid results can be grouped, which allows me to group by DN Type or Folder Path. This feature was not available out of box and developed it. Very useful feature
  * Added export functionality which will export search results or filtered results in CSV format
  * Kept log viewer in tabbed interface. It helped saving many clicks to open log file from windows explorer to analyze issues, if any

Both version meets same business requirement but no wonder, one prefers updated version as it allows them to do their job efficiently.

# More resources at UX Design

* * *

  * [User Interface: Stack Exchange](http://ui.stackexchange.com/)
  * [UX Exchange](http://uxexchange.com/)
  * [User Interface Engineering](http://www.uie.com/articles/three_hund_million_button/)

# Interesting reads

* * *

  *  <a title="Engineering changes" href="http://blogs.msdn.com/b/e7/archive/2009/06/23/engineering-changes-to-cleartype-in-windows-7.aspx" target="_blank" rel="noopener noreferrer">Why Microsoft changed font to &#8216;Calibri&#8217;?</a>
  * <a title="Flat design trend" href="http://marketblog.envato.com/trends/deeper-look-flat-web-design-trend/" target="_blank" rel="noopener noreferrer">Flat design trend</a>&#8211; More related with web design but worth reading it