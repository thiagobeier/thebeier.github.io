---
layout: post
title: Microsoft Teams - Check who can create Microsoft 365 Groups / Team and Channels
date: 2020-09-21 22:45
author: beierca
comments: true
categories: [Administration, Azure AD, export to csv, Microsoft Teams, News, Powershell, security group, Tips]
---
<p><img class="aligncenter" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" /> Hi there Today I'm walking you through the Microsoft Teams script to check who can create Microsoft 365 Groups We use security groups (Azure AD synced) or Azure AD dynamic groups (cloud based) to control who can create a Team on Microsoft Teams That doesn't mean a user can't join a Team clicking on a request or with a code. You should use this as part of any deployment where you have a controlled environment. Otherwise, you'll find hundreds of Teams and Office 365 Groups created in your M365 tenant.  </p>
<blockquote>################################################################</blockquote>
<blockquote># Author Thiago Beier thiago.beier@gmail.com</blockquote>
<blockquote># Version: 1.0 - 2020-09-21</blockquote>
<blockquote>#</blockquote>
<blockquote># Check which Group members can create team on Microsoft based on article https://docs.microsoft.com/en-us/microsoft-365/solutions/manage-creation-of-groups?view=o365-worldwide</blockquote>
<blockquote># Exports log to %workdir% .log extension</blockquote>
<blockquote># Exports group members (users and nested group names) to csv</blockquote>
<blockquote># Toronto, CANADA</blockquote>
<blockquote># Email: thiago.beier@gmail.com</blockquote>
<blockquote># https://www.linkedin.com/in/tbeier/</blockquote>
<blockquote># https://twitter.com/thiagobeier</blockquote>
<blockquote># https://thiagobeier.wordpress.com</blockquote>
<blockquote>################################################################</blockquote>
<blockquote>#CLIENT-NAME Teams data collection</blockquote>
<blockquote>#Connect-AzureAD</blockquote>
<blockquote>#create working dir change the directory if you need to change the output directory for .log and .csv files</blockquote>
<blockquote>$workdir = "c:\temp\teams\"</blockquote>
<blockquote>mkdir $workdir</blockquote>
<blockquote>$dt=get-date -format yyyy-MM-dd-hhmmss</blockquote>
<blockquote>Start-Transcript $workdir\CLIENT-NAME-Teams-log-$dt.log</blockquote>
<blockquote>$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id</blockquote>
<blockquote>(Get-AzureADDirectorySetting -Id $settingsObjectID).Values</blockquote>
<blockquote>#retrieve if CLIENT-NAME has a specific security group in use to control who can create Team/Channel on Teams</blockquote>
<blockquote>$findazureadgroup = ((Get-AzureADDirectorySetting -Id $settingsObjectID).Values| where {$_.name -like "GroupCreationAllowedGroupId"}).value</blockquote>
<blockquote>#retrieve azure ad group info Get-AzureADGroup -ObjectId $findazureadgroup #export users who have access to create Team and Channels</blockquote>
<blockquote>Get-AzureADGroupMember -ObjectId $findazureadgroup | select displayname,userprincipalname | export-csv $workdir\teams-lockdown-$dt.csv</blockquote>
<blockquote>stop-transcript</blockquote>
<blockquote>################################################################</blockquote>
<p>  Expected output</p>
<ul>
<li>GroupCreationAllowedGroupId = Azure AD Group ID </li>
<li>EnableGroupCreation = False (default is True)</li>
</ul>
<p>&nbsp;</p>
<p><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/TIPS/12.png" /></p>
<p>References</p>
<p>https://docs.microsoft.com/en-us/microsoft-365/solutions/manage-creation-of-groups?view=o365-worldwide</p>
<p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Thanks,</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Thiago Beier <a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p>
