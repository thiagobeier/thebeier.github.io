---
layout: post
title: Azure Policy Enforcement - 1
date: 2020-04-11 00:47
author: beierca
comments: true
categories: [Administration, Automation, Azure, json, policy, Tags, templates, Tips]
---
Hi there

We can use Azure Policy to enforce specific azure resources to be created only on <strong>specific locations in Azure Regions</strong> such as: CanadaCentral

This Azure policy enforcement should be used to keep your Azure Resource Group clean having all of its own azure resource items created within the same Azure Region.

Before you move forward please create the Azure Resource for this demonstration

<strong>New-AzResourceGroup -Name Demo -Location "canadacentral"</strong>

<strong><span style="color:#ff0000;">TIP!</span></strong>
<ul>
	<li>if you have multiple definitions on the same policy you will have to fulfill all prerequisites during the azure resources creation before having them created properly</li>
	<li>always define and use naming conventions that reminds you its actions such as <strong>Allowed locations_canadacentral</strong></li>
</ul>
<strong>Policy example</strong>
<pre>{
    "properties": {
        "mode": "all",
        "parameters": {
            "allowedLocations": {
                "type": "array",
                "metadata": {
                    "description": "The list of locations that can be specified when deploying resources",
                    "strongType": "location",
                    "displayName": "Allowed locations"
                },
                "defaultValue": [ "canandacentral" ]
            }
        },
        "displayName": "Allowed locations",
        "description": "This policy enables you to restrict the locations your organization can specify when deploying resources.",
        "policyRule": {
            "if": {
                "not": {
                    "field": "location",
                    "in": "[parameters('allowedLocations')]"
                }
            },
            "then": {
                "effect": "deny"
            }
        }
    }
}</pre>
<strong>Steps</strong>

Log on Azure Portal and search for "Policy" at the Azure Marketplace and click on it.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/169.png" />

Now you're at the Policy Blade - You will see a standard policy if that's your first time working with Policies withing your Azure Subscription. Otherwise, you'll see all available and assigned policies.

On this screen you have the following:
<ul>
	<li><strong>Authoring</strong>
<ul>
	<li><em>Assignments</em>: A policy assignment is a policy definition that has been assigned to take place within a specific scope.</li>
	<li><em>Definitions</em>: <span style="color:#ff0000;"><strong>Start here! </strong></span>Every policy definition has conditions under which it's enforced. And, it has a defined effect that takes place if the conditions are met.</li>
</ul>
</li>
	<li><strong>Scope</strong>: A scope could range from a <a href="https://docs.microsoft.com/en-us/azure/governance/management-groups/overview">management group</a> to an individual resource. The term <em>scope</em> refers to all the resources, resource groups, subscriptions, or management groups that the policy definition is assigned to. Policy assignments are inherited by all child resources.</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/170.png" />

<strong>Click on Authoring \ Definitions</strong>

On this screen you have the following:
<ul>
	<li>You can add, edit or delete an <strong>Initiative</strong></li>
	<li>You can add, edit or delete a <strong>Definition</strong></li>
	<li>you can use the search fields to look for an specific Initiative or Policy Definition</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/171.png" />

Click on <strong>Allowed locations_canadacentral</strong> custom policy

<img style="color:var(--color-text);" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/155.png" />

Check <span style="color:var(--color-text);">the following:</span>
<ul>
	<li><strong>Definition</strong>: the policy itself (you can copy, paste, edit the policy you want to deploy)</li>
	<li><strong>Assignments</strong>:</li>
	<li><strong>Parameters</strong>:</li>
</ul>
At <strong>Parameters</strong> you can assign, edit (copy and paste) the current policy

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/172.png" />
At Assignments you check what it's configured on it (click on the policy name "<em><strong>Allowed locations_canadacentral</strong> </em>")

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/173.png" />

Then you'll see the fields:
<ul>
	<li><strong>Basics</strong>
<ul>
	<li>Scope: in which Subscription ID this Policy is applied to</li>
	<li>Exclusions: it's for the Azure Resources Groups excluded for this policy assignments</li>
	<li>Assignment name: use the same policy name</li>
	<li>Policy enforcement: Enabled (set as enabled to have this working)</li>
	<li>Assigned by: who created and assigned the policy</li>
</ul>
</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/156.png" />

<strong>Exclusions expanded</strong>
<ul>
	<li>all the highlighted Azure Resources (on scope) will not receive this Policy enforcement.</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/159.png" />

<strong>Parameters</strong>
<ul>
	<li>same information from the JSON file policy</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/158.png" />

<span style="color:#ff0000;"><strong>Policy in action</strong></span>

Go to <strong>Demo1</strong> Azure Resource Group and try to create a new storage account on "<strong>Central US</strong>"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/167.png" />

It will fail on validation pointing to the <strong>Azure Policy name</strong> in place.

<img style="color:var(--color-text);" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/168.png" />

<strong>Error detailed</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/175.png" />

Click "Previous" or "Basics" and select Canada Central as Location for this Storage Account proceed through the NEXT screen until the validation to make sure that's gonna pass now. Proceed with the Storage Account creation by clicking on Create (blue button)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/176.png" />

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
