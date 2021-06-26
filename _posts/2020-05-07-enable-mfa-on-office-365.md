---
layout: post
title: Enable MFA on Office 365
date: 2020-05-07 13:00
author: beierca
comments: true
categories: [Administration, Automation, Azure AD, MFA, Office365, Powershell, Security]
---
Hi there

In this article I'm covering how to enable MFA for all users based on get-msoluser queries

<strong>First of all</strong> let's cover some basics on get-msoluser commands.

List all licensed users on your subscription
<p style="padding-left:40px;"><strong>Get-MsolUser -All | where {$_.isLicensed -eq $true}</strong></p>
List all unlicensed users on your subscription
<p style="padding-left:40px;"><strong>Get-MsolUser -All -UnlicensedUsersOnly</strong></p>
List all unlicensed users excluding #EXT# (Guests users) and *Sync* (Azure AD connect synchronization accounts)
<p style="padding-left:40px;"><strong>Get-MsolUser -All -UnlicensedUsersOnly | Where-Object {($_.userprincipalname -notlike "*EXT*") -and ($_.userprincipalname -notlike "*Sync*")}</strong></p>
List the same as previous by domain name that contains <em><strong>collabcan.com</strong></em>
<p style="padding-left:40px;"><strong>Get-MsolUser -All -UnlicensedUsersOnly | Where-Object {($_.userprincipalname -notlike "*EXT*") -and ($_.userprincipalname -notlike "*Sync*")} | Where-Object {$_.userprincipalname -like "*collabcan.com"}</strong></p>
Now that we're familiar with get-msoluser let's add our loop to grab user's UPN (userprincipalname)

<strong>Enable MFA for all licensed users.</strong>
<pre><strong># Eanble MFA
# Uncomment the line with $Set-Msoluser after you test this out</strong>

$users = Get-MsolUser -All | where {$_.isLicensed -eq $true} | Where-Object {($_.userprincipalname -notlike "*EXT*") -and ($_.userprincipalname -notlike "*Sync*")}
foreach ($user in $users)
{
$st = New-Object -TypeName Microsoft.Online.Administration.StrongAuthenticationRequirement
$st.RelyingParty = "*"
$st.State = "Enabled"
$sta = @($st)
write-host -ForegroundColor Cyan "working on user" $user.userprincipalname
<strong>#Set-MsolUser -UserPrincipalName $user -StrongAuthenticationRequirements $sta</strong>

}

<strong>#End</strong></pre>
<strong>Disable MFA for all licensed users.</strong>
<pre># Disable MFA for all licensed users (exclude SYNC and EXT)
$users = Get-MsolUser -All | where {$_.isLicensed -eq $true} | Where-Object {($_.userprincipalname -notlike "*EXT*") -and ($_.userprincipalname -notlike "*Sync*")}
foreach ($user in $users)
{
$st = New-Object -TypeName Microsoft.Online.Administration.StrongAuthenticationRequirement
$st.RelyingParty = "*"
$st.State = "Enabled"
$sta = @($st)
write-host -ForegroundColor Cyan "working on user" $user.userprincipalname
#Set-MsolUser -UserPrincipalName $user.userprincipalname -StrongAuthenticationRequirements @()
}
#End</pre>
Share if you liked it.

<strong>Reference</strong>
https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-userstates

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
