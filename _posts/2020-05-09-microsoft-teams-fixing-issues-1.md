---
layout: post
title: Microsoft Teams - Fixing issues #1
date: 2020-05-09 14:00
author: beierca
comments: true
categories: [Administration, fix, howto, issues, Management, microsoft, Microsoft Teams, Office365, Tips]
---
Hi there

In this post I'll cover some issues that we faced and how to fix it based on its symptoms

Error deploying <strong>Teams Workload</strong> - What is this?, This is also know as <a href="https://docs.microsoft.com/en-us/microsoftteams/use-advisor-teams-roll-out" target="_blank" rel="noopener">Advisor for Teams</a>.

How to get in there?
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/13.png" />
<strong>Error #1</strong>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/9.png" />

<strong>Fix</strong>

go to Teams Admin Portal \ Teams Apps \ Permissions policies \ Global (edit)

Change Microsoft apps from "Block all appo" to "Allow all apps"

<span style="color:#ff0000;"><strong>Cause</strong></span>: Some your organizations block all Microsoft Apps by default and this feature "Advisor for Teams" will deploy a Team with a few Microsoft apps on it so you can follow up your Microsoft Teams project deployment from there if Microsoft apps are blocked it will fail.

<em>before</em>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/10.png" />

<em>after</em>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/11.png" />

Then switch back to Advisor for Teams and try to proceed with its deployment
<ul>
	<li>select the assignment and click next (NEXT is not greyed anymore)</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/14.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/15.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/16.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/17.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/18.png" />

<span style="color:#ff0000;"><strong>TIP</strong></span>: sometimes after you apply the fix it gets stuck at this phase. Give it a few hours and re-run. Microsoft is being hammed by the spike usage on its technologies and that's causing delays, GUI errors and powershell timeout on the past month.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/A/22.png" />

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
