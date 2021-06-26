---
layout: post
title: Power Automate - Export and Import Flows
date: 2020-03-09 12:00
author: beierca
comments: true
categories: [Administration, export, flow, import, Microsoft Flow, Office365, Power Automate]
---
HI there

How many of you use Power Automate (AKA Microsoft Flow) on Office 365 to automate easy tasks such as get an email notification about the Weather, a notification when a file is created (uploaded) to a Microsoft Teams channel or even to publish on your Twitter account all your recent blog posts?

At this article I'll show how to export Power Automate Flows to a package of JSON file and import them. Particularly I am demonstrating here how to export to a .ZIP file from Office 365 Tenant "A" and how to import into another Office 365 Tenant.

<strong>Step 1 - At the Source Tenant (Exporting the Flow package)</strong>

Go to you source tenant (Tenant A) on Office 365 log as Global Administrator

Access the Power Automate Admin Console - <a href="https://us.flow.microsoft.com/">short link</a>

Access the <strong>My flows</strong> on the left menu, you should see all your current flows on the screen.
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/6.png" />

<strong>Select</strong> the Flow you would like to export

Click on the <strong>ellipses</strong> (...) know as "<em><strong>More Commands</strong></em>"

Then select <strong>Export</strong> option Package (.zip)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/7.png" />

Give the package a <strong>Name</strong>:

Rename or keep the <strong>Environment</strong>:

Give the package a <strong>Description</strong>:

<strong>Review</strong> the package content (name, resource type, import setup and action)
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/8.png" />

Click on <strong>Export</strong> and wait

<strong>Download</strong> the ZIP file created and go to your Downloads folder.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/9.png" />
<strong>
Step 2 - At the Target Tenant (Importing the Flow package)</strong>

Go to you source tenant (Tenant A) on Office 365 log as Global Administrator

<strong>Access</strong> the Power Automate Admin Console - <a href="https://us.flow.microsoft.com/">short link</a>

<strong>Access</strong> the My flows on the left menu, you should see all your current flows on the screen.

On the main Flows Screen you have a blue arrow to Import your flows.

<span style="color:#ff0000;">TIP!</span> Be aware that you'll need to update the flow that's being imported to use your current tenant's credentials <em><strong>username@targetsourcedomain.com</strong></em> as we as the flow content itself where you might have references to SharePoint Sites and Lists, Microsoft Teams Channels that are pointing to Source Tenant applications and its previous infrastructure.

<strong>Importing the Flows</strong>

<strong>Select "My flows"</strong> on the left side of the screen

Click on the blue arrow <strong>Import</strong>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/17.png" />

Select <strong>Upload </strong>to locate the file on your local computer
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/19.png" />

Select <strong>the File corresponding to the exported flow from source tenant </strong>and click <strong>Open</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/20.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/21.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/22.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/23.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/24.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/25.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/26.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/27.png" />

<strong>After you import the Flow</strong>

Edit the flow and double check
<ul>
	<li><strong>connectors</strong></li>
	<li><strong>flow contents</strong></li>
	<li><strong>credentials</strong></li>
</ul>
Now edit your imported Flow

Step 1

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/28.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/29.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/30.png" />

Step 2
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/49.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/16.png" />

Additional info

Exporting Flows (method #2)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/14.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/15.png" />

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
