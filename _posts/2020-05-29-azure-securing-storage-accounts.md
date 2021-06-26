---
layout: post
title: Azure -  Securing storage accounts
date: 2020-05-29 13:00
author: beierca
comments: true
categories: [Azure, azure powershell, azure resources, firewall, Powershell, Security, storage account, Tips, Troubleshooting]
---
<p style="text-align:justify;">Hi there</p>
<p style="text-align:justify;">Did you know that Storage accounts on Azure come with Firewall disabled by default allowing external access (any to storageaccountname)? Before you ask me, that doesn't happen with <a href="https://aws.amazon.com/premiumsupport/knowledge-center/secure-s3-resources/" target="_blank" rel="noopener">AWS</a>.</p>
<p style="text-align:justify;">What about to fix 100 storage accounts by hand. <a href="https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security#grant-access-from-an-internet-ip-range" target="_blank" rel="noopener">Powershell</a> can assist you on that.</p>
<p style="text-align:justify;">If you're running Azure Storage accounts on Production, UAT or DEV keep an eye on it.</p>
<p style="text-align:justify;"><strong>Go to your <a href="https://portal.azure.com" target="_blank" rel="noopener">Azure Portal</a></strong></p>
<p style="text-align:justify;">Search for Storage accounts on Home \ All services if that's not pinned already.</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/storageaccounts/2.png" />
<p style="text-align:justify;">Go on each storage account and click on Firewalls and virtual networks under settings</p>
<p style="text-align:justify;">You should see "allow access from" set to All networks (default option)</p>
<p style="text-align:justify;"><span style="color:#0000ff;"><strong>Fixing manually</strong></span></p>
<p style="text-align:justify;">Change to <strong>selected networks</strong></p>
<p style="text-align:justify;"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/storageaccounts/1.png" /></p>
<p style="text-align:justify;"></p>
<p style="text-align:justify;"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/storageaccounts/5.png" /></p>
<p style="text-align:justify;"><strong>Explore</strong> the following options:</p>

<ul style="text-align:justify;">
	<li>
<div><strong>+ Add existing virtual network</strong></div>
<ul>
	<li>select from the list all VNETS that you need to associate to this storage account allowing access to it</li>
</ul>
</li>
	<li>
<div><strong>+ Add new virtual network</strong></div>
<ul>
	<li>add / create a new VNET that you'll associate to this storage account allowing access to it</li>
</ul>
</li>
	<li>
<div><strong><span style="color:var(--color-text);">Firewall</span></strong></div>
<ul>
	<li>
<div><span style="color:var(--color-text);">Add IP ranges to allow access from the internet or your on-premises networks.</span><span style="color:var(--color-text);">  (if you need to lock this down to an Internet IP address - your home ip address for example) <span style="color:#ff0000;"><strong>TIP</strong></span>: it always detect your current internet ip address - check yours at <a href="https://www.ipchicken.com" target="_blank" rel="noopener">IPChicken</a></span></div></li>
</ul>
</li>
</ul>
<p style="text-align:justify;"><span style="color:#0000ff;"><strong>Fixing using powershell</strong></span></p>
<p style="text-align:justify;"><em>Coming soon.</em></p>
<p style="text-align:justify;">I'm still working on a script to do this by subscription, resource groups and its associated VNETs. Client's production, uat or dev environments after deployed it will have a high complexity around naming convention for azure resources as well as for the required ones for this task: VNETs, subnets and storage accounts names.</p>
Checking usign AZ CLI

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/storageaccounts/7.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/storageaccounts/8.png" />

<strong>Reference</strong>

<a href="https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security</a>
<a href="https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security#grant-access-from-an-internet-ip-range" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security#grant-access-from-an-internet-ip-range</a>

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
