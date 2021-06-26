---
layout: post
title: Create a static HTML web app in Azure
date: 2020-03-06 06:10
author: beierca
comments: true
categories: [Administration, Azure, Blog, html, web app, Web Apps]
---
Hi there

In this post I'm going over on how to create a static HTML web app in Azure

You'll need:
<ul>
	<li>Free azure subscription</li>
	<li>An Azure Resource (I'm using "<strong>MyBlog</strong>")</li>
	<li><a href="https://filezilla-project.org/download.php?type=client">Filezila ftp client</a> (to download default html file from the new azure web app and to modify it, upload it back and see the result)</li>
	<li>basic knowledge of HTML language</li>
</ul>
<strong>Steps to follow</strong>
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>go to your <strong>azure subscription</strong></li>
	<li>on <strong>home</strong> screen find the azure resource groups and select you resource group (i.e.: MyBlog)</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/31.png" />
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>select the<strong> Azure Resource</strong> and click on "+" add (to add the web app resource)</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/32.png" />
<ol>
	<li style="list-style-type:none;">
<ol>
	<li><strong>create</strong> the new web app</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/35.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/36.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/37.png" />
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>select the new web app (under <strong>Overview</strong>)</li>
	<li>copy the <strong>URL</strong> link <a href="https://htmlapp001.azurewebsites.net">https://htmlapp001.azurewebsites.net</a></li>
	<li>test the new web app main url <a href="https://htmlapp001.azurewebsites.net/">https://htmlapp001.azurewebsites.net/</a>(click on it , open new tab on the browser)</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/43.png" />
<ol>
	<li>accessing the<strong> web app ftp</strong>
<ol>
	<li>go to the <strong>Deployment Center</strong> blade and select FTP (scroll down and click on it then click on <em><strong>Dashboard</strong></em>)
<ol>
	<li>FTPS Endpoint:</li>
	<li>Username:</li>
	<li>Password:</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/45.png" />

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/41.png" /></li>
</ol>
</li>
	<li><strong>FTP access</strong> and html file changes
<ol>
	<li>configure the filezila ftp client accordingly
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>go on file \ site manager \ select the FTP site you've configured</li>
	<li>click connect</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/42.png" />
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>you should see the <em><strong>hostingstart.html</strong></em> file in there</li>
	<li>download the file</li>
	<li>rename it to <em><strong>newhostingstart.html</strong></em></li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/48.png" />
<ol>
	<li>edit it and change the following
<ol>
	<li>locate <span style="color:#0000ff;">"Microsoft Azure App Service - Welcome"</span> change to <span style="color:#ff0000;">"Microsoft Azure App Service - Welcome by Thiago Beier"</span></li>
	<li>locate <span style="color:#0000ff;"><span style="color:#0000ff;">"</span>Hey, App Service Developers!</span>" change to <span style="color:#ff0000;">"Hey, App Service by Thiago Beier!</span>"</li>
	<li>save it</li>
</ol>
</li>
	<li>upload the file back to the web app root path</li>
	<li>go back to the site url <a href="https://htmlapp001.azurewebsites.net/">https://htmlapp001.azurewebsites.net/</a></li>
	<li>add the new html file name at the end of the complete url <a href="https://htmlapp001.azurewebsites.net/newhostingstart.html">https://htmlapp001.azurewebsites.net/newhostingstart.html</a> and see the changes you've made</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/41.png" /></li>
</ol>
</li>
</ol>
Fell free to <strong>explore</strong> the other blades such as:
<ul>
	<li><a href="https://docs.microsoft.com/en-us/azure/app-service/web-sites-traffic-manager-custom-domain-name">Custom Domains</a></li>
	<li><a href="https://docs.microsoft.com/en-us/azure/app-service/manage-backup">Backups</a></li>
	<li>Configuration \ <a href="https://docs.microsoft.com/en-us/azure/app-service/configure-common">Default Documents</a></li>
	<li>Development tools \ <a href="https://microsoft.github.io/AzureTipsAndTricks/blog/tip20.html">Console</a></li>
</ul>
<strong>Quick view</strong> on the Development tools \ Console
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/38.png" />

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
