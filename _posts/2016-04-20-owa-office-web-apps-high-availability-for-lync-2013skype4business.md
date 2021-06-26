---
layout: post
title: OWA – Office Web Apps high availability for Lync 2013/Skype4Business
date: 2016-04-20 13:06
author: beierca
comments: true
categories: [Communication]
---
<h5><a name="Topology"></a>Topology</h5>
<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe1.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe1.png?w=614" alt="" /></a><a href="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe1.png?w=500">
</a>
<h5><a name="Pre-requisitos"></a>Prerequisites</h5>
<ul>
	<li>ADDS – Active Directory Domain Services.</li>
	<li>Lync Server 2013 or Skype For Business deployed in the environment</li>
	<li>ADCS – Active Directory Certificate service for certificates request based in predefined templates</li>
</ul>
Do the same below to all servers that will run WAC (OWA – office web apps)
<ul>
	<li>Open a PowerShell as Administrator and then copy and paste</li>
	<li>Add-WindowsFeature NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Web-Includes,Web-Static-Content,Web-Windows-Auth,Web-Mgmt-Console,InkAndHandwritingServices -source r:\sources\sxs -restart</li>
	<li>Download Office Web Apps from <a href="http://www.microsoft.com/en-us/download/details.aspx?id=35489">http://www.microsoft.com/en-us/download/details.aspx?id=35489</a></li>
	<li>Download Office Web Apps updates from <a href="http://support.microsoft.com/kb/2760445">http://support.microsoft.com/kb/2760445</a></li>
	<li>Install also NLB feature on all servers that will run WAC (OWA – Office web apps)</li>
</ul>
&nbsp;
<h5><a name="Configuracao"></a>Configuration</h5>
<strong><em>Requesting needed certificates for WAC (Office Web Apps)</em></strong>

In the first node of this FARM generate the certificate request using mmc.exe , Certificates, Personal and then go to all tasks, advanced operations and select “Create Custom Request”

<strong>Windows + R \ mmc.exe &lt;enter&gt;</strong>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe2.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe2.png?w=614" alt="" /></a>

<strong>Follow the instructions bellow.</strong>

Select Custom Request and click next

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe3.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe3.png?w=614" alt="" /></a>

At Custom Request select the “web server” template, and at “request format” check PKCS #10 and click next

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe5.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe5.png?w=614" alt="" /></a>

Select properties once you have “web server” at Active Directory Enrollment Policy and click properties

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe6.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe6.png?w=614" alt="" /></a>

Select Custom Request and click next

At general TAB name the certificate “officeweb” and click apply

<a href="http://thiagobeier.files.wordpress.com/2013/08/080513_1730_owaofficewe6.png?w=500">
</a>

At the subject TAB select “common name” at type and give the CN name to this certificate

Hm11.home.intranet and click ADD

&nbsp;

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe7.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe7.png?w=614" alt="" /></a>

&nbsp;

At “Alternative name” select DNS as type

Fill with the following names:

Officeweb.home.com.br (your external url that is going to be used to answer the request for WAC)

Officeweb.home.intranet (your internal url that is used to answer for internal request inside your ADDS network/netbios domain)

And also add the host names of the servers where WAC FARM is running.

Hm11.home.intranet

Hm12.home.intranet

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe9.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe9.png?w=614" alt="" /></a>

At the “Private Key” TAB select the key size as 2048

Check “make private key exportable” and click ok or apply

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe10.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe10.png?w=614" alt="" /></a>

After this click NEXT and select the folder to save the request file yourcertreqname.req and click save.

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe11.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe11.png?w=614" alt="" /></a>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe12.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe12.png?w=614" alt="" /></a>
<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe13.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe13.png?w=614" alt="" /></a>

Be sure that your folder path is correct and the file has its own name and file extension .REQ and click FINISH

&nbsp;

Now you can request your certificate at your internal CA (certificate authority) in AD forest.

Access your internal CA url to request the certificate

Select “request a certificate”

Select “advanced certificate request”

Select the option “Submit a certificate request by using a base-64 encoded CMC or PKCS #10, or submit a neweal request by using a base-64 encoded PKCS #7 file”

Open the certificate request file in NOTEPAD, copy the entire data and paste it at the “saved request” \ Base-64-encoded certificate request

<img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe14.png?w=614" alt="" />

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe15.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe15.png?w=614" alt="" /></a>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe16.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe16.png?w=614" alt="" /></a>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe17.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe17.png?w=614" alt="" /></a>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe18.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe18.png?w=614" alt="" /></a>

&nbsp;

Wait to processed and then select DER endoced or Base 64 encoded and click “download certificate”, if you prefer you can click at “download certificate chain” and this file contains the CA root certificates of your CA tree.

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe19.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe19.png?w=614" alt="" /></a>

<em>Import the certificate in the 1st server of the FARM</em>

<em>After that you can export this certificate with its private key to use it (import it) at the 2nd FARM server.</em>

<strong>ATENTIONS</strong>: for each server joined at this FARM you need to name it at the DNS type at the request certificate done in the first steps of this article.

&nbsp;

&nbsp;
<h5><a name="Criando_a_WEBFARM_para_Office_Web_Apps"></a>Deploying the WAC FARM</h5>
&nbsp;

<strong><em>At the first server of the FARM run the following command in the powershell as administrator</em></strong>

New-OfficeWebAppsFarm -InternalUrl <a href="https://officeweb.contoso.net/">https://officeweb.contoso.net</a> –ExternalUrl<a href="https://officeweb.contoso.com/">https://officeweb.contoso.com</a> -CertificateName "office" –AllowHttp

where “office” in red is the “subject name” used during the certificate request.

&nbsp;

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe20.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe20.png?w=614" alt="" /></a>

&nbsp;

For each new server joined at this FARM execute the following command

New-OfficeWebAppsMachine –MachineToJoin "hm11.home.intranet"

If everything is ok at this moment you can run the  “get-officewebappsfarm” command to verify the servers that are joined at this FARM.

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe21.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe21.png?w=614" alt="" /></a>

*sometimes you won’t resolve the server’s name of all servers joined at the FARM and a good Solution is to import again the certificate at IIS or direct using MMC.exe \ certificates \ personal.

<strong> </strong>
<h5><a name="Teste_e_validacao"></a>Validation tasks</h5>
At the first server joined at the FARM, open a browser and hit the following addresses

<a href="https://hm11.home.intranet/hosting/discovery/">https://hm11.home.intranet/hosting/discovery/</a> - local server name

<a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a> - external url

from a remote server (not a FARM server)

https://&lt;server_XXX&gt;.home.intranet/hosting/discovery/ (server name/hosting/discovery/)

<a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a> (external url name/hosting/discovery/) -&gt; this is the name used at the Lync and Skype 4 Business topology publishing.

<em>Validate the NLB function</em>

Shutdown one of the servers joined at this FARM (or only disconnect the NIC or virtual NIC)

Hit the external URL from internet of a remote host  <a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a>

The answer should be like the following.

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe22.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe22.png?w=614" alt="" /></a>

<a name="Configurando_OWA_Office_Web_Apps_para_Ly"></a>Configuring (Office Web Apps) at Lync 2013/Skype 4 Business
<h5><a name="At_the_Lync_Skype_For_Business_front_end_server"></a>At the Lync/Skype For Business front end server</h5>
Use the <em>topology builder</em> at shared components (office web apps servers)

Set it to officeweb.home.com.br, your external URL (visible internally and externally)

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe23.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe23.png?w=614" alt="" /></a>

<a href="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe24.png?w=614"><img src="https://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe24.png?w=614" alt="" /></a>

Publish the topology and follow the instructions

*for LAB please create a dns zone named <a href="http://home.com.br/">home.com.br</a> for internal resolution, at this lab we have 2 dns zones in ADDS home.intranet (ADDS integrated zone) and <a href="http://home.com.br/">home.com.br</a> (your external valid
dns zone).

<strong> </strong>
<h5><a name="Referencias"></a>References</h5>
<ul>
	<li><a href="http://technet.microsoft.com/en-us/library/jj219458.aspx">http://technet.microsoft.com/en-us/library/jj219458.aspx</a></li>
	<li><a href="http://technet.microsoft.com/en-us/library/jj219455.aspx">http://technet.microsoft.com/en-us/library/jj219455.aspx</a></li>
</ul>
