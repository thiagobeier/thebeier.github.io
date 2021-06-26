---
layout: post
title: Microsoft Teams - Allow Team Creation
date: 2020-05-04 13:00
author: beierca
comments: true
categories: [Azure AD, channel, creation, Microsoft Teams, Office365, Powershell, Security, security group, team]
---
Hi there

In this article I'm demonstrating how to lockdown Teams creation to a specific Security Group member.

This will allow you to keep your deployment clean once by default every user enabled on Microsoft Teams has team's creation access.

<strong><span style="color:#ff0000;">WARNING:</span> Checking if your organization already has this implemented
</strong>
<pre>#Connect-AzureAD
$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
(Get-AzureADDirectorySetting -Id $settingsObjectID).Values

$allgroupinfo = (Get-AzureADDirectorySetting -Id $settingsObjectID).Values
$groupid = $allgroupinfo[9].Value
Get-AzureADGroup -ObjectId $groupid | fl displayname</pre>
<strong>Output</strong>
<ul>
	<li>check the following
<ul>
	<li>EnableGroupCreation</li>
	<li>GroupCreationAllowedGroupId
(try to copy and paste this group in Azure AD group - check the result)</li>
</ul>
</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/14.png" />

<strong>Fresh Setup</strong>

<strong>Go to Office 365 Home \ Groups</strong> and create a new security group (that can be done under Azure AD Groups)
<ul>
	<li>type: security</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/1.png" />

<strong>click next</strong>

Give the group a Name and a Description
<ul>
	<li><strong>name</strong>: AllowCreateTeams</li>
	<li><strong>description</strong>: member users can teams &amp; channels at Microsoft Teams</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/2.png" />

<strong>click next</strong>

at Review and finish group adding, select create group

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/3.png" />

wait for the group to be created and filter for its name under groups

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/4.png" />

&nbsp;

<strong>add all users</strong> that will be able to create teams &amp; channels to this group
<ul>
	<li>edit the group</li>
	<li>search for the users and click add then save then close</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/8.png" /><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/5.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/6.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/7.png" />

check the group members

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/9.png" />

run the following powershell logged on Office365, Teams, Azure AD
<pre>$GroupName = "AllowCreateTeam"
$AllowGroupCreation = "False"

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
$template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
$settingsCopy = $template.CreateDirectorySetting()
New-AzureADDirectorySetting -DirectorySetting $settingsCopy
$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
$settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
}
else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values</pre>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/11.png" />

<strong>Testing</strong>
<ul>
	<li>log with a user that is not member of this group</li>
	<li>you should not be able to see the option to create Team</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/12.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/1/13.png" />

<span style="color:#ff0000;"><strong>TIP</strong></span>: by default teams &amp; channels has no CODE then you cannot join or guess its codes.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
