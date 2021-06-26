---
layout: post
title: Error deleting a Teams Application Policy
date: 2020-05-03 10:00
author: beierca
comments: true
categories: [Administration, app setup policy, Management, Microsoft Teams, policy, Powershell]
---
Hi there

This post is quick and you'll learn how to delete a Teams Application Policy from your Teams deployment.

<strong>Log on Teams Admin Portal</strong>

Go to <a href="https://admin.teams.microsoft.com/policies/app-setup" target="_blank" rel="noopener">https://admin.teams.microsoft.com/policies/app-setup</a>

select the app setup policy you want to delete

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/1.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/2.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/3.png" />

if you get access denied with the following content "<span style="color:var(--color-text);">The policy "Profile3" is currently assigned to one or more users. You must assign a different policy to those users before you can delete this policy.</span><span style="color:var(--color-text);">"</span>

use this command to retrieve which users have this policy assigned to
<pre>Get-CsOnlineUser -Filter {teamsappsetuppolicy -eq "Tag:Profile3"} | Select UserPrincipalName</pre>
<strong>Output expected</strong>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/4.png" />

go to <strong>Users</strong> tab on <strong>Teams Admin Portal</strong>

search for the user "tgermano@collabcan.com"

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/5.png" />

click on policies or at the user name

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/6.png" />

then select Policies on the user , find the App setup policy named "Profile3"

click on "EDIT" at Assigned policies

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/7.png" />

click on the right menu and find App setup policy

scroll down and pick a different policy (suggestion: default policy) and click apply

go back to Teams App setup policy tab

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/8.png" /><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/9.png" />

you will see the message "We assigned the policies. It might take a few minutes for you to see these changes.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/10.png" />

select the policy name "Profile3" and hit delete

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/11.png" />

check the green messa "Item was deleted". Now the policy is gone.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8/12.png" />

now the policy has been deleted properly (no error). However, if the policy doesn't go away git it Teams Admin Portal some time and try again after a few minutes.

I hope that helped you.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>

&nbsp;

&nbsp;
