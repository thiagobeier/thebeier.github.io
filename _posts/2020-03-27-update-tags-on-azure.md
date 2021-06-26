---
layout: post
title: Update tags on Azure
date: 2020-03-27 16:50
author: beierca
comments: true
categories: [Automation, Azure, azure cloud shell, Powershell, Tags, Tips]
---
<span class="hljs-variable">Hi there</span>

<span class="hljs-variable">in this post I'm demonstrating how to update Azure Tags using PowerShell - Azure Cloud Shell</span>

update Azure Tags for a Azure Resource Group
<pre>#blog post update tags
$tags = @{"<strong>Department</strong>"="<strong>IT</strong>"; "<strong>Environment</strong>"="<strong>Devtest</strong>"}
$Resources = Get-AzResource | where-object { $_.resourcegroupname -eq "<strong>Demo2</strong>"}
$thisrgid = "/subscriptions/340e6a31-b9ab-42ac-a930-d120c92300b8/resourceGroups/Demo2"
Update-AzTag -ResourceId $resource.id -Tag $tags -Operation Merge</pre>
update Azure Tags for a Azure Resource Object
<pre>#blog post update tags
$tags = @{"<strong>Department</strong>"="<strong>IT</strong>"; "Environment"="<strong>Devtest</strong>"}
$Resources = Get-AzResource | where-object { $_.resourcegroupname -eq "<strong>Demo2</strong>" | select xXXXXXXXX}
$thisrgid = "/subscriptions/340e6a31-b9ab-42ac-a930-d120c92300b8/resourceGroups/Demo2"
Update-AzTag -ResourceId $resource.id -Tag $tags -Operation Merge</pre>
&nbsp;

Reference

<a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources">https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources</a>

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
