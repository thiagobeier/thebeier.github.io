---
layout: post
title: Microsoft Teams – field lessons #3
date: 2020-08-26 13:30
author: beierca
comments: true
categories: [Microsoft Teams]
---
<p><!-- wp:paragraph --></p><p>Hi there</p><p><img class=" aligncenter" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" /></p><p>This short article it's to show how to track if pilot users got their licenses assigned properly.</p><p>The following script will pull out all users with TEAMS enabled for them.</p><ul><li>saves on TEAMS.txt (current directory)</li><li>shows on screen (gridview format)</li></ul><pre>Connect-msolservice<br />$all = Get-MsolUser -All<br />$teamsUsers = foreach ($user in $all) {<br />$serviceStatuses = @($user.Licenses.ServiceStatus)<br />$teamsPlans = $serviceStatuses.Where({$_.ServicePlan.ServiceName -clike "*TEAMS*"})<br />if ($true -in $teamsPlans.ForEach({$_.ProvisioningStatus -like "*Success*"})) {<br />$user<br />}<br />}<br /><br />$teamsUsers | Out-File TEAMS.txt<br />$teamsUsers | Out-GridView</pre><p>References</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>
