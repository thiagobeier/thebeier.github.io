---
layout: post
title: Create tags on Azure (Azure Cloud Shell)
date: 2020-03-27 16:47
author: beierca
comments: true
categories: [Automation, Azure, azure cloud shell, Powershell, Tips]
---
Hi again

This post it's to demonstrate how to create the Azure Tags on a Resource Group as well as on an Azure Resource (stogare account) using PowerShell using Azure Cloud Shell.

You need the Azure Resource ID from the Azure Resoure Group you're applying the changes (adding tags)

The following command will add the following tags to the Azure Resource Group "<strong>RG-TOR-DEVTEST-BI</strong>"

tag name: Department
tag value:IT
tag name:Environment
tag value:Devtest

<strong><span style="color:#ff0000;">TIP!</span></strong> - change the "<strong>$thisrgid</strong>" variable from "<strong>12345678-ab12-b9ab-az01-s390-123456789asd</strong>" to your Azure Resource Group ID
<pre>$tags = @{"Department"="IT"; "Environment"="Devtest"}
$Resources = Get-AzResource | where-object { $_.resourcegroupname -eq "RG-TOR-DEVTEST-BI"}
$thisrgid = "/subscriptions/<strong>12345678-ab12-b9ab-az01-s390-123456789asd</strong>/resourceGroups/RG-TOR-DEVTEST-BI"
New-AzTag -ResourceId $thisrgid -Tag $tags</pre>
Log on Azure portal <a href="https://portal.azure.com">https://portal.azure.com</a>

<strong>Launch the Azure Cloud shell</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/120.png" />

Copy and paste the PowerShell command(s) on the Azure Cloud Shell screen and hit enter.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/89.png" />

Check the results using Azure Portal

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/121.png" />

<span style="color:#ff0000;"><strong>TIP!</strong></span> - Use the following command to retrieve all azure tags on your subscription.
<pre>#list your Azure Subscriptions
<strong>get-azsubscription</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/122.png" />

#set your current Azure Subscription 
<strong>Set-AzContext -SubscriptionName "Disaster Recovery (DR)"</strong>

#list all tags on current environment / subscription
<strong>az group list --query [].tags</strong></pre>
Reference

<a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources">https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources</a>

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
