---
layout: post
title: Managing Office 365 licenses (assign license)
date: 2020-03-17 13:00
author: beierca
comments: true
categories: [Administration, azuread, Identity Management, Licensing, Office365, Powershell, subscription]
---
Hi there

If you don't have Azure AD P1 or P2 this article it's addressed to you.

Here you can find what you need to export users’ current license status E1, E3 and ATP and how to assign licenses to them.

First of all, connect to your Office 365 Subscription with the following commands:
<pre>Connect-ExchangeOnline
Connect-AzureAD
Connect-MsolService</pre>
Then you can list all available licenses available under your Office 365 subscription
<pre>Get-MsolAccountSku

Get-AzureADSubscribedSku | Select SkuPartNumber</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/52.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/51.png" />

<strong>Retrieving user's license</strong>
<pre>Get-MsolUser -UserPrincipalName thiago@thebeier.com | Format-List DisplayName,Licenses</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/54.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/56.png" />

<strong>Export to CSV all Enterprise E3 licensed users</strong>
<pre>Get-MsolUser -All | Where-Object {($_.licenses).AccountSkuId -match "ENTERPRISEPACK"} | Out-file C:\temp\EnterpriseE3Users.csv</pre>
<strong>Export to CSV all Standard E1 licensed users</strong>
<pre>Get-MsolUser -All | Where-Object {($_.licenses).AccountSkuId -match "STANDARDPACK"} | Out-file C:\temp\StandardE1Users.csv</pre>
<strong>Export to CSV all Enterprise ATP licensed users</strong>
<pre>Get-MsolUser -All | Where-Object {($_.licenses).AccountSkuId -match "ATP_ENTERPRISE"} | Out-file C:\temp\EnterpriseATPUsers.csv</pre>
<strong>Assigning ATP licenses to E1 and E3 users.</strong>
<pre>Get-MsolUser -All | Where-Object {($_.licenses).AccountSkuId -match "ENTERPRISEPACK"} | Set-MsolUserLicense -AddLicenses "tenant:ATP_ENTERPRISE"</pre>
<pre>Get-MsolUser -All | Where-Object {($_.licenses).AccountSkuId -match "STANDARDPACK"} | Set-MsolUserLicense -AddLicenses "tenant:ATP_ENTERPRISE"</pre>
<strong>Assigning ATP licenses to users</strong>
<pre>#assign license
$userUPN="thiago@thebeier.com"
$planName="ATP_ENTERPRISE"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign</pre>
<span style="color:#ff0000;">Tip! - <span style="color:#000000;">You can assign any license to several users at the same time importing users from a txt or CSV file as well. <a href="https://gallery.technet.microsoft.com/Office365-Assign-ATP-96d0f49f">Download here</a>.</span></span>

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
