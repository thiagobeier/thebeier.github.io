---
layout: post
title: Deploying Microsoft Teams - must read 2
date: 2020-05-11 12:00
author: beierca
comments: true
categories: [Administration, governance, guide, Microsoft Teams, Office365, processes]
---
Hi there
<p style="text-align:justify;">This article is more technical than the <a href="https://thiagobeier.wordpress.com/2020/04/18/deploying-microsoft-teams-must-read/">first</a> one. However, I'm trying to align the whys behind the technical approach. Moreover, if your goal it's to Support remote workers using Microsoft Teams (Work From Home), please click <a href="https://docs.microsoft.com/en-us/microsoftteams/support-remote-work-with-teams" target="_blank" rel="noopener">here</a>.</p>
<img class=" aligncenter" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" />
<p style="text-align:justify;">Regardless of your project size that relies on the company size you should have in mind which Teams' features your client is looking for.</p>

<ul style="text-align:justify;">
	<li>Where to <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-overview" target="_blank" rel="noopener">start and what is Teams</a>?</li>
	<li>is there a willing to allow <a href="https://docs.microsoft.com/en-us/microsoftteams/guest-access" target="_blank" rel="noopener">guest access</a>?</li>
	<li>will users be able to <a href="https://docs.microsoft.com/en-us/microsoft-365/admin/create-groups/manage-creation-of-groups?view=o365-worldwide" target="_blank" rel="noopener">create teams and channels by default</a>?</li>
	<li>will users be able to <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-scoped-directory-search" target="_blank" rel="noopener">join at public teams</a>?</li>
	<li>will users be able to create meetings with <a href="https://docs.microsoft.com/en-us/microsoftteams/set-up-audio-conferencing-in-teams" target="_blank" rel="noopener">Audio Conferencing</a>? - <a href="https://thiagobeier.wordpress.com/2020/04/28/teams-audio-conferencing/" target="_blank" rel="noopener">check my article</a>.</li>
	<li>will users be able to create <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-live-events/what-are-teams-live-events" target="_blank" rel="noopener">Live Meetings</a>?</li>
	<li>will users be able to use <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-app-permission-policies" target="_blank" rel="noopener">third party</a> applications?</li>
	<li>will users be able to use all <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-app-permission-policies" target="_blank" rel="noopener">Microsoft published</a> applications?</li>
	<li>will users be able to use / upload <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-custom-app-policies-and-settings" target="_blank" rel="noopener">custom applications</a> to Teams?</li>
	<li>will users need <a href="https://docs.microsoft.com/en-us/microsoftteams/teams-app-setup-policies" target="_blank" rel="noopener">different Teams application setup</a> (pinned apps)?</li>
	<li>will all of those changes be targeted by Group membership?
<ul>
	<li><span style="color:#ff0000;"><strong>Yes</strong></span>: break down each policy by Group membership need but AVOID to target policies by user or larger group of users. Prefer to assign default policies to large number of users. If you have 12k users for a specific team app policy target those users to default Org-wide policy and have separate security groups for small groups up to 5k users so you can use batch to assign them.</li>
	<li><span style="color:#ff0000;"><strong>No</strong></span>: make that simple - always prefer default setup</li>
</ul>
</li>
	<li>will your Organization <a href="https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership" target="_blank" rel="noopener">assign users to teams dynamically</a>?</li>
	<li>will your Organization <a href="https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/licensing-groups-assign" target="_blank" rel="noopener">assign licenses to users dynamically</a>?</li>
	<li>will your Organization <a href="https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sync-whatis" target="_blank" rel="noopener">sync its users, computers and security groups</a> to Cloud (Azure AD Connect)?</li>
	<li>will your <a href="https://docs.microsoft.com/en-us/azure/active-directory/user-help/my-apps-portal-end-user-access" target="_blank" rel="noopener">Organization centralize how users use published applications</a> on Office 365 (https://myapps.microsoft.com)?</li>
	<li>will <a href="https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-userstates" target="_blank" rel="noopener">MFA be enabled</a> by default to all users?</li>
	<li>will your <a href="https://support.office.com/en-us/article/share-content-in-a-meeting-in-teams-fcc2bf59-aecd-4481-8f99-ce55dd836ce8" target="_blank" rel="noopener">Organization allow users to share contents</a> with external users on meetings? - check <a href="https://support.office.com/en-us/article/share-a-file-in-teams-0c4d34ee-5dd8-46d5-ab35-0d227b5e6eb5" target="_blank" rel="noopener">here</a>.</li>
	<li>you can also use <a href="https://docs.microsoft.com/en-US/microsoftteams/use-advisor-teams-roll-out?WT.mc_id=TeamsAdminCenterCSH">Advisor for Teams</a> to assist and guide you through your Microsoft Teams deployment. Have in mind if you <strong><a href="https://docs.microsoft.com/en-us/microsoftteams/teams-app-permission-policies" target="_blank" rel="noopener">disable all Microsoft applications</a></strong> at your Organization the <strong>Advisor for Teams</strong> won't setup properly and it will fail.</li>
	<li>Are you <a href="https://docs.microsoft.com/en-us/microsoftteams/upgrade-start-here" target="_blank" rel="noopener">upgrading to Teams</a>?</li>
	<li>is there any need for <a href="https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/plan-hybrid-connectivity?toc=/SkypeForBusiness/sfbhybridtoc/toc.json" target="_blank" rel="noopener">Hybrid setup</a>?</li>
	<li>is there any need for <a href="https://docs.microsoft.com/en-us/microsoftteams/cloud-voice-landing-page" target="_blank" rel="noopener">Cloud voice</a>?</li>
	<li>Need <a href="https://docs.microsoft.com/en-us/microsoftteams/training-microsoft-teams-landing-page" target="_blank" rel="noopener">training</a> on Teams?</li>
</ul>
<p style="text-align:justify;"><strong>References</strong></p>

<ul style="text-align:justify;">
	<li>Teams <a href="https://docs.microsoft.com/en-us/microsoftteams/limits-specifications-teams">Limits</a></li>
	<li><a href="https://docs.microsoft.com/en-us/microsoftteams/security-compliance-overview">Security </a>on Teams</li>
	<li><a href="https://support.office.com/en-us/article/empower-your-small-business-with-remote-work-9b91a85a-39b4-40a6-a590-0f9bea0ba8e6?ui=en-US&amp;rs=en-CA&amp;ad=CA" target="_blank" rel="noopener">Empower your small business</a> with remote work.</li>
</ul>
<p style="text-align:justify;">Need a Microsoft Office 365, Teams and Azure specialist? <a href="mailto:thiago.beier@gmail.com?subject=Contact.">Get in touch</a>.</p>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
