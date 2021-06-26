---
layout: post
title: Teams Interaction (chat) between different domains on the same Office 365 tenant.
date: 2020-04-07 12:30
author: beierca
comments: true
categories: [Administration, Azure AD, domains, Microsoft Teams, Office365, upn, userprincipalname]
---
Hi there

Do you know if users from different domains (<em>UPN - User Principal Name</em>) under the same Office 365 tenant can talk to each other using MS Teams?

Short answer: YES
<ol>
	<li>Go to your DNS preferred provider and buy 02 different domains</li>
	<li>Go to your Office 365 Tenant and add those 02 different domains</li>
	<li>Enable 02 different users, one on each domain (@domainA.com , @domainB.com)</li>
	<li>Log on 02 different browsers or Teams client and Browser and try to reach user@domainA.com from user@domainB.com and vice-versa</li>
</ol>
Check interaction in action

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/138.png"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/138.png" /></a>

<span style="color:#ff0000;"><strong>TIPs!</strong></span>
<ol>
	<li>users can be Azure AD synced (synced from your on-premises ADDS - Active Directory Domain Services)</li>
	<li>users on on-premises ADDS needs to be nested on different OUs (if you manage different UPN / domains / companies) at the same Active Directory domain.</li>
	<li>users need to have different UPN (User Principal Name), email address and ProxySMTPAddress attributes proper configured to be synced over to Azure AD / Office 365.</li>
</ol>
Please check the <strong><a href="https://thiagobeier.wordpress.com/2020/04/01/add-an-additional-domain-at-office-365/">article</a></strong> I posted on how to Add an additional domain at Office 365

Please check the <strong><a href="https://thiagobeier.wordpress.com/2020/04/08/add-a-new-user-on-your-office-365-tenant-different-email-domain/">article</a></strong> I posted on how to Create a new user with different domain / UPN (UserPrincipalName) on Office 365

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
