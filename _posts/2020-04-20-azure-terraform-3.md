---
layout: post
title: Azure Terraform #3
date: 2020-04-20 12:00
author: beierca
comments: true
categories: [Automation, Azure, IaC, Terraform, VNET]
---
Hi there

Continuing our journey on how to automate Azure Resources deployment using Terraform today we're demonstrating how to create (or add to our current plan) a VNET with subnets.

Have with you your previous <em><strong>main.tf</strong></em> file - download from <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/main.tf">here</a>.

Now open your Visual Studio Code and open your Project Folder

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/10.png" />

Load your <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/main.tf">main.tf</a> and lets add the following code for the <a href="https://docs.microsoft.com/en-us/azure/virtual-network/quick-create-portal">VNET</a> creation
<ul>
	<li>Creates a VNET named: example-network</li>
	<li>VNET IP address block: 10.0.0.0/16</li>
	<li>Creates a Subnet 10.0.1.0/24 named: subnet1</li>
	<li>Azure Resource Group Name: terraform Resource Group (created previously)</li>
</ul>
<div>
<div>
<pre>#Azure Resource Group

resource "azurerm_resource_group" "rg" {

  name     = "terraform"

  location = "canadacentral"

}

# Create a virtual network within the resource group

resource "azurerm_virtual_network" "vnet" {

  name                = "example-network"

  location            = azurerm_resource_group.rg.location

  resource_group_name = azurerm_resource_group.rg.name

  address_space       = ["10.10.0.0/16"]

tags = {

    CostCenter = "IT"

    Environment = "PROD"

  }

}

# Create Subnets

resource "azurerm_subnet" "subnet" {

  name                 = "subnet1"

  resource_group_name  = azurerm_resource_group.rg.name

  virtual_network_name = azurerm_virtual_network.vnet.name

  address_prefix       = "10.10.1.0/24"

}</pre>
</div>
</div>
You should see the following

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/14.png" />

Open a PowerShell on your Project Folder and run the following

<strong>az login</strong> (to connect to your azure subscription)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/11.png" />

enter your credentials on browser and wait for the next screen

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/12.png" />

<strong>terraform init</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/15.png" />

<strong>terraform plan </strong>(OR <em>terraform plan -out myplan3 to save your plan and reuse it if needed - <span style="color:#ff0000;">keep your code under control</span></em>)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/16.png" />

<strong>terraform apply</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/17.png" />

<strong>Check you result at Azure Portal</strong>

<em>Before</em>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/13.png" />

<em>After</em>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/18.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/19.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/20.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/21.png" />

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
