---
layout: post
title: Renovando Certificado do Exchange 2013/2016: SHA-256
date: 2016-04-04 20:09
author: beierca
comments: true
categories: [Certificado Digital, Exchange &amp; Office Server]
---
Olá pessoal para quem está tendo dificuldades com o tema, após consultarmos forum technet, canal de parceiros Microsoft que apoia as entregas em projetos no Brasil temos o seguinte:

Atualmente não existe por parte do Exchange a geração da requisição do certificado já com SHA256. O que para muitos administradores de ambientes com navegadores que irão alertar a respeito de certificados emitidos com SHA1.

Testamos com o Exchange 2013 Cumulative Update 10, 11 e o mais novo 12

<strong>Gere a requisição do certificado no exchange</strong>

New-ExchangeCertificate –Server cas1 –GenerateRequest –FriendlyName Exchange13COMPANY –PrivateKeyExportable $true –SubjectName “c=BR, s=DF, l=BRASILIA, o=COMPANY, ou=DGPTI, cn=correio.domain.com” –DomainName  correio.domain.com,correio.domain.local,autodiscover.domain.com,domain.com –RequestFile “\\cas1\temp\cert\CertRequestExc13.req”

<strong>Validação dos dados do certificado </strong>

copie e cole os dados (conteudo do seu certifiado) e clique em verificar.

<a href="https://cryptoreport.websecurity.symantec.com/checker/views/csrCheck.jsp">https://cryptoreport.websecurity.symantec.com/checker/views/csrCheck.jsp</a>

A solução que temos atualmente é esta conforme o artigo

<a href="http://www.workingsysadmin.com/renewing-exchange-2013-certificates-sha-256-style/">http://www.workingsysadmin.com/renewing-exchange-2013-certificates-sha-256-style/</a>

Procurando informações sobre os updates do Exchange?

Segue link <a href="https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx">https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx</a>

Até mais,

Thiago Beier
