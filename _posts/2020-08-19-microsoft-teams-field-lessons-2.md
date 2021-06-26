---
layout: post
title: Microsoft Teams – field lessons #2
date: 2020-08-19 13:30
author: beierca
comments: true
categories: [Microsoft Teams]
---
<p><!-- wp:paragraph --></p>
<p style="text-align:justify;">Hi there</p>
<p style="text-align:center;"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" /></p>
<p style="text-align:justify;">This short article it's to show how to track all Office 365 users Teams Upgrade Effective Mode. Run this before you start your pilot phase to have all users' previous mode just in case you need to them back.</p>
<p style="text-align:justify;">The following script uses Skype for Business module - check <a href="https://github.com/thiagobeier/scripts/tree/master/25" target="_blank" rel="noopener">here</a> at my GitHub repository for a script to automate this step if you need or follow along with the script below.</p>
<pre>#connect SFB module<br />Install-Module SharePointPnPPowerShellOnline -Force<br />$sfbSession = New-CsOnlineSession<br />Import-PSSession $sfbSession -AllowClobber<br />Enable-CsOnlineSessionForReconnection<br /><br />#teams upgrade mode report<br />Get-CSOnlineUser | select UserPrincipalName, teamsupgrade* | ConvertTo-Html | Out-File "TeamsUpgrade.html"<br />Get-CSOnlineUser | select UserPrincipalName, teamsupgrade* | ConvertTo-Csv -NoTypeInformation | Out-File "TeamsUpgrade.csv"</pre>
<ul>
<li style="text-align:justify;">the script saves a TeamsUpgrade.html file with the report on current directory</li>
<li style="text-align:justify;">the script saves a TeamsUpgrade.csv file with the report on current directory</li>
</ul>
<p>&nbsp;</p>
<p>References<br />https://docs.microsoft.com/en-us/microsoftteams/teams-only-mode-considerations</p>
<p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p>
<p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p>
<p>Thanks,</p>
<p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p>
<p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p>
<p><!-- /wp:paragraph --></p>
