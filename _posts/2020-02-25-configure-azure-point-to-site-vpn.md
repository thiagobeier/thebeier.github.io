---
layout: post
title: Configure Azure Point-to-Site VPN
date: 2020-02-25 06:00
author: beierca
comments: true
categories: [Azure, azure vpn, point-to-site vpn, resource group, Security]
---
Hi there

In this article we're gonna explore how to create an Azure Point-to-Site VPN for Remote Access
<h4 class="text-heading3">Connect to your Azure virtual networks from anywhere</h4>
Point-to-Site VPN allows you to connect to your virtual machines on Azure virtual networks from anywhere.
<ol>
	<li>Connect to your Azure Subscription https://portal.azure.com</li>
</ol>
<strong>Prerequisites</strong>
<ol>
	<li>Under your Resource Group</li>
	<li>Create your VNET (Virtual Network)</li>
	<li>Create at least 02 subnets on your VNET
<ol>
	<li>Address Space (IP: <strong>10.120.0.0/16</strong>)
<ol>
	<li style="list-style-type:none;">
<ol>
	<li><strong>Frontend</strong> subnet (IP: <strong>10.120.1.0/24</strong>)</li>
	<li><strong>Gateway</strong> subnet (IP: <strong>10.120.255.0/24</strong>)<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/1.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/2.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/3.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/4.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/5.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/6.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/7.PNG" />
<img /></li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
</ol>
<strong>Virtual Network Gateway Setup</strong>
<ol>
	<li><strong>Create a Virtual Network Gateway resource object</strong>
<ol>
	<li style="list-style-type:none;">
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>Name: Virtual network gateway</li>
	<li>SKU: basic</li>
	<li>Public IP address: define a static one (create a new one)</li>
	<li>Resource Group: pick your default resource group where your VMs are being hosted.<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/8.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/9.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/10.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/11.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/12.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/13.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/14.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/15.PNG" /></li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
	<li><strong>After your Virtual Network Gateway is created go to this resource and check the following information (should be empty)</strong>
<ol>
	<li style="list-style-type:none;">
<ol>
	<li>select Point-to-site configuration</li>
	<li>configure
<ol>
	<li>
<div class="azc-form-labelcontainer azc-text-label">Address pool:</div></li>
	<li>Tunnel type:</li>
	<li>Authentication type:</li>
	<li>Root certificates:
<ol>
	<li>Name</li>
	<li><span id="fxgridcol10" class="azc-grid-headerlabel azc-grid-headerCell" role="columnheader">Public certificate data</span></li>
</ol>
</li>
	<li>Revoked certificates
<ol>
	<li>Name</li>
	<li>Thumbprint</li>
</ol>
</li>
</ol>
</li>
	<li>Allocated IP addresses<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/16.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/17.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/18.PNG" /></li>
</ol>
</li>
</ol>
</li>
	<li><strong>Setup the Virtual Network Gateway SSl Root Cert and Child Cert using self-signed certificate</strong>
<ol>
	<li>Create a self-signed root certificate
Open PowerShell as an Administrator and run the following script
<pre>#Root Certificate
$date_now = Get-Date
$extended_date = $date_now.AddYears(10)
$cert = New-SelfSignedCertificate -Type Custom -KeySpec Signature `
-Subject “CN=2020P2SRootCert” -KeyExportPolicy Exportable `
-HashAlgorithm sha256 -KeyLength 2048 `
-CertStoreLocation “Cert:\CurrentUser\My” -KeyUsageProperty Sign -KeyUsage CertSign -Notafter $extended_date</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/1.PNG" />

<img />
This will create root cert and install it under current user cert store valid for 10 years.</li>
	<li>Generate a client certificate
Open PowerShell as an Administrator and run the following command:
<pre>#Client Certificate
New-SelfSignedCertificate -Type Custom -DnsName 2020P2SChildCert -KeySpec Signature `
-Subject “CN=2020P2SChildCert” -KeyExportPolicy Exportable `
-HashAlgorithm sha256 -KeyLength 2048 `
-CertStoreLocation “Cert:\CurrentUser\My” `
-Signer $cert -TextExtension @(“2.5.29.37={text}1.3.6.1.5.5.7.3.2”) -Notafter $extended_date</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/3.PNG" />
<pre>Get-ChildItem -Path "Cert:\CurrentUser\My\" | select issuer,subject,thumbprint | where-object { $_.subject -like "*2020*"}</pre>
</li>
	<li>Export the root certificate public key (.cer)
<pre>#Export SSL Cert to PFX
$mypwd = ConvertTo-SecureString -String "P@ssw0rd" -Force -AsPlainText
Get-ChildItem -Path Cert:\CurrentUser\My\93B0F586E79C3003C02B70FCCA32F361207A19AE | Export-PfxCertificate -FilePath 2020SslChildCert.pfx -Password $mypwd #client
Get-ChildItem -Path Cert:\CurrentUser\My\180D81C8631257C13880327AE028DAB90CB6861C | Export-PfxCertificate -FilePath 2020SslRootCert.pfx -Password $mypwd #root</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/5.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/p2s/7.PNG" /></li>
	<li>Export the client certificate
<strong><span style="color:#ff0000;">Tip</span></strong>: change the ROOT and Client certificate Expire dates to 5, 10 or 15 years otherwise you'll have to regenerate them again in 1 year (default option)</li>
</ol>
</li>
	<li><strong>Setup the Virtual Network Gateway</strong>
<ol>
	<li>select Point-to-site configuration
<ul>
	<li>Click on the newly created VPN gateway connection.</li>
	<li>Then in a new window click on Point-to-site configuration</li>
	<li>Click on <strong>Configure Now</strong></li>
	<li>In new window type IP address range for VPN address pool. In this demo, I will be using <strong>10.120.100.0/24</strong>. For tunnel, type use both <strong>SSTP &amp; IKEv2</strong>. Linux and other mobile clients by default use IKEv2 to connect. Windows also use <strong>IKEv2</strong> first and then try <strong>SSTP</strong>. For authentication type use <strong>Azure Certificates</strong>.</li>
	<li>In the same window, there is a place to define a root certificate. Under root certificate name type the cert name and under public certificate data, paste the root certificate data ( you can open cert in notepad to get data).</li>
	<li>Then click on <strong>Save</strong> to complete the process.</li>
</ul>
<strong>Note</strong>: when you paste certificate data, do not copy —–BEGIN CERTIFICATE—– &amp; —–END CERTIFICATE—– text

<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/19.PNG" /><img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/20.PNG" /></li>
</ol>
</li>
	<li><strong>Testing VPN connection (quick</strong>
<ol>
	<li>Log in to Azure portal from the machine and go to VPN gateway config page.</li>
	<li>On that page, click on <strong>Point-to-site configuration</strong>.</li>
	<li>After that, click on <strong>Download VPN client</strong>.</li>
</ol>
</li>
</ol>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/24.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/22.PNG" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/vnet/21.PNG" />

<strong>References</strong>
https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal
https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-certificates-point-to-site
https://docs.microsoft.com/en-us/azure/vpn-gateway/point-to-site-how-to-vpn-client-install-azure-cert
