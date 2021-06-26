---
layout: post
title: Azure - just-in-time access (JIT)
date: 2020-05-19 13:00
author: beierca
comments: true
categories: [Automation, Azure, azure security center, JIT, just-in-time, remote access, Security, vpn]
---
Hi there

In this post I'd like to show you JIT (just-in-time) and how it works

JIT will create an inbound rule on a NSG (Network Security Group) associated to a VM (Virtual Machine) allowing traffic on the following ports 22, 3389, 5985 or 5986 by up to 24 hours.
<ol>
	<li>setup JIT in Azure Security Center</li>
	<li>double check your Virtual Machine \ Networking (inbound port rules)</li>
</ol>
<strong>Step #1 - Enable / Configure JIT for the VMS you'd like to test</strong>

Go to Azure Portal \ Home \ All services and search for Security Center and click on it.

<span style="color:#ff0000;"><strong>TIP</strong></span>: use the same <strong>Azure Security Center</strong> to enable and request access the VM (users need access to Azure Portal or via PowerShell to do so).

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/22.png" />

At Azure <strong>Security Center</strong> blade navigate to ADVANCED CLOUD DEFENSE \ Just in time VM access

Now you can see Virtual Machines and 03 sub menus:
<ul>
	<li>Configured</li>
	<li>Not Configured</li>
	<li>Unsupported</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/23.png" />

Select Not Configured to enable JIT on your VM

If the VM's list is large click on search and add your VM in there

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/25.png" />

VM-FS01 is our demo vm for this article.

Search for VM-FS01

Select the VM VM-FS01 and click the blue button "Enable JIT on X VMs"

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/26.png" />

Switch back to the Configured menu and check if the VM has JIT enabled already.

If JIT is already enabled you'll see the option "Request access" in blue when you select the VM-FS01 virtual machine.

Click on "Request access"

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/30.png" />

on the next screen (new blade) toggle On for the port you want to enable, for this we're using 3389 then select IP Range and add the ip range where your traffic is coming from.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/31.png" />

<span style="color:#ff0000;"><strong>TIP</strong></span>: if you're connecting from internet you need to add the public source IP address to allow this connection to come through. In this article I'm connected to a Point-to-site vpn on azure with 10.13.1.0/24 IP block.

Add 10.13.1.0/24 as the IP range and select the Time range in hours. (after this time the rule will be disabled from the VM NSG).

Enter a request justification and click on Open ports (will be in blue if you've added / selected all prerequisites for this request.

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/28.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/32.png" />

You can check the activity logs for the specific vm and check JIT audit logs

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/24.png" />

Now you're able to connect using MSTSC (RDP on 3389) to VM-FS01 vm

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/35.png" />

<strong>Step #2 - Check VM NSG rules</strong>

If you click on the VM \ Networking you'll see an entry named SecurityCenter-JITRule-292389437-9DDC142A624B43E8903EC815DA81234E referring to the JIT request you've submitted and that is in place with high priority.

<a href="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/34.png" target="_blank" rel="noopener"><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/34.png" /></a>

For this test I disabled Azure default settings (allow tcp from any to VM on tcp ort 3389 / RDP)

You can also enable JIT within the VM
<ul>
	<li>select the VM</li>
	<li>go to Settings \ Configuration and follow the wizard from there</li>
</ul>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/vmresetpass/38.png" />

If you can not access the VM with your admin account you can reset the VM password. Learn how - click here.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
