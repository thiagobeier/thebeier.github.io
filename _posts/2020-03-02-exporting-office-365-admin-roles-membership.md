---
layout: post
title: Exporting Office 365 Admin Roles membership
date: 2020-03-02 06:30
author: beierca
comments: true
categories: [Administration, Exchange &amp; Office Server, export from portal, export to csv, Office365, roles membership]
---
Hi there

In this post I'm covering how to export Office 365 Role Members to CSV
<h4 id="view-role-groups">View role groups</h4>
<h4 id="use-the-eac-to-view-role-groups">Use the EAC to view role groups</h4>
<ol>
	<li>In the EAC, go to <strong>Permissions</strong> &gt; <strong>Admin Roles</strong>. All of the role groups in your organization are listed here.</li>
	<li>Select a role group. The Details pane shows the <strong>Name</strong>, <strong>Description</strong>, <strong>Assigned roles</strong>, <strong>Members</strong>, <strong>Managed by</strong>, and <strong>Write scope</strong> of the role group. You can also see this information by clicking <strong>Edit</strong> <img src="https://docs.microsoft.com/en-us/exchange/exchangeonline/media/itpro_eac_editicon.png" alt="Edit icon" />.</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/roles/1.png" />
<em><strong>Exported result (csv file)
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/roles/2.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/roles/3.png" />

You can export the same using PowerShell. Please fell free <a href="https://gallery.technet.microsoft.com/office/O365-Export-Roles-from-2e2f6565">this amazing script</a> from <a href="http://twitter.com/jerryyasir">Jerry Yasir</a> available at my Technet Gallery <a href="https://gallery.technet.microsoft.com/Export-Office365-User-a8060592">repository</a>.

<strong><span style="color:#ff0000;">Tip!</span></strong>

When you run any not signed PowerShell script you'll be prompted the following error message "Powershell file cannot be loaded" please set the execution policy before you run it.
<pre>Set-ExecutionPolicy -ExecutionPolicy Unrestricted</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/roles/4.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/roles/5.PNG" />

<strong>Reference</strong>
https://docs.microsoft.com/en-us/exchange/permissions-exo/role-groups
https://gallery.technet.microsoft.com/office/O365-Export-Roles-from-2e2f6565

Thanks,

<strong>Thiago Beier</strong>
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
