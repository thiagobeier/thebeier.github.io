---
layout: post
title: Azure Automation Account, Tags and Runbook
date: 2020-03-27 16:12
author: beierca
comments: true
categories: [Automation, Azure, Schedule, Tags]
---
Hi there

You can maintain your <strong>Azure Resources</strong> clean to avoid high billing invoices.

You will need the following:
<ol>
	<li><strong>Azure Tag</strong> flagging your Azure Resources with <strong>YYYY-MM-DD</strong> format</li>
	<li><strong>Azure Automation Account</strong></li>
	<li><strong>Schedule</strong></li>
	<li><strong>Azure Resource</strong> (i.e.: azure storage account with tag <strong>expireOn</strong> set to date you want to test)</li>
</ol>
<strong>Steps</strong>

Configure Azure Tags properly on the Azure Resource you're about to evaluate the following steps. - <strong>Check this article</strong>.

Create Azure Automation Account

Log on <strong>Azure Portal</strong> - <a href="https://azure.microsoft.com/en-ca/free/">create free account</a>

Go to the Azure Marketplace and search for "automation" and click on it

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/90.png" />

Create the Azure Automation Account

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/91.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/92.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/94.png" />

Create the Runbook

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/95.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/96.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/97.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/98.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/99.png" />

Paste the proper PowerShell script from <a href="https://dev.to/fboucheros">@Fboucher</a> - Great thanks for the awesome <a href="https://github.com/FBoucher/AzSubscriptionCleaner">PowerShell Script.</a>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/100.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/101.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/102.png" />

Create the Schedule

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/103.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/105.png" />

<span style="color:#ff0000;"><strong>TIP!</strong></span> Check the storage account before it is deleted by the Runbook.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/106.png" />

<span style="color:#ff0000;"><strong>TIP!</strong></span> Check the storage account (used to be deleted: it has the <strong>expireOn</strong> tag set on)
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/107.png" />

<strong>Import modules required</strong>

To import modules required first you need to save modules locally on your PC
<pre>#save modules offline
mkdir c:\temp\azure\modules\
Save-Module -Name Az.Accounts -Path c:\temp\azure\modules\
Save-Module Az.ResourceGraph -Path c:\temp\azure\modules\
Save-Module Az.Resources -Path c:\temp\azure\modules\</pre>
Compact each folder to module-name.zip
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/112.png" />

<strong>Now you are ready to import the modules</strong>

Go the the Modules under Runbook blade

select add module <strong>(+ add module)</strong>

At upload file (.zip format, 100 MB max size) and locate the folder c:\temp\azure\modules\

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/110.png" />

Import modules on the following order one after another
<ol>
	<li><em><strong>Az.Accounts</strong></em></li>
	<li><em><strong>Az.ResourceGraph</strong></em></li>
	<li><em><strong>Az.Resources</strong></em></li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/111.png" />

Wait for time and date scheduled to check the Runnbook execution

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/113.png" />

As you can see the first attempt failed on my LAB (I hadn't imported the PowerShell modules).

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/114.png" />

After I fixed the PowerShell modules import - the next schedule run without issues.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/115.png" />

Validate that the storage account has gone (<span style="color:#ff0000;"><strong>ATTENTION</strong></span>: wrong use of this script on production could cause a disaster). Have Backup policy and routine implemented (<a href="https://azure.microsoft.com/en-ca/services/site-recovery/">ASR</a> - Azure Site Recovery or <a href="https://docs.microsoft.com/en-us/azure/backup/backup-overview">Backup</a>)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/116.png" />
thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
