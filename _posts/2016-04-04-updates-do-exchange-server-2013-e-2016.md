---
layout: post
title: Updates do Exchange Server (2013 e 2016)
date: 2016-04-04 20:15
author: beierca
comments: true
categories: [Exchange &amp; Office Server]
---
Olá a todos, hoje vamos abordar os ultimos updates liberados pela Microsoft para Exchange Server

Ambos foram testados em laboratorio e em produção.

O único sintoma presenciado foi que no <strong>Exchange 2013 saindo do CU3</strong> para o <strong>CU12</strong> direto foi que o serviço "IIS Admin" havia falhado e dando a falsa impressao de que as requisicoes para um servidor mailbox especifico havia falhado retornando tela do OWA e ECP em branco. Após identificada essa falha por meio do "iisreset " reiniciamos o serviço e o ambiente normalizou.

<a href="https://thiagobeier.files.wordpress.com/2016/04/exc13cu12iisadmin.png" rel="attachment wp-att-315"><img class="alignnone size-medium wp-image-315" src="https://thiagobeier.files.wordpress.com/2016/04/exc13cu12iisadmin.png?w=300" alt="exc13cu12iisadmin" width="300" height="67" /></a>

<strong>Exchange Server 2013 Cu12</strong>
<table>
<tbody>
<tr>
<th>Product name</th>
<th>Release date</th>
<th>Build number</th>
</tr>
<tr>
<td><a href="http://go.microsoft.com/fwlink/p/?LinkId=747754">Exchange Server 2013 CU12</a></td>
<td>March 15, 2016</td>
<td>15.00.1178.004</td>
</tr>
</tbody>
</table>
<strong>Exchange Server 2016 Cu1</strong>
<table>
<tbody>
<tr>
<th>Product name</th>
<th>Release date</th>
<th>Build number</th>
</tr>
<tr>
<td><a href="http://go.microsoft.com/fwlink/p/?LinkId=747753">Exchange Server 2016 CU1</a></td>
<td>March 15, 2016</td>
<td>15.01.0396.030</td>
</tr>
</tbody>
</table>
&nbsp;

Link original <a href="https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx">https://technet.microsoft.com/en-us/library/hh135098(v=exchg.150).aspx</a>

&nbsp;

até a próxima.

Thiago Beier
