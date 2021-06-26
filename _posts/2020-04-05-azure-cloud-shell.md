---
layout: post
title: Azure Cloud Shell
date: 2020-04-05 02:17
author: beierca
comments: true
categories: [Azure, azure CLI, azure cloud shell, azure powershell, bash, Management, Powershell, Storage]
---
Hi there

If you don't want to worry about having all required <em><strong>Azure PowerShell</strong></em> modules up to date in your PC you can use the Azure Cloud Shell to execute your tasks on Azure.

Azure Cloud Shell is an interactive, authenticated, browser-accessible shell for managing Azure resources.

To access it. Go to your Azure Portal

on the Right Top you have the Cloud Shell icon. (click on it)

This will requires an <strong>Azure Storage Account</strong> to store your profile with scripts, files, etc.

<span style="color:#ff0000;"><strong>WARNING</strong></span>: If the Azure Storage Account fails you're not a Global Administrator and you need to request proper access to complete this action.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azurecloudshell/azurecloudshell.PNG" />

After the Azure Console is loaded you choose between PowerShell or Bash style console.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azurecloudshell/azurecloudshell1.PNG" />

<strong>Basic Concepts</strong>
<ul>
	<li>Cloud Shell runs on a temporary host provided on a per-session, per-user basis</li>
	<li>Cloud Shell times out after 20 minutes without interactive activity</li>
	<li>Cloud Shell requires an Azure file share to be mounted</li>
	<li>Cloud Shell uses the same Azure file share for both Bash and PowerShell</li>
	<li>Cloud Shell is assigned one machine per user account</li>
	<li>Cloud Shell persists $HOME using a 5-GB image held in your file share</li>
	<li>Permissions are set as a regular Linux user in Bash</li>
</ul>
Want to know more how to use it?

Check this Article on how to <a href="https://thiagobeier.wordpress.com/2020/03/27/create-tags-on-azure-azure-cloud-shell/">Manage</a> Azure Tags with Azure Cloud Shell.

<strong>Reference </strong>

https://docs.microsoft.com/en-us/azure/cloud-shell/overview
<p style="text-align:center;"><strong>[<a href="https://thiagobeier.youcanbook.me/">Book Me</a>]</strong></p>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
