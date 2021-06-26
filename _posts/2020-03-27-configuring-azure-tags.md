---
layout: post
title: Configuring Azure Tags
date: 2020-03-27 12:00
author: beierca
comments: true
categories: [Azure, gui, setup, Tags, Tips]
---
Hi there

In this post I'll demonstrate how to check if your Azure Resources have Tags implemented and how to add tags to them.

<em>Tags can be used to identify different Azure Resource Groups, Azure Resources and Subscriptions as well for costing analysis based on different LOB (Line of Business).</em>

Go to your Azure subscription (don't have one? - register for <a href="https://azure.microsoft.com/en-ca/free/">free</a>)

Go to your Azure Resource Group then pick the Azure Resource to be focus of this article

Pick or create an Azure Storage Account for this demo.

<strong>Adding tags</strong> to our Azure Resource Group
<ul>
	<li>add tag <strong>name</strong>: environment</li>
	<li>add tag <strong>value</strong>: demo</li>
	<li>add tag <strong>name</strong>: owner</li>
	<li>add tag <strong>value</strong>: Thiago B.</li>
	<li>add tag <strong>name</strong>: costcenter</li>
	<li>add tag <strong>value</strong>: IT</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/118.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/119.png" />

Let's add the following tags to our Azure Resource (a resource withing Azure Resource Group)
<ul>
	<li>add tag name: <strong>expireOn</strong></li>
	<li>add tag value: <strong>2020-03-23</strong> (YYYY-MM-DD format)</li>
</ul>
This setup will allow us to demonstrate how to cleanup Azure Resources at this <strong><a href="https://thiagobeier.wordpress.com/2020/03/27/azure-automation-account-tags-and-runbook/">article</a></strong>. (coming soon)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/106.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/107.png" />

&nbsp;

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
