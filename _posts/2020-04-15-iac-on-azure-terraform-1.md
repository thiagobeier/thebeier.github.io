---
layout: post
title: IaC on Azure - Terraform #1
date: 2020-04-15 16:37
author: beierca
comments: true
categories: [Automation, Azure, IaC, Terraform, visual code]
---
Hi there

As an introduction of Infrastructure as Code (IaC) with Azure Resource Manager (ARM) Template I'd like to cover this in a couple articles.

At this one we're gonna cover the concept and how to prepare our environment on Windows 10 machine using Visual Studio Code (you can also do the same on Notepad++) with Terraform.

Advantages of using IaC on your Azure environment with ARM (before Terraform)
<ul>
	<li><strong>Consistency</strong>: Consistently achieve standardized provisioning or deployment</li>
	<li><strong>Accelerating</strong>: Accelerating provisioning or deployment rapidly</li>
	<li><strong>Reusability</strong>: Reusable JSON code for repeatable or similar provisioning or deployment</li>
	<li><strong>Extensibility</strong>: Extensible JSON code for incorporating with additional items</li>
</ul>
Advantages of using Terraform to automate Azure deployments
<ul>
	<li><strong>Orchestration</strong>, not merely configuration</li>
	<li><strong>Immutable</strong> infrastructure</li>
	<li><strong>Declarative</strong>, not procedural code</li>
	<li><strong>Client-only</strong> architecture</li>
</ul>
<strong>Setup your environment</strong>
<ol>
	<li>Tutorial: Configure the Azure Terraform Visual Studio Code extension</li>
	<li>Prerequisites
<ul>
	<li>Azure subscription: If you don't have an Azure subscription, create a <a href="https://azure.microsoft.com/free/?ref=microsoft.com&amp;utm_source=microsoft.com&amp;utm_medium=docs&amp;utm_campaign=visualstudio">free account</a> before you begin.</li>
	<li>Terraform: <a href="https://docs.microsoft.com/en-us/azure/terraform/terraform-install-configure">Install and configure Terraform</a>. I've tested with the Terraform v0.12.24 and provider.azurerm v2.5.0</li>
	<li>Visual Studio Code: Install the version of <a href="https://code.visualstudio.com/download">Visual Studio Code</a> that is appropriate for your environment.</li>
</ul>
</li>
	<li>Prepare your dev environment</li>
	<li>Install <a href="https://git-scm.com/download/win">Git</a></li>
	<li>Install <a href="https://www.terraform.io/downloads.html">Terraform</a></li>
	<li>Install <a href="https://nodejs.org/en/">Node.js</a> - <a href="https://nodejs.org/dist/v13.12.0/node-v13.12.0-x64.msi">Latest Version</a> (checked April 14th)</li>
	<li>Install <a href="https://graphviz.gitlab.io/_pages/Download/Download_windows.html">GraphViz</a></li>
	<li>Install Terraform Visual Studio Code extension
<ol>
	<li>Launch Visual Studio Code.</li>
	<li>Select <strong>Extensions</strong>.</li>
	<li>Use the <strong>Search Extensions in Marketplace</strong> text box to search for the Azure Terraform extension:

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/1/13.png" /></li>
	<li>Select <strong>Install</strong>.</li>
</ol>
</li>
	<li>
<h3 id="prepare-a-test-plan-file">Prepare a test plan file</h3>
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>In Visual Studio Code, select <strong>File &gt; New File</strong> from the menu bar.
<ol>
	<li>copy the code below
<pre class="highlight hcl"><code><span class="n">#Provider
provider "azurerm" {
features {}
}
resource</span> <span class="s2">"azurerm_resource_group"</span> <span class="s2">"example"</span> <span class="p">{</span>
  <span class="nb">name</span>     <span class="o">=</span> <span class="s2">"terraform"</span>
  <span class="n">location</span> <span class="o">=</span> <span class="s2">"canadacentral"</span>
<span class="p">}</span></code></pre>
</li>
</ol>
</li>
	<li>From the menu bar, select <strong>File &gt; Save As</strong>.</li>
	<li>In the <strong>Save As</strong> dialog, navigate to a location of your choice and then select <strong>New folder</strong>. (Change the name of the new folder to something more descriptive than <em>New folder</em>.)</li>
	<li>Make sure your new folder is highlighted (selected) and then select <strong>Open</strong>.</li>
	<li>In the <strong>Save As</strong> dialog, change the default name of the file to <em>main.tf</em>.</li>
	<li>Select <strong>Save</strong>.</li>
	<li>In the menu bar, select <strong>File &gt; Open Folder</strong>. Navigate to and select the new folder you created.
c:\Azure\1\
check your main.tf file content</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/1.png" />
<ol>
	<li>For this deployment let's use your Powershell or CMD.exe (make sure you have terraform in your Environment PATH)
<ol>
	<li>Run all commands from the folder where your main.tf is located
<ol>
	<li style="list-style-type:none;">
<ol>
	<li style="list-style-type:none;">
<ol>
	<li><strong><strong>terraform init</strong></strong>&nbsp;

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/3.png" /></li>
	<li><strong><strong>terraform plan</strong></strong>&nbsp;

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/4.png" /></li>
	<li><strong>terraform apply</strong> <span style="color:#ff0000;"><strong>(before we need to login in Azure)
</strong><em>az login
</em></span>- enter your Azure Subscription login on the browser if you have MFA enabled
- proceed after the browser notifies you to close it and go back to your deployment
<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/5.png" />answer <span style="color:#ff0000;"><strong>YES</strong> </span>to the proceed with this deployment

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/6.png" />

check the deployment was successful

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/7.png" />

check the Azure Resource Group created in Azure

<img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/0/8.png" /></li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
</ol>
<em><strong>References</strong></em>

https://www.terraform.io/docs/providers/azurerm/index.html
https://learn.hashicorp.com/
http://portal.azure.com/
https://registry.terraform.io/providers/hashicorp/azurerm/2.5.0
https://registry.terraform.io/browse/providers

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
