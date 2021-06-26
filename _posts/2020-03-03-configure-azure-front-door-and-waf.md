---
layout: post
title: Configure Azure Front Door and WAF
date: 2020-03-03 09:00
author: beierca
comments: true
categories: [Azure, azure front door, geo-restriction, network security, Security, waf]
---
Hi there

In this article will be configuring <strong>Azure Front Door</strong> with WAF () to block unauthorized access per Region (Geo-filtering)

<strong>Azure Front Door Service</strong> enables you to define, manage, and monitor the global routing for your web traffic by optimizing for best performance and instant global failover for high availability.

<strong>Prerequisites</strong>
<ul>
	<li>For this article we used 01 VM (IAAS) size: Standard DS1 v2 (1 vcpus, 3.5 GiB memory) running default IIS site with a static Public IP address</li>
	<li>Take notes of the following:
<ul>
	<li>VM DNS Name (each IAAS VM nas a DNS Name)</li>
</ul>
</li>
	<li>You need our own <a href="https://ca.godaddy.com">DNS service</a> to make changes need on CNAME entries</li>
</ul>
<strong>Azure Front Door</strong> will be replacing http/https direct access to the site (s) running on the Windows Server VM protecting its unauthorized access with WAF.

<strong>Setup Azure Front Door Service</strong>
<ul>
	<li>create the Azure Front Door resource on Azure</li>
	<li>Add a frontend host for Front Door</li>
	<li>Add application backend and backend pools</li>
	<li>Add a routing rule</li>
</ul>
<h4 id="how-to-set-up-a-geo-filtering-waf-policy-for-your-front-door">How to set up a geo-filtering WAF policy for your Front Door</h4>
This feature allows you to block traffic from specific Country / Region i.e.: you want your application to be accessed only from Canada and U.S.A. and block from Brazil
<ul>
	<li>go on the Azure Front Door you created and select the <strong>"Web application firewall" blade and check it there is any policy in there</strong></li>
	<li>go to the Azure market place and search for "Web Application Firewall (WAF)"</li>
	<li>create a new one</li>
	<li>at policy for:</li>
	<li>at subscription:</li>
	<li>at Resource Group:</li>
	<li>under instance details
<ul>
	<li>policy name:</li>
	<li>policy state: leave default (Enabled)</li>
</ul>
</li>
	<li>after your WAF is created go to its resource and select custom rules blade
<ul>
	<li>click on "+ add custom rule"</li>
	<li>give a name at custom rule name:</li>
	<li>leave status and rue type default options (enabled and match)</li>
	<li>set priority to 1 (it can't be blank)</li>
	<li>under conditions
<ul>
	<li>Match type: Geo-location</li>
	<li>Match variable: RemoteAddres</li>
	<li>Operation: select is</li>
	<li>Country code: pick all countries you want to block (those countries won't be able to reach site1.thebeier.com or site2.thebeier.com)</li>
	<li>leave the default condition as Deny Traffic
<ul>
	<li>click Add and hit SAVE on the next screen (the main screen for Custom Rules)</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/1.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/2.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/3.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/4.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/5.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/6.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/7.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/8.PNG" /></li>
</ul>
</li>
</ul>
</li>
</ul>
<strong>DNS changes</strong>
<ul>
	<li>Add a CNAME address pointing your site URL address to the Azure Front Door Host
<ul>
	<li>Go to your DNS service management portal</li>
	<li>add a CNAME to site1 under your domain thebeier.com (full URL site1.thebeier.com) pointing to Azure Front Door Frontend Host URL (leave TTL low to speed up your test)</li>
</ul>
</li>
</ul>
<strong>Network Security Group</strong>
<ul>
	<li>Make changes on the VM Network security group</li>
	<li>this is how you block ANY ANY (Internet to VM) http/https access and allow only for Azure Front Door service tag on Azure NSG (Network Security Group)</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/waf/9.png" />

<strong>Testing Azure Front Door and WAF policies</strong>
<ul>
	<li>Try to access your site from Canada and U.S.A. (result expected: access allowed)
<ul>
	<li>I'm located in Toronto so I can reach site1.thebeier.com from my host (or vm on my laptop)</li>
</ul>
</li>
	<li>Try to access your site from Brazil (result expected: access denied)
<ul>
	<li>create a VM on Azure IAAS located in Brazil to have this test done or access ask anyone you know that's in Brazil to access site1.thebeier.com</li>
</ul>
</li>
</ul>
<strong>References</strong>
<strong>Azure Front Door</strong> <a href="https://docs.microsoft.com/en-us/azure/frontdoor/front-door-faq">https://docs.microsoft.com/en-us/azure/frontdoor/front-door-faq</a>
<strong>WAF</strong> <a href="https://docs.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overviewhttps://docs.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overview">https://docs.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overview</a>

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
