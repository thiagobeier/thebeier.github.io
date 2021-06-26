---
layout: post
title: SCCM client tips and tricks
date: 2020-02-29 08:00
author: beierca
comments: true
categories: [cache, psexec, SCCM, scripts, sysinternals, System Center]
---
Hi there

I run into a client ticket where he asked to change the client cache after an Office 365 Pro Plus click-to-run failed.

My initial thought was the default client push configuration settings.

Then I checked the following:
<ul>
	<li>SCCM client push settings at SCCM console <strong>\Administration\Overview\Site Configuration\Sites</strong></li>
	<li>SCCM client cache at a domain joined workstation</li>
	<li>Simulated the Office 365 Pro Plus click-to-run on a sandbox machine (that can be also a real user domain joined workstation) which you have access to</li>
	<li>Restarted the sccm services (SMS Agent Host service) under services.msc (Windows Services Management Console)</li>
</ul>
<em><strong>SCCM console view
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/1.png" />

<em><strong>SCCM services on windows
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/5.png" />

<strong>Fixes</strong>
<ol>
	<li>VBS script to clear cache, set new value</li>
	<li>PowerShell Script to clear cache and set new value</li>
	<li>Change default client push settings at SCCM for any "agent / client" automatic deployment</li>
	<li>Created a script at SCCM console to make changes on the fly (have in mind that in large environments that might take longer to fix a simple step missed during SCCM deployment)</li>
	<li>Script to clear SCCM local cache (c:\windows\ccmcache\ folder)</li>
	<li>Restart SMS Agent Host (SCCM agent service remotely)</li>
</ol>
<span style="color:#ff0000;">Tip!
</span><strong>Use psexec</strong> to run VBS or Powershell remotely against any domain joined workstation you might need to. To do so, please download the PsExec from Sysinternals <a href="https://docs.microsoft.com/en-us/sysinternals/downloads/psexec">here</a> or the full Sysinternals Suite <a href="https://download.sysinternals.com/files/SysinternalsSuite.zip">here</a>.

open a <strong>cmd.exe</strong> as administrator from the SCCM console (primary server or any DP "Distribution Point" available on network).

<em>Do the following</em>

Copy the sccm-cache.vbs to the desired workstation on its <strong>\\dESKTOP-LVTEST\admin$</strong> share. Remember that the <strong>admin$ share</strong> it's the <strong>c:\windows\</strong> folder on the target machine where you run your psexec.exe remote against.
<pre>psexec.exe \\dESKTOP-LVTEST "c:\windows\inceraase-sccm-cache.vbs"
psexec.exe \\dESKTOP-LVTEST "c:\windows\SCCM-client-wmi-queries.cmd"
psexec.exe \\dESKTOP-LVTEST "c:\windows\sccm-clear-local-cache.vbs"</pre>
<strong><span style="color:#ff0000;">Tip!</span>
Restarting the SCCM</strong> service remotely also force SCCM agent/client to download its policies from MP (Management Point) - one single command.
<pre>psexec.exe \\dESKTOP-LVTEST net stop ccmexec &amp;&amp; psexec.exe \\dESKTOP-LVTEST net start ccmexec</pre>
You can repeat the same psexec remote to clear SCCM cache and to trigger agent from WMI command line if you don’t want to open the configuration manager properties.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/4.png" />

<strong>Files used (copy from your SCCM server)</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/2.png" />

<strong>To the workstation over the network (remember the admin$ it's the c:\windows\ folder locally)</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/3.png" />

<strong>Logs files</strong>

Please look at the logs files at CCM\Logs\ folder at the client as well as at ccmsetup\logs\ and if you need ccmcache\ folder to make sure all the scripts covered at this post worked properly.

<em><strong>SCCM main folders at the client
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/6.png" />

<em><strong>CCM Logs folder
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/7.png" />

<em><strong>CCMSetup Logs folder
</strong></em>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/sccm/8.png" />

<a href="https://thiagobeierblog.blob.core.windows.net/files/sccm-scripts.zip">Files Download</a>

thanks,

<strong>Thiago Beier</strong>
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
