---
layout: post
title: Upgrade Azure AD Connect
date: 2020-05-05 13:00
author: beierca
comments: true
categories: [Administration, Azure AD, Tips, upgrade]
---
Hi there

In this article I'm showing how to upgrade in place your Azure AD connect
You can export of profiles before running the upgrade or snapshot the virtual server
You can also have a second server ready to go at Staging mode if this one broken.

Old / current Version: <strong>1.4.38.0</strong>
New version: <strong>1.5.29.0</strong>
<ol>
	<li>check the Azure AD connect current version
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/1.png" /></li>
	<li>download the new version from <a href="https://www.microsoft.com/en-us/download/details.aspx?id=47594">here</a>.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/2.png" /></li>
	<li>go to downloads folder and run the AzureADConnect.msi file.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/3.png" /></li>
	<li>The setup will ask to upgrade the current version
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/4.png" /></li>
	<li>click upgrade to proceed and wait
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/5.png" /></li>
	<li>Enter your office 365 global admin credentials and click next
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/6.png" /></li>
	<li>wait for the setup to connect and load its information
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/8.png" /></li>
	<li>on Ready to configure screen, leave the option "Start the synchronization process when configuration completes." selected and click <strong>Upgrade</strong>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/9.png" /><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/10.png" /></li>
	<li>When migration is complete you'll see the "Configuration complete" screen, click exit.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/11.png" /></li>
	<li>check under windows key \ Azure AD Connect for the following apps:
- Azure AD connect
- Synchronization rules editor
<strong>- Synchronization Service: <span style="color:#ff0000;">run this one to make sure all settings are ok.</span></strong>
- Synchronization service webservice
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/adconnect/12.png" /></li>
</ol>
<strong>Reference</strong>

https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-roadmap#install-azure-ad-connect
https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-topologies

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
