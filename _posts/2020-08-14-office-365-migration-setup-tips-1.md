---
layout: post
title: Office 365 - Migration & Setup tips #1
date: 2020-08-14 13:00
author: beierca
comments: true
categories: [Active Directory, Administration, Automation, Azure AD, DNS, Exchange Online, migration, Office365, Powershell]
---
<p><!-- wp:paragraph --></p><p>Hi there</p><p>This article it's to remind you to pay attention in a few items that would help you through each new Office 365 project or migration.</p><p>In addition to an Active Directory health check, IdFix and new UPN (userprincipalname) suffix that you need to cover on each single project please have also look at the following:</p><ol><li>have access do Public DNS services</li><li>have accounts with granted access to ADDS, Azure AD Connect and O365</li><li>export all ADDS users objects to CSV</li><li>export all Office 365 tenant users objects to CSV</li><li>Add e-mail address to all users from UPN (userprincipalname)</li><li>Add primary SMTP address from UPN (userprincipalname) + domain</li><li>Add SMTP aliases from &lt;tenantdomain&gt;.onmicrosoft.com and &lt;tenantdomain&gt;.mail.onmicrosoft.com domains</li><li>check if all users have email addresses</li><li>check if all users have proxyAddresses properly filled</li><li>convert shared mailboxes to regular user and assign licenses and set user's location: The other day that happened in a migration where all G-suite accounts were migrated over to O365 to shared  mailboxes where the client created a brand new ADDS forest and enabled sync with new username convention for new mailboxes and the migrated ones. However, we had the migration in process and we didn't want to interrupt G-suite to O365 migration and cause delays that's why we used shared mailboxes.</li></ol><p>If you need clear all ProxyAddresses with the following script (target a specific OU) to not harm your ADDS environment.</p><pre class="prettyprint prettyprinted"><span class="typ">#Create a file.csv with all username, samaccountname with header SAM on column A<br />Import</span><span class="pun">-</span><span class="typ">Module</span> <span class="typ">ActiveDirectory</span>
<span class="typ">Import</span><span class="pun">-</span><span class="typ">Csv</span><span class="pln"> file.csv</span> <span class="pun">|</span> <span class="typ">ForEach</span><span class="pun">-</span><span class="typ">Object</span> <span class="pun">{</span> <span class="typ">Set</span><span class="pun">-</span><span class="typ">AdUser</span> <span class="pun">-</span><span class="typ">Identity</span><span class="pln"> $_</span><span class="pun">.</span><span class="pln">SAM </span><span class="pun">-</span><span class="typ">Clear</span> <span class="typ">ProxyAddresses</span> <span class="pun">}</span></pre><p>References</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>