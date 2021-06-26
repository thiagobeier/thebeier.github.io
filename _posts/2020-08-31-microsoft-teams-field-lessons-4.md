---
layout: post
title: Microsoft Teams – field lessons #4
date: 2020-08-31 13:00
author: beierca
comments: true
categories: [Microsoft Teams, Tips]
---
<p></p>

<!-- wp:paragraph -->
</p><p>Hi there</p><p><img class="aligncenter" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" /></p><p style="text-align:justify;">Let me show you how to clear Teams Cache on Windows and MacOS if you need to troubleshoot: Skype only mode users not showing its status on Teams client.</p><p style="text-align:justify;">When you have a large environment where you have Skype users enabled on Office 365 and licensed on Teams at the same time you're running a Teams Pilot and your Tenant it's on islands mode you might experience issues. Check this post.</p><p style="text-align:justify;">In order to fix you MacOS, Windows PC (laptop, VDI host, vm, etc.) you can do the following:</p><ol><li style="text-align:justify;">Quit Microsoft Teams</li><li style="text-align:justify;">Delete the following directory/folder content:<br /><ul><li><strong>Windows</strong><br />%AppData%\Microsoft\Teams\</li><li><strong>Mac</strong><br />~/Library/Application Support/Microsoft/Teams/</li></ul></li><li style="text-align:justify;">Launch Microsoft Teams client again.</li></ol><p>Sometime, you might need to close Outlook client to have the entire folder cleared however, that didn't affected troubleshooting the main issue "Skype for Business user's status and interoperability".</p><p>References</p><p>https://answers.microsoft.com/en-us/msoffice/forum/all/ms-teams-login-problems/4f915ddd-151f-4e92-8d2a-11b876e50f8a</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
</p><p>Thanks,</p><p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
</p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p>
<!-- /wp:paragraph -->

<p></p>
