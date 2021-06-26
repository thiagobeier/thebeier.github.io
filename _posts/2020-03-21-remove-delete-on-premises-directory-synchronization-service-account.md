---
layout: post
title: Remove / Delete On-Premises Directory Synchronization Service Account
date: 2020-03-21 12:00
author: beierca
comments: true
categories: [Active Directory, Azure, Azure AD, Office365, Powershell, syncronization, Uncategorized]
---
Hi There

Even if you're doing LABs, PoC (Proff of conceps) or rolling Azure AD connect (AD sync) on production sometimes you might face the follow error message:
<div class="ms-Persona-primaryText primaryText-934" dir="auto"></div>
<div class="ms-Persona-tertiaryText tertiaryText-936" dir="auto">
<div class="flyoutHeaderStyle-886">Delete user failed</div>
<div class="flyoutBodyStyle-887">We couldn't delete this account: Sync_SRV-DC01_8f0a01761ef9@tecbis.onmicrosoft.com. This is your directory synchronization account and you'll have synchronization failures if it's deleted.</div>
</div>
&nbsp;

<strong>To fix this do the following:</strong>

Connect to your Office 365 Tenant using PowerShell

$msolcred = get-credential

connect-msolservice -credential $msolcred

Disable directory synchronization. To do this, type the following cmdlet, and then press Enter:
<pre class="sbody-pre">Set-MsolDirSyncEnabled –EnableDirSync $false</pre>
Check that directory synchronization was fully disabled by using the Windows PowerShell. To do this, run the following cmdlet periodically:
<div class="indent">
<pre class="sbody-pre">(Get-MSOLCompanyInformation).DirectorySynchronizationEnabled</pre>
</div>
This command will return <strong class="uiterm">True</strong> or <strong class="uiterm">False</strong>. Continue to run this periodically until it returns <strong class="uiterm">False</strong>, and then go to the next step.

<span class="text-base">Note</span> It may take 72 hours for deactivation to be completed. The time depends on the number of objects that are in your cloud service subscription account.
<pre>Remove-MsolUser -UserPrincipalName Sync_SRV-DC01_8f0a01761ef9@tecbis.onmicrosoft.com</pre>
Refresh, and the user will have moved to "deleted users."  You can delete it from there, or leave it alone and left Azure kill it off in 30 days.

<strong>Re-enable Directory Synchronization</strong>

To re-enable directory synchronization, run the following cmdlet:
<div class="indent">
<pre class="sbody-pre">Set-MsolDirSyncEnabled -EnableDirSync $true</pre>
</div>
<em><strong>Reference</strong></em>

https://support.microsoft.com/en-ca/help/2619062/you-can-t-manage-or-remove-objects-that-were-synchronized-through-the

https://docs.microsoft.com/en-us/previous-versions/azure/jj151815(v=azure.100)?redirectedfrom=MSDN

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
