---
layout: post
title: Azure Terraform #4
date: 2020-05-12 13:00
author: beierca
comments: true
categories: [Azure, azure cloud shell, IaC, Powershell, Terraform]
---
Hi there

In this article I'm covering a summary of 3 topics we talked about
<ol>
	<li><strong>Prerequisites</strong>
<ol>
	<li>Terraform latest version</li>
	<li>PATH variable configure (you can call terraform from anywhere in cmd.exe and powershell or from Visual Studio Code)</li>
	<li>Visual Studio Code or notepad++ or any other text editor you'd like to use</li>
</ol>
</li>
	<li><strong>Basic Azure LAB</strong>
<ol>
	<li>Azure resource group</li>
	<li>VNET</li>
	<li>VM (IAAS) - Linux UbuntuServer</li>
	<li>Apache2 running on the deployed VM
<ol>
	<li>I'll show how to install apache2 without logging in the VM (out of Terraform)</li>
</ol>
</li>
	<li>Resources with TAGs by default (MY subscription has policy enforcement for 2 tags: environment and costcenter and location:canadacentral)</li>
</ol>
</li>
	<li><strong>How do deploy it</strong>
<ol>
	<li>copy <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plain1-main.tf" target="_blank" rel="noopener">main.tf</a> to your working folder.</li>
	<li>rename from plan1-main.tf to main.tf</li>
	<li>open it and have a look</li>
	<li>having your plan saved <strong>plan1</strong> run the following:
<ol>
	<li><strong>az login</strong> (proceed with Azure logon process on browser and close it , or leave that it will close in 10 seconds) return to the working folder</li>
	<li><strong>terraform init</strong></li>
	<li><strong>terraform apply "plan1"</strong></li>
	<li>check the output
<em>az login</em>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/2.png" />
<em>Terraform init</em><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/4.png" />
<em>Terraform plan -out plan1</em>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/6.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/7.png" /></li>
</ol>
</li>
</ol>
</li>
	<li><strong>How to update its deployment (check <span style="color:#ff0000;">Learn More</span> section below)</strong>
<ol>
	<li>make changes on your environment
<ol>
	<li>add tags to all resources published</li>
	<li>run terraform plan -out plan<strong>X</strong></li>
	<li>run terraform -apply plan<strong>X</strong></li>
</ol>
</li>
</ol>
</li>
	<li><strong>How to destroy it</strong>
<ol>
	<li>having finished your testing destroy it to save money$
<ol>
	<li>run <strong>terraform destroy</strong>
<span style="color:#ff0000;"><strong>WARNING</strong></span>: everything will be destroyed from this specific deployment on Azure</li>
</ol>
</li>
</ol>
</li>
</ol>
<strong><span style="color:#ff0000;">Learn More</span></strong>

<strong>Time to improve what you have deployed</strong>
<ul>
	<li>after your deployment is done check the Resourse Group resources. You should see 1 virtual machine, 1 virtual network, 1 disk, 1 public IP (<a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/3.png" target="_blank" rel="noopener"><em><strong>Dynamic</strong></em></a>), 1 network interface and 1 network security group<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/8.png" /></li>
	<li>go to the public IP and copy its IP Address<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/9.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/10.png" /></li>
	<li>try to access it on port 22, what's the error?
<ul>
	<li>user@IPaddress (check main.tf for default username and password under the VM resource creation)</li>
</ul>
</li>
	<li><span style="color:#ff0000;"><strong>TIP</strong></span>: navigate to your Azure Resource Group \ Network security group \ interfaces blade - what's missing?</li>
	<li><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/13.png" /></li>
	<li></li>
	<li>click <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan2-main.tf" target="_blank" rel="noopener">here</a> to copy <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan2-main.tf" target="_blank" rel="noopener">main.tf</a> for plan2 on terraform</li>
	<li>replace your initial main.tf file content by the new one (open plan2-main.tf file and copy its content, open main.tf select all and paste copied content into it)</li>
	<li><strong>Plan2</strong>
<ul>
	<li>search for <strong>"associating NSG to NIC"</strong>  without the "", you should get into a line with comments #associating NSG to NIC</li>
	<li>run terraform plan -out plan2</li>
	<li>run terraform apply "plan2"<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/14.png" /><img src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/12.png" /></li>
	<li>go to your Azure portal , Resource Group "" and check if the Network security group \ interfaces had been populated<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/15.png" /></li>
	<li>now try to access the vm on Port 22<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/16.png" /></li>
	<li>user@IPaddress</li>
	<li>after you get into the VM check its internal ip: ifconfig<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/17.png" /></li>
	<li>logout your vm session</li>
	<li>try to access the VM on port 80 http://publicIPaddress , what's the output? - Go to Plan3<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/24.png" /></li>
</ul>
</li>
	<li><strong>Plan3</strong>
<ul>
	<li>click <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan3-main.tf" target="_blank" rel="noopener">here</a> to copy <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan3-main.tf" target="_blank" rel="noopener">main.tf</a> for plan3 on terraform</li>
	<li>replace your initial main.tf file content by the new one (open plan3-main.tf file and copy its content, open main.tf select all and paste copied content into it)</li>
	<li>search for <strong>"adding port 80"</strong> without the "", you should get into a line with comments #adding port 80<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/23.png" /></li>
	<li>run terraform plan -out plan3</li>
	<li>run terraform apply "plan3"<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/26.png" /></li>
	<li>go to your Azure portal , Resource Group "Name" and check if the Network security group \ Inbound security rules has a firewall rule to allow TCP PORT 80 from any to any with priority 1002<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/28.png" /></li>
	<li>try to access the VM on port 80 http://publicIPaddress, what's missing?</li>
	<li><span style="color:#ff0000;"><strong>TIP</strong></span>: go to your Azure portal , Resource Group "Name" , select the VM, under Operations (left blade) \ Run command
<ul>
	<li style="list-style-type:none;">
<ul>
	<li>select <strong>RunShellScript</strong></li>
	<li>on the next blade paste the following command: a<strong>pt-get install apache2 -y</strong> and wait until is completed then issue another command: <strong>service apache2 start</strong></li>
	<li>go back to the <strong>http://publicIPaddress</strong> and you should see Apache default web site<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/20.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/21.png" /></li>
	<li><a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan3-main.tf.mp4" target="_blank" rel="noopener">video</a>: when apache setup and start command is running and your browser (chrome with auto refresh plugin is waiting for apache to comes up)[video src="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/plan3-main.tf.mp4"]</li>
</ul>
</li>
</ul>
&nbsp;
<ul>
	<li>click <a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/terraform/4/Azureresources%20(terraform4).csv" target="_blank" rel="noopener">here</a><span style="color:var(--color-text);"> to check its azure resources csv file.</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<strong>Working on Next article #1</strong>: Customize the latest main.tf (plan3) adding the apache2 installation and its initial index.html setup from custom files.

<strong>Working on Next article #2</strong>: Basic Azure LAB with 02 VMS with WAF (Web Application Firewall)

<strong>Working on Next article #3</strong>: Basic Azure LAB with 02 VMS with WAF (Web Application Firewall) and Azure Front Door

<em><strong>References
</strong></em>https://www.terraform.io/docs/providers/azurerm/r/network_interface_security_group_association.html

Thanks,

Thiago Beier
<em>Share this article if you liked it.</em>
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
