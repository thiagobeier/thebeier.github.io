---
layout: post
title: BEFORE INSTALLING MIM 2016
date: 2016-04-20 13:00
author: beierca
comments: true
categories: [Identity Management, Uncategorized]
---
<strong>What is MIM?</strong>

<a href="https://technet.microsoft.com/en-us/library/mt150253.aspx?f=255&amp;MSPPError=-2147217396">https://technet.microsoft.com/en-us/library/mt150253.aspx?f=255&amp;MSPPError=-2147217396</a>

<strong>How does it work?</strong>
<ul>
	<li>Syncing, managing and enabling users in office 365</li>
	<li>Getting users from HR system and creating users, managing identities in ADDS, Exchange and Lync/S4B.</li>
	<li>In addition, so much more.</li>
</ul>
<strong>What are the hardware requirements?</strong>
<ul>
	<li>Better virtualized (VMWARE, Hyper-V and other supported hypervisor)</li>
</ul>
<strong>What are the Software requirements?</strong>
<ul>
	<li>WS 2012/R2, Exchange, Lync/S4B, PowerShell, VBscript</li>
	<li>SharePoint 2013 Foundation Complete installation (standalone) with remote SQL database.</li>
</ul>
<strong>Can I separate the MIM roles between servers?</strong>

YES, the most common scenario is having a dedicated server to Sync, other to FIM/MIM service and Portal (SharePoint foundation and registration) and another server preferred at DMZ to the password reset portal (accessed externally).

<strong>Does it use any open source solution to improve it?</strong>

YES. Now at the MIM 2016 server MSFT has released the MIM WAL (Workflow Activity Library) and you can build by yourself following this guide here. This way you will be able to improve the way you develop your solution.

More information at <a href="https://github.com/Microsoft/MIMWAL/wiki">https://github.com/Microsoft/MIMWAL/wiki</a>

MIM Wal Deployment <a href="https://github.com/Microsoft/MIMWAL/wiki/build-and-deployment">https://github.com/Microsoft/MIMWAL/wiki/build-and-deployment</a>

<strong>What do you recommend me to learn before using MIM?</strong>

Do not do what I have done. It’s a good advice to learn C#, PowerShell and strong knowledge of ADDS (Active Directory Domain Services) structure (objects, extension attributes, etc.). I also I recommend you to have skills involving Exchange and Lync 2013/Skype4Business administration and troubleshooting if you want to work with them (used when you want to create users in ADDS, give them a mailbox account and make them enabled to use IM in Lync/Skype for business).

<strong>Can I use shared SQL database or instance (even though clustered)?</strong>

NO.

Let me explain a few reasons.

When you’re about to install the SharePoint 2013 foundation for MIM2016 or FIM2010R2SP1 you don’t receive a warning saying that you need a dedicated SQL database or instance to it. However, if you do it in production environment once you have a dedicated SQL (clustered or not) database or instance to MIM you can put SharePoint databases, sync, service databases pointed to the same server or instance. But never share it with another SQL database or production instance because during the SharePoint 2013 foundation it makes a few changes at the SQL server parameters affecting your SQL server infrastructure impacting in parallelism as you can see here

<a href="https://technet.microsoft.com/en-us/library/hh292622.aspx">https://technet.microsoft.com/en-us/library/hh292622.aspx</a>

<a href="https://technet.microsoft.com/en-us/library/cc262243.aspx">https://technet.microsoft.com/en-us/library/cc262243.aspx</a>

<a href="https://davidlozzi.com/2014/04/08/installing-sharepoint-2013-foundation/">https://davidlozzi.com/2014/04/08/installing-sharepoint-2013-foundation/</a>

<strong>Attention: </strong>At the customer, because his environment made a huge mistake deploying it in a shared SQL server\instance in a production environment even though it was an infrastructure environment (only used for system center, MIM, Lync, RDS, etc.)

SharePoint specialists warn about using a dedicated instance for SharePoint 2013 foundation only and another instance for MIM and FIM solution such as SQL\SPT2013 and SQL\MIM.
<ul>
	<li>MIMWAL Site - <a href="http://aka.ms/MIMWAL">http://aka.ms/MIMWAL</a></li>
	<li>MIMWAL Releases - <a href="http://aka.ms/MIMWAL/Releases">http://aka.ms/MIMWAL/Releases</a></li>
	<li>MIMWAL Documentation Wiki - <a href="http://aka.ms/MIMWAL/Wiki">http://aka.ms/MIMWAL/Wiki</a></li>
	<li>MIMWAL FAQ - <a href="http://aka.ms/mimwal/faq">http://aka.ms/mimwal/faq</a></li>
	<li>MIMWAL GitHub Code Repo - <a href="http://aka.ms/MIMWAL/Repo">http://aka.ms/MIMWAL/Repo</a></li>
	<li>MIMWAL TechNet Q&amp;A Forum - <a href="http://aka.ms/MIMWAL/Forum">http://aka.ms/MIMWAL/Forum</a></li>
</ul>
&nbsp;

Once again, Thank you.

Thiago Beier

&nbsp;

&nbsp;
