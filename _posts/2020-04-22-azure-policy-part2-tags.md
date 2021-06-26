---
layout: post
title: Azure Policy - Part2 (tags)
date: 2020-04-22 14:30
author: beierca
comments: true
categories: [Administration, Azure, Uncategorized]
---
Hi there

At this article - Part2 I'll show you how to create and manage policies to enforce compliance on Azure Resources and Azure Resource Groups guaranteeing to your Azure Deployment some standardization for filtering and costs management as well.
<h4 id="basics">The basics of resource tagging in Azure</h4>
Tags allow you to organize resources and resource groups by assigning them a <code>name:value</code> pair such as <code>CostCenter:IT</code>.

That's really useful when it comes to things like
<ul>
	<li><strong style="color:var(--color-text);">Access control and compliance:</strong><span style="color:var(--color-text);"> allows you to keep track of who can access what, where protecting sensitive data. </span></li>
	<li><strong>Automation:</strong> apply bulk actions to related resources automatically, e.g. “shut down all VMs with the tag <code>Environment:Uat</code> overnight” or “in resource-group-uat or  delete resources that have been inactive for 180 days”</li>
	<li><strong>Cost management:</strong> most tags assigned to resources are included in your detailed usage data exported as graph or CSV. At the Cost Management Portal / Blade that lets you filter resources according to a common project, customer, department, line of business, etc., facilitating reporting and identifying which department is responsible for which cost.</li>
</ul>
You can assign policies on the Azure Portal, on PowerShell, on Azure CLI and using templates as you prefer.
<ul class="tree-group" role="group">
	<li role="none"><a class="tree-item is-leaf is-selected" role="treeitem" href="https://docs.microsoft.com/en-us/azure/governance/policy/assign-policy-portal">Assign a policy - Portal</a></li>
	<li role="none"><a class="tree-item is-leaf" role="treeitem" href="https://docs.microsoft.com/en-us/azure/governance/policy/assign-policy-powershell">Assign a policy - PowerShell</a></li>
	<li role="none"><a class="tree-item is-leaf" role="treeitem" href="https://docs.microsoft.com/en-us/azure/governance/policy/assign-policy-azurecli">Assign a policy - Azure CLI</a></li>
	<li role="none"><a class="tree-item is-leaf" role="treeitem" href="https://docs.microsoft.com/en-us/azure/governance/policy/assign-policy-template">Assign a policy - template</a></li>
</ul>
<strong><span style="color:#ff0000;">Tip!</span></strong> - Have a look at the RBAC and Azure policy section <a href="https://docs.microsoft.com/en-us/azure/governance/policy/overview#rbac-permissions-in-azure-policy">here</a>.

First of all Create an Empty Resource Group on Azure to assign policies to it from the beginning.

Log on Azure Portal <a href="https://portal.azure.com">https://portal.azure.com</a>
Go to <strong>Home</strong> and select Resource groups
click on <strong>"+" to Add</strong> a new Resource group

<strong>Follow the wizard</strong> to create a new Resource group
<em>Subscription</em>:
<em>Resource group Name</em>: (can't be blank)
<em>Resource details (region)</em>: select the closes region that fit your needs (Canada Central)
select "review+create" box and wait to be completed then you can go to the new resource group created

Now you can start to define your tags and policy standards such as
<ul>
	<li>the <strong>Demo</strong> resource group will have the following tags
<ul>
	<li>environment: demo</li>
	<li>owner: Thiago B.</li>
	<li>costcenter: IT</li>
</ul>
</li>
	<li>the following policies will be applied to your subscription at Demo resource group only
<ul>
	<li>Assign a policy to enforce a condition for resources you create in the future (inherited from Demo resource group only)</li>
	<li>Create and assign an initiative definition to track compliance for multiple resources</li>
	<li>Resolve a non-compliant or denied resource</li>
</ul>
</li>
</ul>
<strong>Screenshots</strong>

Go to Azure Resource Groups

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_7.png" />

Click "+ Add"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_8.png" />

Follow the Wizard "Create a resouce group", give it a name and select the region (Location) and click on "Review + create"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_9.png" />

Check the Validation step and click "Create"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_10.png" />

Wait for the task to be completed and click at "Go to resource group"

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_11.png" />

You're now at the Demo Resource Group
<ul>
	<li>check the subscription name and id</li>
	<li>check the tags field</li>
	<li>check the deployments field</li>
</ul>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_12.png" />

<strong>Creating the Tags</strong>

go to <strong>Demo</strong> resource group and select the blade TAGS on left

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_13.png" />

add the TAGs Name and Values accordingly and click <strong>SAVE <span style="color:#3366ff;">(use tab to navigate between the Tags fields)
</span></strong>
- <strong>Name</strong>: environment, <strong>Value</strong>: demo
- <strong>Name</strong>: owner, <strong>Value</strong>: Thiago B.
- <strong>Name</strong>: costcenter, <strong>Value</strong>: IT
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_14.png" />

check if the Tags were added successfuly

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/azrpolicy/Screenshot_15.png" />

<strong><span style="color:#ff0000;">Pending</span> </strong>- Policy to enforce those tags to be inherited by all Resources withing this Resource Group

Next Article - Azure Policy - Part3 (tags)

References

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
