---
layout: post
title: Azure - CIS Hardened Images
date: 2020-05-25 12:30
author: beierca
comments: true
categories: [Administration, Azure, CIS, hardening, images, OS, Security, Windows Server]
---
<p style="text-align:justify;">Hi there</p>
Did you know you have CIS Hardened Images available on Azure Marketplace o deploy on your environment?
<p style="text-align:justify;">CIS Hardened Images, also known as virtual machine images, allow the user to spin up a securely configured, or hardened, virtual instance of many popular operating systems to perform technical tasks without investing in additional hardware and related expenses. As mentioned at <a href="https://www.cisecurity.org/blog/cis-hardened-images-now-in-microsoft-azure-marketplace/" target="_blank" rel="noopener">https://www.cisecurity.org/blog/cis-hardened-images-now-in-microsoft-azure-marketplace/</a></p>
<img class="" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/azurecertified.jpg" width="168" height="168" />
<p style="text-align:justify;"><a href="https://www.cisecurity.org/services/hardened-virtual-images/">CIS Hardened Images</a> help organizations around the world bring the secure configurations of the <a href="https://www.cisecurity.org/cis-benchmarks/">CIS Benchmarks</a> to the cloud. Available on <a href="https://www.cisecurity.org/hardened-images/">multiple platforms</a> (and for over a dozen technologies), learn more about how CIS Hardened Images can help you start secure and stay secure.</p>
<img class="" style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/cisbenchmarks.jpg" width="278" height="169" />
<p style="text-align:justify;">Some of the common threats that can be mitigated by using a CIS Hardened Image include:</p>

<ul style="text-align:justify;">
	<li>Denial of service</li>
	<li>Insufficient authorization</li>
	<li>Overlapping trust boundaries threats</li>
</ul>
<p class="">The CIS benchmarks contain two levels, each with slightly different technical specifications:</p>

<ul>
	<li><span class="inner-wrap"><strong>Level 1</strong> – Recommended, minimum security settings that should be configured on any system and should cause little or no interruption of service or reduced functionality</span></li>
	<li><span class="inner-wrap"><strong>Level 2</strong> – Recommended security settings for highly secure environments and could result in some reduced functionality.</span></li>
</ul>
Microsoft Azure <a href="https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=center%20for%20internet%20security&amp;page=1&amp;filters=partners%3Bpay-as-you-go%3Bwindows" target="_blank" rel="noopener">Marketplace</a> offers currently (May 21st 2020)
<ul>
	<li>17 Linux-based CIS images</li>
	<li>10 Windows-based CIS images</li>
</ul>
<strong>Quick test deployment using Windows 2019 CIS image</strong>
<p style="text-align:justify;">Version: CIS Microsoft Windows Server 2019 Benchmark L1</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/2.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/3.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/4.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/5.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/6.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/7.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/8.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/9.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/10.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/11.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/12.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/13.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/14.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/15.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/16.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/17.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/18.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/19.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/50.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/51.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/52.png" />
<p style="text-align:justify;">Admin User &amp; Password: During this VM setup using CIS image set the default admin user with standard password "P@ssw0rd@2020"</p>
<p style="text-align:justify;">After the VM is deployed, try to change the VM password to "P@ssw0rd@2020#" it fails</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/27.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/28.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/29.png" />

&nbsp;
<p style="text-align:justify;">Create a 16 character long &amp; strong password and updated it.
Password: <strong>6-U26qY5UZKR&amp;=9.</strong>  generated using <a href="https://passwordsgenerator.net" target="_blank" rel="noopener">https://passwordsgenerator.net</a> website</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/31.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/32.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/33.png" />

&nbsp;
<p style="text-align:justify;">Log in the VM</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/20.png" />

See CIS hardening in action

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/36.png" />

UAC

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/37.png" />
<p style="text-align:justify;">Check the folder C:\CIS Hardening Report\</p>
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/38.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/39.png" />

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/40.png" />

<strong>CIS Benchamarks - Security Configuration Assessment Report</strong>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/42.png" />

&nbsp;
<p style="text-align:justify;">There are 2 (two files) on this directory</p>

<ul style="text-align:justify;">
	<li><a href="https://thiagobeierblog.blob.core.windows.net/files/CIS%20Hardening%20Report/CIS-CAT_Results.html" target="_blank" rel="noopener">CIS-CAT_Results.html</a></li>
	<li><a href="https://thiagobeierblog.blob.core.windows.net/files/CIS%20Hardening%20Report/WS2019_EXCEPTIONS.txt" target="_blank" rel="noopener">WS2019_EXCEPTIONS.txt</a></li>
</ul>
<strong>All CIS images available on Azure marketplace</strong>

<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/azure/cis/1.png" />

&nbsp;
<p style="text-align:justify;"><strong>References</strong></p>
<p style="text-align:justify;"><a href="https://www.cisecurity.org/blog/cis-hardened-images-now-in-microsoft-azure-marketplace/" target="_blank" rel="noopener">https://www.cisecurity.org/blog/cis-hardened-images-now-in-microsoft-azure-marketplace/</a></p>
<p style="text-align:justify;"><a href="https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=center%20for%20internet%20security&amp;page=1&amp;filters=partners%3Bpay-as-you-go" target="_blank" rel="noopener">https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=center%20for%20internet%20security&amp;page=1&amp;filters=partners%3Bpay-as-you-go</a></p>
<p style="text-align:justify;"><a href="https://www.microsoft.com/security/blog/2017/10/12/easily-create-securely-configured-virtual-machines/" target="_blank" rel="noopener">https://www.microsoft.com/security/blog/2017/10/12/easily-create-securely-configured-virtual-machines/</a></p>
Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
