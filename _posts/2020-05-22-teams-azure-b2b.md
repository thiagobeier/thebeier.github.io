---
layout: post
title: Teams - Azure B2B
date: 2020-05-22 12:00
author: beierca
comments: true
categories: [Administration, Azure, Azure b2b, azuread, Communication, External, Federation, Guest, Microsoft Teams, Tips]
---
Hi there

Did you know that you can have 2 (two) different Microsoft Teams' domain users collaborating across companies?

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/3.png" />

You can use the Azure AD B2B to orchestrate this.

Advantages
<ul>
	<li>External / Guest users can be invited to a Teams (channels) on Company A (source)</li>
	<li>External / Guest users can collaborate on supported file types (Excel, Word, PowerPoint) on real-time</li>
	<li>External / Guest users will only see channels they're allowed to within a specific Team on Source Company</li>
	<li>Fully supported on Teams client (flat and web version)</li>
</ul>
Additional tasks
<ul>
	<li>Teams &amp; Channel management</li>
	<li>Email to target (External / guest users) the invitation or Teams' email (to join a team)</li>
	<li>Enable users on Teams on both companies (Office 365 Tenants)</li>
	<li>License users on Teams</li>
</ul>
Enable guest Access on Source Company at Home \ Settings \ Org-settings \ Microsoft Teams \ Allow guest access on Teams (enable it) or go to Teams Admin Center \ Org-wide settings \ Guest Access (set Allow guest access in Teams to On) and proceed with the following options.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/11.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/14.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/2.png" />

&nbsp;

<strong>on Company A:</strong>
<ul>
	<li>create the Team and its channels</li>
	<li>define which channels are going to be private and public</li>
	<li>set General channel (create by default in every Team created) to allow only Admins posting on it</li>
	<li>Manage this Team members and invite guest users user@targetcompany.com</li>
	<li>Share this Team link (... get link to team) with target company so they can join to the team after they accept the invitation</li>
	<li>evaluate its experience</li>
</ul>
<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/6.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/6.png" /></a>

&nbsp;

<strong>on Company B (target company, partner, client, etc.)</strong>
<ul>
	<li>accept the invitation on Microsoft Teams client or web client and get into the Team at Source Company</li>
	<li>check the Team access</li>
	<li>check the Channels' access</li>
	<li>try to collaborate with users from Company A (source company) by posting on the allowed Channel</li>
</ul>
<strong>At this demo</strong>

company A (source company calls ORDERGRID)

users from another company will be joining ORDERGRID's Team and its channels

users from guest company will be able to collaborate under Members channel (Excel file)

users can't post on General channel (only admins: managed by the Source Company)

users from guest company can see all posts and announcements at General channel

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/15.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/15.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/16.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/16.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/17.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/17.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/18.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/18.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/8.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/8.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/19.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/19.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/20.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/20.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/22.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/22.png" /></a>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/23.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/D/23.png" /></a>

<strong>References</strong>

https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies
https://www.microsoft.com/en-us/microsoft-365/blog/2017/09/11/azure-ad-b2b-collaboration-in-microsoft-teams/
https://docs.microsoft.com/en-us/microsoftteams/communicate-with-users-from-other-organizations

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>

&nbsp;
