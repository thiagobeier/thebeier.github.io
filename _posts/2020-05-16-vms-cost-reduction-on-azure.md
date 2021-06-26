---
layout: post
title: VM's Cost reduction on Azure
date: 2020-05-16 11:00
author: beierca
comments: true
categories: [Administration, Automation, Azure, cost management, IAAS, Powershell, vms]
---
Hi there
<p style="text-align:justify;">In this post I'm talking about different ways to save money on monthly invoices on Azure. Due to pandemic moment we're living on several clients SMBs, Medium and Large Enterprise are implementing several processes and analysis to identify and reduce costs on Azure workloads and Virtual Machines are where it's kicked off.</p>
<p style="text-align:justify;">It is known that on several companies' strategies and its cloud-based scenarios there's a trend and standardization around Azure Resources by type, business cost center or even environment such User Acceptance Test (UAT), Development (DEV) and Production (PROD).</p>
<p style="text-align:justify;">We also talked about <strong>Azure TAGS</strong> to take as a benefit on identifying resources on Azure by Environment and Cost Center improving invoice analysis on Azure Costs Management.</p>
<p style="text-align:justify;">There are also other ways to prevent costs with IAAS (VMS) on Azure such as:</p>

<ol>
	<li style="text-align:justify;"><strong>Start and Stop VMS on a scheduled windows</strong> / time of the day where not all servers need to be running 24x7 and for those servers you can use <a href="https://docs.microsoft.com/en-ca/azure/automation/automation-intro" target="_blank" rel="noopener">Azure Automation</a>.</li>
	<li style="text-align:justify;"><strong>Vertical Resize</strong> where there's an specific need to resize your VMS during a short and predetermined period of time where it's known that those VMs are not used with that increased size all the time (lunch time, after-hours or weekends). For those scenarios, you can resize the VM using <a href="https://docs.microsoft.com/en-ca/azure/virtual-machines/windows/sizes" target="_blank" rel="noopener">Azure Automation</a>. Check this <a href="https://github.com/l3oferreira/azure-automation-runbooks/blob/master/runbooks/vm-scale.ps1" target="_blank" rel="noopener">powershell script</a> modified from another one created by <a href="https://github.com/SiebertT">Siebert Timmermans</a>. However, if have never configured a runbook on Azure please follow these guidelines for updating the PowerShell modules (some commonly used modules are already available, but need to be updated to use new functionality), configuration and scheduling of the runbook:
https://docs.microsoft.com/en-ca/azure/automation/automation-update-azure-modules
https://docs.microsoft.com/en-ca/azure/automation/learn/automation-tutorial-runbook-textual-powershell
&nbsp;

In order to be successful on scaling of virtual machine, some practices need to be considered:
<ul>
	<li><span style="color:var(--color-text);">Resizing is restricted to the existing sizes in a VM family , as well as their availability in the region where it was implemented;</span></li>
	<li><span style="color:var(--color-text);">Always prefer to resize your VM in the same series / VMs' family, making chages only on their sizes (for example, from Basic A0 to Basic A4);</span></li>
	<li><span style="color:var(--color-text);">Within each VM family, some sizes of VMs require a minimum managed disk. Always choose to create the virtual machine at first in its maximum dimension, so that there are no errors in later resizing it;</span>

<span style="color:var(--color-text);">The following is a list of design pairs that can be used in the vertical design runbook:</span>

https://docs.microsoft.com/en-ca/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-vertical-scale-reprovision
&nbsp;</li>
</ul>
</li>
	<li style="text-align:justify;"><strong>Use reserved instances</strong>: There are scenarios where servers are critical components for company function where there's no scale up options or where those servers are never shutdown on predefined windows as after-hours, weekends as mentioned previously. For those you have the option to pay-as-you-go and then use reserved instances. At this model there's a commitment on the VM usage and consumption up to 3 years, reducing costs up to 72% on the same VM size it charged monthly.
https://azure.microsoft.com/en-ca/pricing/reserved-vm-instances/
https://docs.microsoft.com/en-ca/azure/virtual-machines/windows/prepay-reserved-vm-instances</li>
	<li><strong>Hybrid benefit</strong>
<p style="text-align:justify;">For companies that have purchased Windows Server licenses prior to a cloud-based migration these licenses can be used in the cloud saving company money. Further reducing the cost of VMs (together with reserved instances, the reduction can reach 80%), whether using the plan for consumption or by reserved instances (and yes, the hybrid benefit also applies. applies in SQL Server licensing).</p>
<p style="text-align:justify;">In order to access the benefit, Windows Server licenses must have active Software Assurance and can be applied to existing VMs, using the retroactive feature.</p>
</li>
</ol>
&nbsp;

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
