---
layout: post
title: Azure Policy Enforcement - 3
date: 2020-04-14 03:13
author: beierca
comments: true
categories: [Administration, Azure, azure policy, azure tags, policy, Storage, storage account, Tags]
---
Hi there

In this post I'm covering how to keep an Azure Resource Group TAGGED properly and how to propagate its TAGs to each resource within it.

That policy enforces that each azure resource created, moved into or preexisting on this specific Azure Resource will have the TAGs inherited from Azure Resource Group

Azure Resource Group Tags

Azure Resources - before policy enforcement

Azure Resources - after policy enforcement

<strong>Steps</strong>

1. Create the Azure Resource Group

2. Create 01 Azure Storage account at this Azure Resouce Group (verify that this resource has no TAG on it)

3. Add TAGs to the Azure Resource Group and check the Azure Storage Account TAGs properties (you should not see any TAGs in there)

4. Create the Azure Policy Definition

5. Create the Azure Policy Assignment

6. Assign the Azure Policy to the Azure Resource Group

7. Check the Azure Storage Account for TAGs inheritance from Azure Resource Group

&nbsp;

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
