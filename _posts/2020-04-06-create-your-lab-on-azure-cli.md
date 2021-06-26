---
layout: post
title: Create your LAB on Azure (CLI)
date: 2020-04-06 12:59
author: beierca
comments: true
categories: [Azure, azure resources, Powershell, resource group, Tags]
---
Hi there

If you're like anybody else who likes to optimize your work trying to automate your LABs I hope this article might be helpful. Following you have a couple PowerShell commands to have your own lab ready to go.

<strong>Steps</strong>

1. Create your Free Azure Account - <a href="https://azure.microsoft.com/en-ca/free/">link</a>

2. Install all required <a href="https://docs.microsoft.com/en-us/powershell/azure/install-az-ps?view=azps-3.7.0">PowerShell</a> modules on your PC (make sure you already have <a href="https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7">Powershell</a> on your system)
<pre>Install-Module -Name Az -AllowClobber</pre>
OR you can log on Azure Portal and use the Azure Cloud Shell

Log on Azure portal <a href="https://portal.azure.com">https://portal.azure.com</a>

<strong>Launch the Azure Cloud shell</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/120.png" />

3. Creating your "<strong>Demo1</strong>" Azure Resource Group on "CanadaCentral" location
<pre>New-AzResourceGroup -Name Demo1 -Location "<strong>canadacentral</strong>"</pre>
4. Creating your Storage account at "<em>CanadaCentral</em>" location with Standard_GRS SKUName
<pre>New-AzStorageAccount -ResourceGroupName <strong>Demo1</strong> -AccountName <strong>mystorageaccount01001</strong> -Location <strong>canadacentral</strong> -SkuName Standard_GRS</pre>
5. Adding tags to your Azure Resource Group (Tag Names: Dept and Environment with following values: IT and PROD)
<pre>$tags = @{"<strong>Dept</strong>"="<strong>IT</strong>"; "<strong>Environment</strong>"="<strong>PROD</strong>"}
$resourceGroup = Get-AzResourceGroup -Name <strong>Demo1</strong>
New-AzTag -ResourceId $resourceGroup.ResourceId -tag $tags</pre>
6. Adding tags to your Azure Resource items (Azure Resources)
<pre>$tags = @{"<strong>Dept</strong>"="<strong>IT</strong>"; "<strong>Environment</strong>"="<strong>PROD</strong>"}
Get-AzResource -ResourceGroupName Demo1 | foreach { 
Write-Host $_.ResourceName $_.Tags 
New-AzTag -ResourceId $_.ResourceId -Tag $_.Tags }</pre>
7. Clearing all Azure Resources' tags (it only clears azure resources item's tags.
<pre>#Clear all TAGS (that are not enforced by Azure Policy from a Azure Resource Item)
#This script doesn't clear azure policy enforced tags 
Get-AzResource -ResourceGroupName Demo1 | foreach {
Write-Host $_.ResourceName
$_.Tags
Update-AzTag -ResourceId $_.ResourceId -Tag $_.Tags -Operation Delete
}</pre>
You should have something similar to this

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/141.png" />

Now you have your first Azure Lab to play around #Enjoy it.
<p style="text-align:center;"><strong>[<a href="https://thiagobeier.youcanbook.me/">Book Me</a>]</strong></p>
thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
