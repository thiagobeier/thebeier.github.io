---
layout: post
title: Microsoft Teams - auto assign users to a Team
date: 2020-04-29 13:00
author: beierca
comments: true
categories: [Administration, Automation, Groups, Management, Microsoft Teams, Office365, Powershell, Sync, syncronization]
---
Hi there

At this post I'm covering how to auto assign users to a Team on Teams

<strong>Steps</strong>
<ol>
	<li>Enable Users &amp; Groups Sync from ADDS (Active Directory Domain Services) to Azure AD</li>
	<li>Create the Team on Teams
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/1.png" /></li>
	<li>Go to Azure AD Groups and check the Office 365 Group that corresponds to Team you've created on step #2 above
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/7.png" /></li>
	<li>Change this group assignment from manual to Dynamic
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/2.png" /></li>
	<li>Add the following rule to retrieve users from the Security Group based on a synced attribute, another security group on cloud (synced). Wait for the group to update its membership based on the rule you selected. On my demo I've selected all users with an email address on collabcan.com domain (proxyaddress contains collabcan.com).
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/3.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/4.png" /></li>
	<li>Check the group membership after membership processing status is update complete.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/5.png" /></li>
	<li>Check the Membership tab on Team's Team !TIP: This won't work if your synced source group (used to grab users from) has more than 5000 users. - Check Microsoft Teams <a href="https://docs.microsoft.com/en-us/microsoftteams/limits-specifications-teams">Limits</a>.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/5/6.png" /></li>
</ol>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
