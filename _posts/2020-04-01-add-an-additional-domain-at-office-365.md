---
layout: post
title: Add an additional domain at Office 365
date: 2020-04-01 23:57
author: beierca
comments: true
categories: [chat, DNS, domains, Microsoft Teams, Office365, public dns]
---
Hi there

If you need add a new domain in Office 365 please continue to read this article.

Why would you need to add new domain to office 365?
<ul>
	<li>If you are migrating your on-premises e-mail domains to Office 365</li>
	<li>If you are enabling Microsoft Teams only on cloud to enable your Company to work from home at this COVID-19 moment.</li>
</ul>
<strong><span style="color:#ff0000;">TIP!</span></strong> - you don't need to migrate mailboxes to have Teams functioning on your company.

Can I have multiple users from different Office 365 hosted domains talking to each other on Microsoft Teams? <span style="color:#ff0000;"><em>YES you can.</em></span>

<strong>Steps</strong>

Log at <a href="https://portal.office.com">https://portal.office.com</a> and go to Home \ Settings \ Domains

Click on <strong>Add</strong> domain

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/123.png" />

<strong>Add</strong> the domain name (FQDN: full qualified domain name) for the domain to be added or migrated to your Office 365 subscription. Click <strong>Next</strong>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/124.png" />

Click on <strong>Verify</strong> and click on More Options

For my domain Office 365 recognizes it as hosted in GoDaddy (and GoDaddy accepts Office 365 to make all changes needed if you allow it and log with your GoDaddy admin account).

Enter your GoDaddy credentials (proceed with sign-in credentials)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/125.png" />

on Active Records, click <strong>Continue</strong>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/126.png" />

On the "Add DNS records" click on Configure to have all DNS entries added to your Public DNS Zone.
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/127.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/128.png" />

Confirm GoDaddy access and click Connect.
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/129.png" />

Wait for setup to complete.
When setup is complete click done.
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/130.png" />

&nbsp;

Check the main screen at <strong>Home \ Settings \ DNS</strong> for thew new domain added.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/131.png" />

<strong>Reference</strong>

<a href="https://docs.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide">https://docs.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide</a>

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
