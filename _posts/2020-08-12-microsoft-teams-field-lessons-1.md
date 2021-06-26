---
layout: post
title: Microsoft Teams – field lessons #1
date: 2020-08-12 13:00
author: beierca
comments: true
categories: [Microsoft Teams]
---
<p><!-- wp:paragraph --></p><p>Hi there</p><p><img class="aligncenter" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" /></p><p>This short article it's to show how to track if pilot users got their migration from islands to Teams Only finished properly.</p><p>With the migration list on hands create a CSV with User Name (column A) and Email address (column B) and use the following script to check the Meeting Migration Status for all users.</p><pre>foreach ($user in import-csv .\pilot-users.csv) {<br />Get-CsMeetingMigrationStatus | where {$_.UserPrincipalName -eq $user.email} | select userprincipalname,state<br />}</pre><p>You can also track this trying this</p><pre>Get-CsMeetingMigrationStatus | where {$_.UserPrincipalName -eq 'teams.test2@thebeier.com'} <br />Get-CsMeetingMigrationStatus | where {$_.UserPrincipalName -eq 'teams.test2@thebeier.com'} | select userprincipalname,state<br />Get-CsMeetingMigrationStatus| Where {$_.State -eq "Failed"}| Format-Table UserPrincipalName,LastMessage</pre><p>References</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>
