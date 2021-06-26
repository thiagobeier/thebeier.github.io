---
layout: post
title: Microsoft Teams - PowerShell
date: 2020-04-23 15:00
author: beierca
comments: true
categories: [Administration, MFA, Microsoft Teams, Office365, Powershell, Tips]
---
Hi there

At this post I'm sharing a default script I've used to connect to Microsoft Teams &amp; Office 365 on my daily basis tasks.

If your organization has Azure AD compliance settings enabled enforcing <strong>MFA</strong> for all Global Admins you'll have to go through the MFA logon process 5 (five) times to get connected. Click <a href="https://docs.microsoft.com/en-us/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps">here</a> and <a href="https://docs.microsoft.com/en-us/microsoft-365/enterprise/multi-factor-authentication-microsoft-365-test-environment?view=o365-worldwide">here</a> to learn more about MFA &amp; Office / Exchange Online.

Use <a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/connect-o365-win-server.ps1.txt" target="_blank" rel="noopener"><strong>this PowerShell</strong> </a>command if you're installing all modules and running from a <strong>Windows Server 2016 or 2019</strong>.

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/6.png" target="_blank" rel="noopener"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/6.png" /></a>

Use <a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/connect-o365-win10.ps1.txt" target="_blank" rel="noopener"><strong>this PowerShell</strong></a> command if you're installing all modules and running from a Windows 10.

<a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/7.png" target="_blank" rel="noopener"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/7.png" /></a>

Those <a href="https://github.com/thiagobeier/scripts/tree/master/25" target="_blank" rel="noopener">scripts</a> are also available the my <a href="https://github.com/thiagobeier/scripts" target="_blank" rel="noopener">GitHub</a> repository.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
