---
layout: post
title: OWA – Office Web Apps em Alta Disponibilidade para Lync 2013
date: 2013-08-05 17:31
author: beierca
comments: true
categories: [Communication]
---
Olá neste artigo iremos mostrar como instalar o OWA (Office Web Apps) em alta disponibilidade.

<strong>Topologia proposta
</strong>

<img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe1.png" alt="" />

<strong>Pré-requisitos
</strong>

Em todos os servidores que irão executar o OWA (Office Web Apps) instale os seguintes pré-requisitos
<p style="margin-left:36pt;"><span style="color:#333333;font-family:Courier New;font-size:9pt;background-color:white;">Add-WindowsFeature NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Web-Includes,Web-Static-Content,Web-Windows-Auth,Web-Mgmt-Console,InkAndHandwritingServices -source r:\sources\sxs -restart</span></p>
<p style="margin-left:36pt;">Baixar e instalar o Office Web Apps - <a href="http://www.microsoft.com/en-us/download/details.aspx?id=35489">http://www.microsoft.com/en-us/download/details.aspx?id=35489</a></p>
<p style="margin-left:36pt;">Baixar e instalar o patch para Office Web Apps - <a href="http://support.microsoft.com/kb/2760445">http://support.microsoft.com/kb/2760445</a></p>
<p style="margin-left:36pt;">Instalar a feature NLB</p>
<strong>Configuração
</strong>
<p style="margin-left:36pt;"><strong><em>Gerando os certificados necessários
</em></strong></p>
<p style="margin-left:36pt;">No 1º Servidor do FARM gerar o certificado para suportar este serviço</p>
<p style="margin-left:36pt;">Abra o MMC (iniciar \ executar \ mmc.exe)</p>
<p style="margin-left:36pt;">Gere uma requisição de certificado</p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe2.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe3.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe4.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe5.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe6.png" alt="" /></p>
<p style="margin-left:36pt;">Pre-selecione os tipos de registros</p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe7.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe8.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe9.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe10.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe11.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe12.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe13.png" alt="" /></p>
<p style="margin-left:36pt;">Tenha certeza de que seu certificado esta ok.</p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe14.png" alt="" /></p>
<p style="margin-left:36pt;">Acesse o caminho de sua CA interna e crie a requisicao de assinatura avançada</p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe15.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe16.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe17.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe18.png" alt="" /></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe19.png" alt="" /></p>
<p style="margin-left:36pt;"><em>Importe o certificado no 1º servidor de sua FARM
</em></p>
<p style="margin-left:36pt;"><em>A partir dele exporte com a chave privada e importe em todos os demais servidores que irão fazer parte desta FARM
</em></p>
<p style="margin-left:36pt;"><span style="color:red;"><strong>ATENÇÃO</strong>: para cada servidor na FARM adicione o nome do mesmo na hora da requisição do certificado.
</span></p>
<strong><em>Criando a WEBFARM para Office Web Apps
</em></strong>
<p style="margin-left:36pt;"><strong><em>No 1o servidor de sua FARM execute o seguinte comando
</em></strong></p>
<p style="margin-left:36pt;"><span style="color:black;"><span style="font-family:Courier New;font-size:9pt;"><span style="background-color:white;">New-OfficeWebAppsFarm -InternalUrl </span>https://officeweb.contoso.net<span style="background-color:white;"> –ExternalUrl </span>https://officeweb.contoso.com<span style="background-color:white;"> -CertificateName "<span style="color:red;">office<span style="color:black;">" –AllowHttp</span></span></span></span>
</span></p>
<p style="margin-left:36pt;"><span style="color:black;font-family:Courier New;font-size:9pt;background-color:white;">Onde "<span style="color:red;">office<span style="color:black;">" em <span style="color:red;">vermelho <span style="color:black;">é o "subject name" utilizado na hora de gerar a requisição do certificado
</span></span></span></span></span></p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe20.png" alt="" /></p>
<p style="margin-left:36pt;">Para cada novo servidor adicionado no FARM (NLB) respondendo por officeweb.home.com.br faça o seguinte</p>
<p style="margin-left:36pt;"><span style="color:black;font-family:Courier New;font-size:9pt;background-color:white;">New-OfficeWebAppsMachine –MachineToJoin "hm11.home.intranet"
</span></p>
<p style="margin-left:36pt;">Se tudo ocorrer bem o retorno do comando "<span style="color:black;font-family:Courier New;font-size:9pt;background-color:white;">get-officewebappsfarm</span>" irá mostrar todos os servidores que estão respondendo por este FARM</p>
<p style="margin-left:36pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe21.png" alt="" /><span style="color:black;font-family:Courier New;font-size:9pt;background-color:white;">
</span></p>
<p style="margin-left:36pt;">*podem ocorrer erros de nao conseguir resolver o nome do host hm11.home.intranet. Solução: validar a importação do certificado emitido anteriormente.</p>
<strong>Teste e validação
</strong>
<p style="margin-left:36pt;">Acesse o caminho da sua FARM OWA no 1º servidor e no nome NLB</p>
<p style="margin-left:36pt;"><a href="https://hm11.home.intranet/hosting/discovery/">https://hm11.home.intranet/hosting/discovery/</a></p>
<p style="margin-left:36pt;"><a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a></p>
<p style="margin-left:36pt;">Acesse o caminho da sua FARM OWA nos próximos nós desta FARM e acesse</p>
<p style="margin-left:36pt;"><a>https://&lt;servidor_XXX&gt;.home.intranet/hosting/discovery/</a></p>
<p style="margin-left:36pt;"><a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a></p>
<p style="margin-left:36pt;"><em>Validando NLB
</em></p>
<p style="margin-left:36pt;">Deslige um dos nós e veja se continua respondendo no endereço <a href="https://officeweb.home.com.br/hosting/discovery/">https://officeweb.home.com.br/hosting/discovery/</a></p>
<strong>    <img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe22.png" alt="" />
</strong>

<strong>Configurando OWA (Office Web Apps) para Lync 2013
</strong>
<p style="margin-left:72pt;">No servidor Front End do Lync 2013</p>
<p style="margin-left:72pt;">Usando o <em>topology builder</em> altere a publicação dos componentes compartilhados (office web apps servers)</p>
<p style="margin-left:72pt;">    Aponte a para o farm nlb officeweb.home.com.br</p>
<p style="margin-left:72pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe23.png" alt="" /></p>
<p style="margin-left:72pt;"><img src="http://thiagobeier.files.wordpress.com/2013/08/080513_1921_owaofficewe24.png" alt="" /></p>
<p style="margin-left:72pt;">Publique a topologia e teste o recurso novo.</p>
<p style="margin-left:72pt;">*para laboratório crie a zona <a href="http://home.com.br">home.com.br</a> no DNS interno para que a resolução funcione corretamente, nesse laboratorio temos duas zonas de DNS home.intranet (integrada ao AD – interna) e <a href="http://home.com.br">home.com.br</a> (domínio existente na internet).</p>
<strong>Referencias
</strong>

<a href="http://technet.microsoft.com/en-us/library/jj219458.aspx">http://technet.microsoft.com/en-us/library/jj219458.aspx</a>

<a href="http://technet.microsoft.com/en-us/library/jj219455.aspx">http://technet.microsoft.com/en-us/library/jj219455.aspx</a>

<a href="https://www.testexchangeconnectivity.com/">https://www.testexchangeconnectivity.com/</a>

&nbsp;
