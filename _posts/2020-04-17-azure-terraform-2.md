---
layout: post
title: Azure Terraform #2
date: 2020-04-17 14:00
author: beierca
comments: true
categories: [Automation, Azure, azure policy, IaC, Terraform]
---
Hi there

At this post series we'll cover the how to create an Azure Resource Group, VNET (Virtual Network) with subnets and 01 Linux VM with Public IP address accessible from internet on SSH (TCP Port 22)
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>Access your Visual Studio Code</li>
	<li>Create a new Folder where your project will be stored</li>
	<li>Have your Azure subscription credentials ready</li>
	<li>Log on your Azure subscription from the Visual Studio Code Terminal</li>
	<li>Create your main.tf file and save it with empty content</li>
	<li>Here it's how your screen should be like</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/1/20.png" />
<ol>
	<li>Use the <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/main.tf">following</a> example to create your 1st Azure Resource Group with your Azure Resources within it.
<div>
<pre>#Provider

provider "azurerm" {

  features {}

}

#Azure Resource Group

resource "azurerm_resource_group" "terraform" {

  name     = "terraform"

  location = "canadacentral"

  }
</pre>
</div></li>
	<li>You'll see an error on this deployment because my Azure Subscription has a Policy enforcement to allow resources only in Canada Central location / region.<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/5.png" /></li>
	<li>Fix the location at the main.tf file and proceed with:
<ol>
	<li>terraform init<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/3.png" /></li>
	<li>terraform plan<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/4.png" />- you can also try the following: terraform plan -out myplan2
- this saves your current plan to <em><strong>myplan2</strong> </em>file</li>
	<li>terraform apply (you need to confirm the operation with <span style="color:#ff0000;"><strong>YES</strong></span>)
- or you can apply the saved plan: <em>terraform apply myplan2</em>
- this apply your saved <em><strong>myplan2</strong> </em>to your azure subscription<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/6.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/7.png" /></li>
	<li>check the output to make sure your deployment run ok
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/8.png" /></li>
</ol>
</li>
</ol>
<ul>
	<li>Test your access to the new deployed Resource Group in Azure
<ol>
	<li>Open Chrome (with the auto refresh plugin) on the Azure Portal website at Azure Resources tab to see when the Azure Resource Group you've created shows up</li>
</ol>
</li>
	<li>Keep this <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/main.tf">main.tf</a> for the next article.</li>
</ul>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
