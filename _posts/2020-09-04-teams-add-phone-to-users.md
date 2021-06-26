---
layout: post
title: Teams: add phone to users.
date: 2020-09-04 13:00
author: beierca
comments: true
categories: [Microsoft Teams, phone, users]
---
<!-- wp:paragraph -->
<p><img class="size-medium aligncenter" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teams.jpg" width="300" height="250" /></p>
<p>Hi there In this article we're adding phone to users that allows them to make and receive calls to PSTN using a local DID. Prerequisites</p>
<ul>
<li>have a Microsoft 365 Phone System - Virtual User available for E3 users (E5 users don't need this)</li>
<li>have a Microsoft 365 Domestic Calling Plan for E3 or E5 users available</li>
<li>assign Microsoft 365 Phone System - Virtual User available to your E5 users</li>
<li>assign Microsoft 365 Domestic Calling Plan to E3 and E5 users (if you currently manage licenses through Azure AD you need to enable it there)</li>
</ul>
<p>Go to Teams Admin Portal</p>
<ol>
<li>Add an Emergency Address pointing to your location
<ol>
<li>go to Locations \ Emergency Address \ Add (+) https://admin.teams.microsoft.com/locations</li>
</ol>
</li>
<li>Add a phone number (buy it)
<ol>
<li>go to Voice \ phone numbers https://admin.teams.microsoft.com/phone-numbers</li>
<li>click on (+) add</li>
<li>you might need to escalate Microsoft PSTN support team if you're running with issues adding phone to users after you have entered your location properly
<ol>
<li>ERROR: The address or location you selected doesn't have any area codes available. Please check the number of licenses you have or contact <a class="ms-Link Link__root___hQfZs link__apLink___2FU1J link__light___2m8u9  Link__isEnabled___28Tws" title="Microsoft customer support" href="https://docs.microsoft.com/en-US/microsoftteams/manage-phone-numbers-for-your-organization/contact-pstn-service-desk?WT.mc_id=TeamsAdminCenterCSH" target="_blank" rel="noopener noreferrer">Microsoft customer support</a>.</li>
</ol>
</li>
<li>you may have to use the <strong>Skype Legacy Portal</strong> (Teams Admin Center \ Legacy Portal) located on bottom left of your screen at the Teams Admin Center</li>
</ol>
</li>
</ol>
<p>&nbsp;</p>
<p>After Microsoft customer supported is escalated it takes a few hours to pick the proper available locations and numbers by location and prefix that you'll be presented Microsoft will add that to you. Please check this process running the following command "<i>Get-CsOnlineTelephoneNumber | Where-Object {$_.ActivationState -cnotcontains “Activated”} | fl *</i>" When this portion is finished you can go back to the Phone and they'll be there</p>
<p>I prefer to ckeck if the numbers were added this way "<i>Get-CsOnlineTelephoneNumber | fl *</i>"</p>
<p>You'll see them there with a different city code and location because it was added by Microsoft Support landing on proper location where Microsoft has available phone numbers to sell.</p>
<p>TIPs</p>
<ul>
<li>to minimize licensing on your environment check the https://docs.microsoft.com/en-us/microsoftteams/business-voice/whats-business-voice</li>
<li>to transfer numbers to Microsoft Teams check here https://docs.microsoft.com/en-us/microsoftteams/phone-number-calling-plans/transfer-phone-numbers-to-teams</li>
</ul>
<p>References</p>
<p><strong>Check my <a href="https://github.com/thiagobeier/scripts/blob/master/README.md">Github</a> repository</strong></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Thanks,</p>
<!-- /wp:paragraph -->
<p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p>
