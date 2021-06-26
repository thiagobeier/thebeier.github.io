---
layout: post
title: Microsoft Teams - Pilot tips #1
date: 2020-08-03 12:00
author: beierca
comments: true
categories: [Administration, Management, Microsoft Teams, Office365, pilot, project management]
---
<p><!-- wp:paragraph --></p><p style="text-align:justify;">Hi there</p><p><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/teamsevents.jpg" /></p><p style="text-align:justify;">With the covid-19 pandemic we have seen home users, companies and government working hard to follow along with with all needs and changes that this moment has brought to us globally. One of the biggest challenges it's to keep people working from home with security, collaboration using great technologies and Microsoft Teams is playing an important role for everyone regardless of  if a user is coming from a competitor or even Skype for Business Server and Online version. Therefore, conduct pilot it's a crucial phase no each and every Microsoft Teams projects no matter the size of your company.</p><p style="text-align:justify;">If you're conducting a Microsoft Teams pilot you should have in mind a few pillars:</p><ul style="text-align:justify;"><li><strong>User experience</strong>: it's always about user. It's because of them, for them and through them that technologies are continuously improving and growing and spreading fast and that's why it's so important to communicate, train and hear from them through the Alpha test &amp; Pilot what are their expectation and feedback on each and every item, feature and place they go on Teams on their daily basics.</li><li><strong>Security</strong>: guaranteeing that your data (company, personal, client, partner, etc.) is safe and being accessed by whose suppose to it's one of the biggest challenge for every company selling technology nowadays and that's not different with Microsoft Teams. It bring a lot of features, policies and integrations with Microsoft platforms such as its own Office 365 but Azure and hybrid ones.</li><li><strong>Usability</strong>: every great technology brings with it a lot of features that allows uses to access from PC, Mac, iOS, Android and web and with it different features are released and available for different devices types and versions which makes your user test cases checklist bigger but needed if you continue to achieve excellence delivering your project no matter of its size.</li></ul><p style="text-align:justify;">Fist of all, for user experience hand out clear documents and communications  targeting each people on each stage of the project you're in. Make sure that the user understand what's coming by training them ahead, talking about the new technology that's being adopted and give them tool to report their experience such as a SharePoint site to report bugs, finding and complaints. The same can be done with Microsoft Forms with Power Automate.</p><p style="text-align:justify;">Secondly, for Security make sure you have licensed all feature and services at Microsoft Office365, Azure AD (Premium P1 or P2) as well as ATP (Advanced Threat Protection) that integrated with OneDrive and SharePoint will bring your entire project and company into a new era on consuming cloud-based services. All of those recommendations needs to work and follow along with security policies and 2FA (two-factor authentication) &amp; MFA (multi factor authentication) features provided by Microsoft to improve users' security.</p><p style="text-align:justify;">Finally about the pillars, talking about usability make sure you're not giving too much different technologies to your users that they can't keep up with. Otherwise, they'll get bored, frustrated and unmotivated having to learn too much about the tools they need to have their work done. Microsoft Teams users' experience it's also based their roles within Teams based on the device they're using for the right task they need. Live Events it's better managed on PC and Mac as an organizer than on a smart phone or tablet.</p><p style="text-align:justify;">Furthermore, a great and simple example of conducting a pilot it's to define which policies are gonna be put in place in the company on Production that can be piloted by each persona on a Microsoft Teams project. Live Events policy can define who can initiate (book and deliver) Live Events within the organization (by default everyone is enabled) and most of the companies disable it and create a custom policy for that. Another policy that it's commonly changed / created are the App setup policies, that define which Teams apps users will have pinned for them when using Microsoft Teams and which Microsoft or third-party apps are also pinned and allowed to them to use within Teams. Where when you do not target a massive amount of users to custom policies Microsoft Teams pushes all Default (ORG-wide) policies by default to all users enabled on Teams. Based on client's requirements you can easily use the following to conduct a simple Pilot as tasks:</p><ol><li>Validate the list of users provided by CLIENT's Team: <em>who's being targeted in the Pilot</em></li><li>Create, validate and send out all end-users / targeted users communications</li><li>Remove the Teams license from all users (Powershell) -<em> if O365 hasn't been deployed to entire organization only</em></li><li>Add Teams license for your test users (Powershell or O365 Admin - if number of users is very small)</li><li>Export current users license status (Office 365, Teams): <em>always save o previous stage to roll back to it if needed</em></li><li>Export current users App setup policies and Live events policies assigned to all users:<pre><em>Get-CsOnlineUser | Where-Object {$_.TeamsMeetingBroadcastPolicy -ne $null} |Sort-Object -Property TeamsMeetingBroadcastPolicy | select DisplayName, TeamsMeetingBroadcastPolicy | Out-GridView</em></pre></li><li>Assign Teams users to Pilot Policies: app setup policy and live event policy (Teams Admin Portal / Powershell)</li><li>Set Pilot users to TeamsOnly mode (Powershell): <span style="color:#ff0000;">this takes longer to apply</span><pre><em>Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity teams.test2@thebeier.com</em></pre></li><li>Proceed with Pilot users basic tests: (where P: Pass, F: failed)</li></ol><ul><li style="list-style-type:none;"><ul><li>User is able to log on Teams Client (flat client, VDI, smart phone, tabled and web client)? P/F</li><li>User is able to check its Outlook calendar at <a href="https://portal.office.com">https://portal.office.com</a>? P/F</li><li>User is able to see previous existing / booked meetings (created as Skype for business meetings) showing up as Teams Meetings? P/F</li><li>User is able to edit/delete/forward meetings now in Teams \ Calendar? P/F</li><li>User is able to reproduce all tests on VDI? P/F</li><li>User is able to reproduce all tests on iOS device? P/F</li><li>User is able to reproduce all tests on Android device? P/F</li><li>User is able to reproduce all tests on Mac device? P/F</li><li>User is able to reproduce all tests on Windows device? P/F</li></ul></li></ul><ol><li>Your company Migration Team to report back to CLIENT's Project Team</li><li>Email Notification to Users not Successfully Migrated</li><li>Report back any failures</li><li>Open the Bridge for Support with Microsoft Vendor / Technical Support</li><li>Decision on Go No Go with NEXT PROJECT PHASE</li></ol><p style="text-align:justify;"> </p><p>References<br /><a href="https://docs.microsoft.com/en-us/microsoftteams/pilot-essentials" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/microsoftteams/pilot-essentials</a></p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thanks,</p><p><!-- /wp:paragraph -->

<!-- wp:paragraph --></p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p><!-- /wp:paragraph --></p>