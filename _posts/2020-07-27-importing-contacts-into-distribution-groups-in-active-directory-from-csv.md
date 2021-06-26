---
layout: post
title: Import Contacts into Distribution Groups in Active Directory from CSV file.
date: 2020-07-27 01:31
author: beierca
comments: true
categories: [Active Directory, Administration, Automation, contacts, Powershell]
---
<p><!-- wp:paragraph --></p><p>Hi there</p><p>Continuing the series from the articles</p><ol><li>A</li><li>B</li><li>C</li></ol><p>we're now on the last part: Importing all contacts identified as user@emaildomain.com in the column "E" at the CSV file</p><p>as we did before the script reads the CSV file</p><p>retried all column "E" data and uses arrays to list the email addresses then it adds the Contact Prefix (check the github repository) to it to check if the contact exists in ADDS before we add it to the designed DG (Distribution Group) from column "A"</p><p>have in mind that we exported all groups and its members to separate files with the following convention:</p><ul><li>GroupName.txt (content: all members on each line from column "E" on the CSV file)</li></ul><p>&nbsp;</p><p>CSV file format</p><p>Script #4</p><p>&nbsp;</p><p>References</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>
