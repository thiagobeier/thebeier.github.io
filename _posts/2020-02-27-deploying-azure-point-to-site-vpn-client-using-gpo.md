---
layout: post
title: Deploying Azure Point-to-Site VPN client using GPO
date: 2020-02-27 06:30
author: beierca
comments: true
categories: [Azure, azure vpn, customization, point-to-site vpn]
---
Hi there

I got a ticket recently to push Azure Point-to-Site VPN cilent using <a href="https://docs.microsoft.com/en-us/previous-versions/windows/desktop/policy/group-policy-architecture">GPO</a> (Group Policy Objects) and got this successful by doing the following:

Configure Azure Point-to-Site VPN

Download Azure Point-to-Site VPN client executable from <a href="https://portal.azure.com">https://portal.azure.com</a>

Download <a href="https://gallery.technet.microsoft.com/scriptcenter/PS2EXE-GUI-Convert-e7cb69d5">PS1-To-Exe</a>

Download <a href="https://www.win-rar.com/download.html?&amp;L=0">Winrar</a>

Decompress the Azure Point-to-Site VPN client to <strong>c:\temp\azurevpnclient\</strong> folder

<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/19.PNG" />

Copy the setup-vpn.ps1 file to <strong>c:\temp\azurevpnclient\</strong> folder

<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/20.PNG" />

Run the <strong>PS1-To-Exe</strong> and search for the setup-vpn.ps1 at the <strong>c:\temp\azurevpnclient\</strong> folder and follow the Wizard until you complete this step

<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/17.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/15.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/16.PNG" />

Now you have the <strong>setupazurevpn.exe</strong> file at <strong>c:\temp\azurevpnclient\</strong>

Create 02 GPOs in ADDS (Active Directory Domain Services)

<strong>GPO #1 Name: Push-AzureVPNClient</strong>

this GPO will push the azure VPN client setup file silently to computers - file created on step 7 above

<strong>GPO #2 Name: Push-AzureVPNPFXfile</strong>

this GPO will push the azure PFX file silently to users with the self-signed  SSL certificate used on step 1 above

on my LAB I used one single GPO to push both the SSL certificate and the Azure VPN client

<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/21.png" />

<strong><span style="color:#0000ff;">Tip: </span></strong><span style="color:#0000ff;"><span style="color:#000000;">This same custom deployment can be pushed by SCCM CB (System Center Configurations Manger Current Branch)</span></span>

<span style="color:#ff0000;"><strong>Attention: </strong><span style="color:#000000;">This custom deployment is not supported by Microsoft.</span></span>

<a href="https://thiagobeierblog.blob.core.windows.net/posts/p2s/setupvpn.ps1">PowerShell File Download</a>

References
<a href="https://azure.microsoft.com/en-ca/services/vpn-gateway/">https://azure.microsoft.com/en-ca/services/vpn-gateway/</a>

<strong style="color:var(--color-text);">Follow Me
</strong><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
