---
layout: post
title: Azure- Reset local Windows password
date: 2020-05-18 12:30
author: beierca
comments: true
categories: [Administration, Azure, azure resources, new user in azuer IAAS VM, password reset, Security, security log]
---
Hi there

in this article I'll demonstrate how to reset the VM user password from Azure Portal.

Did you know that if you don't even know the admin you can still reset a user password for a new user you define on this process?

<em><span style="color:#ff0000;">YES you can!</span></em>

If you enter any user name that is not present on the VM you're trying to "reset" its password Azure extension will create this new user, will add this user to the local administrators group and set its password to not expire and allow you to gain remote access to the VM.

<strong>Resetting user's password from Azure Portal</strong>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/5.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/6.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/35.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/7.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/8.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/10.png" />

&nbsp;

<strong>Resetting user's password from PowerShell</strong>
<pre>$SubID = "&lt;SUBSCRIPTION ID&gt;" 
$RgName = "&lt;RESOURCE GROUP NAME&gt;" 
$VmName = "&lt;VM NAME&gt;" 
$Location = "&lt;LOCATION&gt;"

Connect-AzAccount 
Select-AzSubscription -SubscriptionId $SubID 
Set-AzVMAccessExtension -ResourceGroupName $RgName -Location $Location -VMName $VmName -Credential (get-credential) -typeHandlerVersion "2.0" -Name VMAccessAgent</pre>
<strong>net user &lt;enter&gt;</strong> : allows you to check how many users are created on this VM

Event viewer \ security logs will keep all changes made by the Azure Extension. Check below

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/12.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/11.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/17.png" />

<strong>References</strong>

https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/features-windows?toc=/azure/virtual-machines/windows/toc.json

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
