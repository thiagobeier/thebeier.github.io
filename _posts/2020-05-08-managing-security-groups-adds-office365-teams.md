---
layout: post
title: Managing Security Groups (ADDS, Office365, Teams & Licensing)
date: 2020-05-08 12:30
author: beierca
comments: true
categories: [Active Directory, ADDS, Azure, Azure AD, Management, Microsoft Teams, Office365, Powershell, security group]
---
Hi there

In this post I'd like to show you how we can automate ADDS synced security groups membership in order to have an additional security group used to assign permissions on Teams (Who can create office 365 groups and team on Teams - check <a href="https://thiagobeier.wordpress.com/2020/05/04/microsoft-teams-allow-create-teams/" target="_blank" rel="noopener">here</a>).

Domain has 03 security groups

<strong>E1-collab-lic</strong>: all users assigned for E1 licenses (with Teams)

<strong>E3-collab-lic</strong>: all users assigned for E3 licenses (with Teams)

<strong>O365_Teams_Mgmt</strong>: all users from E1-collab and E3-collab that will have access to create Office 365 Groups and Teams on Teams. - check article to set this group its proper permission.

<strong>Prepare our sandbox environment</strong>
<ol>
	<li>Install a fresh VM (2 cpu, 4 gb ram, 40 GB OS disk)</li>
	<li>Install a Domain Controller domain: <strong>thebeier.local</strong></li>
	<li>Give it internet access</li>
	<li>Install Azure AD connect latest version - from <a href="https://www.microsoft.com/en-us/download/details.aspx?id=47594" target="_blank" rel="noopener">here</a>.</li>
	<li>Create the an OU, Security Groups and users for this LAB using the powershell below.
<pre>#create OU, group, users , add users to e1, e3 licenses

New-ADOrganizationalUnit -Name "Groups" -Path "DC=thebeier,DC=local"

New-ADGroup -Name "O365_Teams_Mgmt" -SamAccountName O365_Teams_Mgmt -GroupCategory Security -GroupScope Global -DisplayName "Allow users to manage teams" -Path "OU=Groups,DC=thebeier,DC=local" -Description "Members of this group are Teams' team and channel Administrators"

New-ADGroup -Name "E1-Collab-lic" -SamAccountName E1-Collab-lic -GroupCategory Security -GroupScope Global -DisplayName "Assign E1-Collab licenses" -Path "OU=Groups,DC=thebeier,DC=local" -Description "E1-Collab"

New-ADGroup -Name "E3-Collab-lic" -SamAccountName E3-Collab-lic -GroupCategory Security -GroupScope Global -DisplayName "Assign E3-Collab licenses" -Path "OU=Groups,DC=thebeier,DC=local" -Description "E3-Collab"

New-ADUser -Name user04 -SamAccountName user04 -DisplayName user04 -path "OU=Groups,DC=thebeier,DC=local" -Description "E3-Collab"

New-ADUser -Name user05 -SamAccountName user05 -DisplayName user05 -path "OU=Groups,DC=thebeier,DC=local" -Description "E1-Collab"

add-ADGroupMember -Identity E3-Collab-lic -Members user04

add-ADGroupMember -Identity E1-Collab-lic -Members user05</pre>
</li>
	<li>Open dsa.msc ADUC - Active directory users and computer to check your AD structure
<ol>
	<li>check OU</li>
	<li>check Groups</li>
	<li>check Users' group membership</li>
</ol>
</li>
</ol>
<strong>Retrieving</strong> users members from E1-collab and E3-collab and adding them to O365_Teams_Mgmt security group.
<pre>#Add-ADGroupMember -Identity "O365_Teams_Mgmt" -Member $_

$users = Get-ADGroupMember -Identity E1-Collab-lic
$users.count
$users.samaccountname | foreach {
write-host -ForegroundColor Yellow "adding user $_ to Group"
Add-ADGroupMember -Identity "O365_Team_Mgmt" -Members $_
}

$users = Get-ADGroupMember -Identity E3-Collab-lic
$users.count
$users.samaccountname | foreach {
write-host -ForegroundColor Yellow "adding user $_ to Group"
Add-ADGroupMember -Identity "O365_Teams_Mgmt" -Members $_
}

$users = Get-ADGroupMember -Identity O365_Team_Mgmt
$users.count</pre>
<span style="color:#ff0000;"><strong>TIP!</strong></span> - What If?
If a user is removed from E1-collab-lic or E3-collab-lic groups this user should be removed from O365_Teams_Mgmt group as well. - <a href="https://github.com/thiagobeier/scripts/tree/master/27" target="_blank" rel="noopener">download here</a>.

For more script check my <a href="https://github.com/thiagobeier/scripts" target="_blank" rel="noopener">Github repo</a>.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>

&nbsp;
