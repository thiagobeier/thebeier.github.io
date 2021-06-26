---
layout: post
title: Microsoft Teams - Powershell #3
date: 2020-05-06 13:00
author: beierca
comments: true
categories: [Microsoft Teams, Powershell, Reports]
---
Hi there

In this post I'm sharing a couple more powershell scripts and routines to help you out on Microsoft Teams deployment and management.

<strong>Script #1</strong> - Export all Teams Application Setup policy report by users assigned to each policy create <em>some policies takes time to report after they're created</em>. This option is not available on Teams Admin Portal at this moment. You can check by user individually (click on each user and check its policies) or click on teams app setup policy and try to add a member and that'll show if the user you're searching for belongs to a group or is empty.
<pre>#count
$a = (Get-CsOnlineUser -Filter {teamsappsetuppolicy -eq 'Profile3'} | Select UserPrincipalName).count
$b = (Get-CsOnlineUser -Filter {teamsappsetuppolicy -eq 'Profile1-Collab'} | Select UserPrincipalName).count
$c = (Get-CsOnlineUser -Filter {teamsappsetuppolicy -eq 'Profile2-limited'} | Select UserPrincipalName).count
$d = (Get-CsOnlineUser -Filter {teamsappsetuppolicy -eq 'App-Setup-Policy-01'} | Select UserPrincipalName).count

write-host -ForegroundColor Cyan $a "Users with Profile3"
write-host -ForegroundColor Green $b "Users with Profile1-Collab"
write-host -ForegroundColor Yellow $c "Users with Profile2-limited"
write-host -ForegroundColor magenta $d "Users with App-Setup-Policy-01"</pre>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/16.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/17.png" />

Download this script from <a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/script-count-users-per-policy.txt">here</a>.

<strong>Script #2</strong> - export all users with Teams licensed under your Office 365 tenant based on its service plan and service name "TEAMS1"
<pre>Get-MsolUser -All | Where-Object { $_.Licenses.ServiceStatus.ServicePlan.ServiceName -match "TEAMS1"} | Select-Object UserPrincipalName, DisplayName</pre>
<strong>Script #3</strong> - Retrieve Azure AD Group members and export to a TXT file. (you can use it in other tasks)
<pre>$group = Get-AzureADGroup -SearchString "E3-group"
$members = Get-AzureADGroupMember -ObjectId 5835c436-c1e1-496b-ab76-6b59bedd6a7c -All $true | Where-Object {$_.ObjectType -eq "User"}
$members1 = $members.userprincipalname
$members1 | Out-File all-e3-group.txt -Encoding utf8</pre>
<strong>Script #4</strong> - Add a user to the group "E3-group" - you need the Azure AD Group ID before you run this command.
<pre>Get-AzureADGroup -SearchString "E3-group"
get-msoluser thiago_teams_test@thebeier.com Get-AzureADUser -ObjectId
Add-AzureADGroupMember -ObjectId "a4b38f3f-1478-4204-b60e-cbf683f0e00a" -RefObjectId</pre>
<strong>Script #5</strong> - check if a user on a specific Azure AD Group has a Teams Application Setup Policy assigned to it.
<pre>$group = Get-AzureADGroup -SearchString "E3-group"
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}
$members1 = $members.userprincipalname
$members1 | foreach {
$User = (Get-CsOnlineUser -Identity $_).teamsappsetuppolicy
If ($User -ne $Null) { 
write-host -ForegroundColor green "User $_ has $user policy assigned"
#$User
} Else {
write-host -ForegroundColor red "User $_ has no policy assigned"
}
}</pre>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/18.png" />

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>

&nbsp;
