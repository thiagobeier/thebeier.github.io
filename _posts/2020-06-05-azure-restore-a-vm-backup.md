---
layout: post
title: Azure - Restore a VM backup
date: 2020-06-05 13:00
author: beierca
comments: true
categories: [ASR, Azure, backup, Backup &amp; Restore, restore, Tips, validation]
---
<p><!-- wp:paragraph --></p><p style="text-align:justify;">Hi there</p><p style="text-align:justify;">Do you have a backup policy in place in your <a href="https://azure.microsoft.com/en-us/services/backup/" target="_blank" rel="noopener">Azure</a> subscription protecting your VMs?</p><p style="text-align:justify;">Have you ever tried to restore a backup on a scheduled windows to make sure your data is ok?</p><p style="text-align:justify;">Some companies for Quality assurance and validation will request a specific vm or application to be restored and tested on a separate environment. Which you can achieve with <a href="https://azure.microsoft.com/en-us/services/site-recovery/" target="_blank" rel="noopener">ASR - Azure Site Recovery</a>.</p><p style="text-align:justify;">Let's go over this in this article</p><ol style="text-align:justify;"><li>Confirm that you have a back up in place</li><li>Confirm that your VM is being backed up</li><li>Restore the VM or its disk contents to validation</li></ol><p style="text-align:justify;"><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><strong>References<br /></strong>https://docs.microsoft.com/en-us/azure/backup/tutorial-backup-vm-at-scale</p><p>&nbsp;</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>
