---
layout: post
title: Azure Policy - Part1
date: 2020-04-21 13:00
author: beierca
comments: true
categories: [Administration, Azure]
---
Hi There

In this article I'm going to introduce you on how to use Azure Policy to keep your Resources and Resources Groups standardized with Tags.

<strong>What is Azure Policy?</strong>
Azure Policy is a service in Azure that you use to create, assign, and manage policies where these policies enforce different rules and effects over your resources, so those resources stay compliant with your corporate standards and service level agreements. In addition, Azure Policy meets this need by evaluating your resources for non-compliance with assigned policies.
<ul>
	<li>A custom policy definition allows customers to define their own rules for using Azure and those rules enforces the following:
<ul>
	<li>Security practices</li>
	<li>Cost management</li>
	<li>Organization-specific rules (like naming or locations)</li>
</ul>
</li>
</ul>
<strong>What are Tags on Azure and how to use?</strong>
Tags are used to organize cloud-based assets in ways that aid operational management and support accounting requirements is a common challenge in large cloud adoption efforts. You can also use tags to monitor and control deployments and costs on Azure.

<strong>Things you need to know when creating tags:</strong>
<ul class="tightList is-style-disc-overcast">
	<li>Tags aren’t inherited hierarchically from resource group to resource</li>
	<li>Tag names can have up to 512 characters; values can have up to 256</li>
	<li>Tags in Azure are not case-sensitive</li>
	<li>These characters aren’t supported with tags: &lt; &gt; % &amp; / ?</li>
	<li>A single resource can be assigned up to 15 tags</li>
</ul>
Azure Policy Blade in Azure Portal

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_4.png" />

Next Article - Azure Policy - Part2 (tags)

<em><strong>References</strong></em>
https://docs.microsoft.com/en-us/azure/governance/policy/samples/
https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging#naming-and-tagging-resources
https://docs.microsoft.com/en-us/azure/governance/policy/tutorials/govern-tags
Full <a href="https://opdhsblobprod01.blob.core.windows.net/contents/4a6d75bb3af747de838e6ccc97c5d978/3355643105170622e064eb7165828337?sv=2015-04-05&amp;sr=b&amp;sig=aLm0R7GDIhX%2FdkeVADJR6fRZ6KRsh5AVR0a%2B0xNWLe0%3D&amp;st=2020-02-27T03%3A36%3A39Z&amp;se=2020-02-28T03%3A46%3A39Z&amp;sp=r">PDF</a> about Azure Policy

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
