---
layout: post
title: Azure Portal  - Views
date: 2020-04-09 14:57
author: beierca
comments: true
categories: [Administration, Automation, Azure, azure resources, azure tags, business, Tags, Tips]
---
Hi there

Recently to automate some tasks we used a full export from Azure Resources. You can view and export its views by Subscription if you want to keep each Azure Resource Groups and its items (Azure Resources) separate from each other.

To facilitate your management go to Azure Portal and select or search for Home \ All Resources then you go to Manage View menu and select "<strong>Edit Columns</strong>"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/142.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/143.png" />

A new blade will open on the right side of the screen then you'll be able to add the following items to the view:
<ul>
	<li>Resource Group ID</li>
	<li>Resource ID</li>
	<li>Resource Type</li>
	<li>Subscription ID (you only need to have this on your view if you want to see all Azure Resources and its subscriptions on the same view, screen or export)</li>
</ul>
Select each item one at a time and move to the right column and click apply when you're finished.

Now you can see all information on the same screen.

Select <strong>Export to CSV</strong> and open it to see how is its disposal.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/144.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/145.png" />

<strong>Applicability</strong>
<ul>
	<li>You can check, update, delete TAGs on each resource by ResourceID
<span style="color:#ff0000;"><strong>TIP!</strong></span> - You might have issues to update TAGs on Azure Resources (items) retrieving its information only by Resource Name. It would be better by ResourceID</li>
	<li>If you company already have hundreds or thousands Azure Resources (items) please define your Business Tag Policy and enforce by policy on the Azure Resource Groups (for Cost Analysis) and use the exported CSV file to add more columns to the right of the exported file to relate to each TAG you might need to make changes on.
<strong><span style="color:#ff0000;">TIP!</span></strong> - This is a complex and exhaustive task that unfortunately someone needs to define, add the tags and review it before using PowerShell to make changes on all Azure Resources at once.

[caption id="" align="alignnone" width="1311"]<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/149.png" width="1311" height="171" /> Click to larger[/caption]</li>
</ul>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
