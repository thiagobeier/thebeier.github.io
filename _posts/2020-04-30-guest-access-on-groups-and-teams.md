---
layout: post
title: Guest Access on Groups and Teams
date: 2020-04-30 15:00
author: beierca
comments: true
categories: [Azure, Groups, Management, Microsoft Teams, Office365, Powershell, Reports]
---
Hi there

At this post I'm covering Guest access on <strong>Office 365 Groups</strong> and <strong>Teams</strong>.

I want to share with everyone some findings that could prove helpful to customers who are trying to limit Guest Access capabilities to their Teams, but still having the option/opportunity to have Guest Access for specified Teams.

Make sure you're connected to <a href="https://technet.microsoft.com/en-us/library/jj984289(v=exchg.160).aspx" target="_blank" rel="noopener noreferrer">Exchange Online PowerShell</a> and <a href="https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0" target="_blank" rel="noopener noreferrer">Azure AD PowerShell</a> in order to run the steps below.

In order to have this done, there are a <strong>few things </strong>that need to be made:
<ol>
	<li>Export all UG (Unified Groups) current settings to CSV (use as report and for tracking changes) - follow the <strong>TIPs #1</strong> and <strong>#2</strong> at this article for improving your reports.</li>
	<li>Must enable Guest Access from Azure AD</li>
	<li>Must enable Guest Access for Office 365 Groups in the O365 Groups Service &amp; Addins portal.</li>
	<li>Must enable Guest Access for Microsoft Teams in the Teams Service &amp; Addins portal or under Org-wide settings \ Guest access menu <a href="https://admin.teams.microsoft.com/company-wide-settings/guest-configuration">https://admin.teams.microsoft.com/company-wide-settings/guest-configuration</a></li>
	<li>Set all Groups/Teams to 'AllowToAddGuests' to $false
Set a specific Group/Team to $True or $False for Allowing Guest Access</li>
	<li>Remove previous settings and set all Groups and Teams back to Allow Guest Access</li>
	<li>Validate all changes made above for Guest Access to $True or $False for all Groups and Teams</li>
</ol>
<strong><span style="color:#ff0000;">TIP #1 - Export all current UG settings to CSV.</span></strong>

Script content
<pre>$Groups = Get-UnifiedGroup
$Groups | ForEach-Object {
$group = $_
New-Object -TypeName PSObject -Property @{
Group = $group.DisplayName
PrimarySMTPAddress = $group.PrimarySMTPAddress
AllowAddGuests = $group.AllowAddGuests
DisplayName = $group.DisplayName
WhenCreated = $group.WhenCreated
WhenChanged = $group.WhenChanged

}
} | Export-CSV "C:\temp\Office365-UG-info.csv" -NoTypeInformation -Encoding UTF8</pre>
&nbsp;

<strong><span style="color:#ff0000;">TIP #2 - Work with the CSV file to get the better of it.</span></strong>
<ol>
	<li>Use the script provided and run against your Office 365 Tenant</li>
	<li>Open the exported csv file expand all columns</li>
	<li>add one more column on far right and name it "Less than 3 characters"</li>
	<li>copy the formula "=LEN(<strong><span style="color:#ff0000;">D2</span></strong>)&lt;3" not the and past it at the 2nd row (change the "<span style="color:#ff0000;"><strong>D2</strong></span>" cell reference according to your need and paste on all cell affected by your working COLUMN</li>
	<li>you can all cut and paste the <span style="text-decoration:underline;">WhenCreated</span> column to close / before the <span style="text-decoration:underline;">WhenChanged</span> to make easy or searches within this control file</li>
	<li>Now you're ready to use your filters to:
<ol>
	<li>list Groups allowing guest access (true / false)</li>
	<li>list Groups that contains less than 3 characters on its name
<ol>
	<li>you can highlight the searched cells to make easy to identify them when filters are disabled (your you can use <em>Conditional Formatting</em> on Excel to do so).</li>
</ol>
</li>
	<li>check when a Group was created and modified</li>
</ol>
</li>
</ol>
&nbsp;

<strong>References</strong>

https://support.office.com/en-us/article/adding-guests-to-office-365-groups-bfc7a840-868f-4fd6-a390-f347bf51aff6?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_usepowershell&amp;PickTab=Manage

&nbsp;

Thanks and I hope you liked this post.
Please share it or reach me out for suggestions

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>

&nbsp;

&nbsp;
