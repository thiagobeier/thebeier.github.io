---
layout: post
title: Add a new user on your Office 365 tenant (different email domain)
date: 2020-04-08 11:25
author: beierca
comments: true
categories: [Administration, Office365, password, template, user creation]
---
Do you know you can have different users on different email domains at Office 365?

If that's your need you can learn here how to add a new user to your Office 365 tenant logging with a different email domain or UPN (User Principal Name)

Pros:
<ul>
	<li>flexibility on managing your domains on Office 365</li>
	<li>users can be synced over from on-premises AD (Active Directory)</li>
	<li>user creation and termination automation process</li>
	<li>users and groups membership automation and Office 365 apps integration</li>
	<li>you don't need ADFS to have this working</li>
	<li>you don't need SSL certificates</li>
</ul>
Cons:
<ul>
	<li>you need local AD infrastructure to sync over user, groups, computers objects</li>
	<li>you need basic knowledge and exposure do ADDS (Active Directory Domain Services) attributes</li>
	<li>you need to manage your own Public DNS records or use any provider that can talk to Office 365 infrastructure</li>
</ul>
<strong>Step #1 - Buy a Domain (DNS domain)</strong>

Buy your Public domains. I use <a href="https://ca.godaddy.com">GoDaddy</a> Please feel free to use any available Public DNS provider in your Country or Region.

<strong>Step #2 - Check your Domains</strong>

Log on your Office 365 tenant as Global Admin

Go to the Home \ Settings \ Domains tab

At this Tab you can add, manage and delete your public DNS domains from your Office 365 tenant

You need this when you're adding new domains, migrating domains to your Office 365 tenant or out of your Office 365 tenant.

After you have your DNS domains added to your Office 365 Subscription you can have multiple users logging with different DNS domains under your Office 365 subscription and they can also be Azure AD synced.

<strong>Step #3 - Create a new user</strong>

Go to your Office 365 Portal

Go to <strong>Home \ Users \ Active Users tab</strong>

Here you can check all users created by status: synced, cloud only, licensed, unlicensed, etc.

Go ahead and click on "Add a user"
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/140.png" />

At <strong>Basics</strong> add the following info:
<ul>
	<li>First Name:</li>
	<li>Last Name:</li>
	<li>Display Name (will auto-fill from First Name + Last Name):</li>
	<li>Username:</li>
	<li>@domain_name: select the UPN (UserPrincipalName) assigned to this user</li>
</ul>
For <strong>Password settings</strong> you can<strong> auto-generate</strong> it or <strong>define</strong> one or event send the generated password to an internal or external email that you have access to. Please always select "Require this user to change their password when they first sign in" to protect your users.

<span style="color:#ff0000;"><strong>TIP!</strong></span>: you can have multiple domains under your Office 365 subscription

<strong>click Next</strong>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/133.png" />

At <strong>Assign product licenses</strong> select:
<ul>
	<li>Location: Brazil (Canada, etc.) - For large deployments set this location as default to not have issues when auto-assign users licenses for auto-provisioning tasks.</li>
	<li>Pick a product license: (if you don't have one, buy it at Home \ Billing \ Licenses)</li>
	<li>Apps: Expand Apps if you need to unselect or select more than one sub-product license (useful in some scenarios)</li>
</ul>
<strong>click Next</strong>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/134.png" />

&nbsp;

At <strong>Optional settings</strong> you can assign Administrative Access to users (roles).

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/135.png" />

At Review and finish you check all information and click on <strong>Finish adding</strong>.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/136.png" />

At the next screen you have your user created.

You can add another user or save this current task as a template for new users.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/137.png" />

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
