---
layout: post
title: Renewing Exchange 2013/2016 Certificates and SHA-256 hash algorithm.
date: 2016-04-20 13:13
author: beierca
comments: true
categories: [Exchange &amp; Office Server, Security]
---
I have been seeing people complaining about new features happening after browser updates and after we have searched at TechNet forums. We went to LATAM-PTS a channel for MSFT Partners who help us on delivering projects and this is what we have for this moment.

There is no feature or recent changes in Exchange 2013 (CU12) or Exchange 2016 that allow us to request an Exchange Certificate with SHA256 and all requests done are still bringing SHA1 hash algorithm.

He have tested Exchange (CU10, CU11 and CU12) and Exchange 2016 RTM and (CU01).

<strong>Requesting Exchange Certificate</strong>

New-ExchangeCertificate –Server cas1 –GenerateRequest –FriendlyName Exchange13COMPANY –PrivateKeyExportable $true –SubjectName “c=BR, s=DF, l=BRASILIA, o=COMPANY, ou=ITPRO, cn=mail.domain.com” –DomainName  mail.domain.com,mail.domain.local,autodiscover.domain.com,domain.com –RequestFile “\\cas1\temp\cert\CertRequest.req”

<strong>Validating certificate request content</strong>

Copy and paste the CertRequest.req at the following site to validate all information

<a href="https://cryptoreport.websecurity.symantec.com/checker/views/csrCheck.jsp">https://cryptoreport.websecurity.symantec.com/checker/views/csrCheck.jsp</a>

The solution we have announced on internet is the following

<a href="http://www.workingsysadmin.com/renewing-exchange-2013-certificates-sha-256-style/">http://www.workingsysadmin.com/renewing-exchange-2013-certificates-sha-256-style/</a>

Looking for more Exchange updates and upgrades information?

<a href="https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx">https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx</a>

Once again, thank you.

Thiago Beier
