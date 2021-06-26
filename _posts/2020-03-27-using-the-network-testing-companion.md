---
layout: post
title: Using the Network Testing Companion
date: 2020-03-27 16:52
author: beierca
comments: true
categories: [adoption, howto, Microsoft Teams, migration, Office365, Tips, Troubleshooting]
---
Hi again

Are you having issues troubleshooting Microsoft Teams deployment? Please check the following questions to lead your troubleshooting matrix:
<ol>
	<li>Are you using Cloud-based users only? (When users are 100% on-cloud)</li>
	<li>Are you using Synced Users to Office 365?</li>
	<li>Are you using Synced Users to Office 365 with Mailboxes on-premises (Exchange On-Premises or Hybrid with no Mailboxes on Office365)?</li>
	<li>Do you also have Skype for Business Server deployed?</li>
</ol>
Regardless of the answer for the questions above use the Network Testing Companion to evaluate your MS Teams infrastructure.

Download the Network Testing Companion from the <a href="https://www.powershellgallery.com/packages/NetworkTestingCompanion/1.5.4">PowerShell Gallery</a>.

Open a PowerShell as Administrator and Run:

Install-Module -Name NetworkTestingCompanion

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/81.png" />

Check your Desktop or Start Menu on Windows 10

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/86.png" />

Run the Network Testing Companion tool. (<strong>Click Start</strong>)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/82.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/83.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/84.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/85.png" />

Check the results and look for:

<strong>a. SSL certificate error.</strong>

<span style="color:#ff0000;"><strong>FIX:</strong></span> Review Office 365 DNS entries for your registered domains. If you're not migrating e-mails at this moment but is migrating MS Teams and there's an Exchange On-Premises with Hybrid setup you can skip Exchagne On-Line portion at this moment.

<strong>b. Network issues: bandwidth, latency, jitter.</strong>

<span style="color:#ff0000;"><strong>FIX</strong></span>: review QoS, Firewalls (IPS, IPS filters), Endpoint Protection and ISP internet links download and upload usage (last month report).

Reference

<a href="https://docs.microsoft.com/en-us/microsoftteams/use-network-testing-companion">https://docs.microsoft.com/en-us/microsoftteams/use-network-testing-companion</a>

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
