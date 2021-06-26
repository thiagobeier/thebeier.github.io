---
layout: post
title: Azure Policy Enforcement - 2
date: 2020-04-14 03:10
author: beierca
comments: true
categories: [Administration, Azure, policy, Tags]
---
Hi there

In this article I'm demonstrating how to use Azure Policy to enforce each Resource to be created within a specific resource with at least two TAGS: <em><strong>CostCenter</strong> </em>and <em><strong>Environment</strong></em>.

Those TAGS are used for <strong>Cost Analysis</strong> at Azure Cost Center as well.
<a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/enforce%20the%20tag%20but%20to%20allow%20any%20value%20to%20be%20used.txt">Download</a> the policy used in this article.

<strong>Steps</strong>

1. <strong>Create</strong> the Azure Definition

Go to Azure portal \ Home \ "Search Resources, services and docs"
Search for Policy (then you can pin it on your home screen after)

On Azure policy screen select Definitions (left menu)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/1.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/2.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/3.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/4.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/5.png" />

2. <strong>Assign</strong> the Azure Policy

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/6.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/7.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/8.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/9.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/10.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/11.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/12.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/13.png" />

3. <strong>Wait</strong> for the policy to get at its running state and check its compliance.
Home \ Policy \ Overview <a href="https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/Overview">link</a>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/pol1/14.png" />

4. Test to <strong>add (create)</strong> a new azure resource within one of the Azure Resource Groups you defined (out of exclusions list).

<span style="color:#ff0000;"><strong>TIP!</strong></span> - This will force each new azure resource that's gonna be created at Demo1 Resource Group to have those two (02) TAGs. Otherwise, the validation step on creation will fail.

Use this policy to prevent that you have azure resources that are not being flagged and tracked properly at the cost center. Some users complained about costs surprises on their invoices and without policy enforcing TAGs properly we they simply lose the control on its monthly costs by Project, Environment, Cost Center or any other key used for Businesses.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
