---
layout: post
title: Azure - IAAS + SQL
date: 2020-07-03 12:00
author: beierca
comments: true
categories: [Administration, Automation, Azure, IAAS, IaC, Terraform, visual Studio Code]
---
<p><!-- wp:paragraph --></p><p>Hi there</p><p>in this article I'll demonstrate how to spin up a SQL server 2019 Standard version on Azure IAAS on a standard VM (Windows 2019 from marketplace).</p><p><strong>Setup your environment</strong></p><p>I used this Terraform <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/sqlsrv/main.tf" target="_blank" rel="noopener">main.tf </a></p><p>Quick review</p><ol><li>download Terraform from <a href="https://www.terraform.io/downloads.html" target="_blank" rel="noopener">https://www.terraform.io/downloads.html</a></li><li>edit your Windows PATH variable to point to your terraform main folder (I have a main folder for Azure deployments with a folder on C:\TERRAFORM\ where I extract my Terraform downloaded file into)</li><li>quick commands<ol><li>az login</li><li>terraform init</li><li>terraform plan -out myplanName</li><li>terraform apply myplanName</li><li>follow up your console output to check for any warnings, errors and its deployment</li><li>terraform destroy</li></ol></li></ol><p>Today's challenge is: Add a data disk to the SQL vm</p><p>Let's work on this on <a href="https://github.com/thiagobeier/blogchallenge" target="_blank" rel="noopener">github repository</a></p><p>download SQL trial from <a href="https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2019" target="_blank" rel="noopener">https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2019</a> to continue your SQL on IAAS setup.</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p>Reference<br /><br /></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>