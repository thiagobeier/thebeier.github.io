---
layout: post
title: Hyper-v descomplicado
date: 2013-08-01 03:24
author: beierca
comments: true
categories: [Hyper-v]
---
Neste post iremos abordar como configurar um "notebook" para ser uma boa ferramenta de trabalho rodando <a href="http://blogs.technet.com/b/keithmayer/archive/2012/09/07/getting-started-with-hyper-v-server-2012-hyperv-virtualization-itpro.aspx">Hyper-v 3.0</a> em <a href="http://www.microsoft.com/pt-br/windows/enterprise/products-and-technologies/windows-8/default.aspx">Microsoft Windows 8 Enterprise</a>
<ul>
	<li>Notebook com no mínimo 08 GB, recomendo utilizar 16 GB</li>
	<li>Disco SSD com no mínimo 300 GB, recomendo utilizar um de 500 GB</li>
	<li>Placa de rede ethernet 10/100/1000</li>
	<li>Placa de rede wireless</li>
</ul>
<strong>Passos
</strong>

<strong>1 – Instale o Sistema Operacional e drivers e verifique as opções de seu hardware para virtualização
</strong>

Utilize do <em>plug-in</em>
<a href="https://www.grc.com/securable.htm">securable</a> e valide as configurações do seu hardware

<strong>2 – Habilite a <em>feature</em> de Hyper-v
</strong>

<img alt="" src="http://thiagobeier.files.wordpress.com/2013/08/080113_0324_hypervdesco1.jpg" />

*aguarde a reinicialização para prosseguir.

<strong>3 – Abra a console de gerenciamento do Hyper-v e configure o "virtual switch"
</strong>

Crie um virtual switch para cada interface de rede (01 para a rede local cabeada "interface física ethernet" e 01 para a rede wireless "interface wireless")

<img alt="" src="http://thiagobeier.files.wordpress.com/2013/08/080113_0324_hypervdesco2.png" />

<img alt="" src="http://thiagobeier.files.wordpress.com/2013/08/080113_0324_hypervdesco3.png" />

<img alt="" src="http://thiagobeier.files.wordpress.com/2013/08/080113_0324_hypervdesco4.png" />

Obs.: a partir de agora você pode atribuir interfaces de rede para as suas maquinas virtuais do tipo EXTERNA (com acesso a sua rede em casa, trabalho, internet)

Caso precise de mais switches virtuais (você poderá criar novos do tipo interno e privados) com o comando <a href="http://technet.microsoft.com/en-us/library/hh848455.aspx">New-VMSwitch</a>

<strong>4 – Isolando laboratórios e criando padrões de maquinas virtuais
</strong>
<ol>
	<li>
<div><strong>Crie as maquinas virtuais modelo (template)
</strong></div>
<ol>
	<li>Crie uma nova máquina virtual "template-XPTO"</li>
	<li>Instale o sistema operacional desejado</li>
	<li>Instale o <em>host</em>
<em>integration services</em></li>
	<li>
<div>Execute o sysprep em modo OOBE e Desligar (shutdown)</div>
<ol>
	<li>Navegue ate <span style="color:red;">c:\Windows\System32\sysprep</span></li>
	<li>Execute: <span style="color:red;">sysprep /generalize /oobe /shutdown</span></li>
</ol>
</li>
	<li>
<div>Após o desligamento copie o seu arquivo <a href="http://technet.microsoft.com/en-us/library/hh831446.aspx">.vhdx</a> (MS Windows 8.x) para a pasta Ex: E:\hyperv\parent\</div>
<ol>
	<li>Esta pasta RAIZ toda e seus arquivos devem estar como somente leitura (read only)</li>
</ol>
</li>
	<li>Repita estes passos para quantas maquinas virtuais distintas que serão utilizadas como template para Cliente-XP, Cliente-7, Cliente-8, Server2003x86, Server2003x64, Server2008R2sp1, Server2012full, etc.</li>
</ol>
</li>
	<li>
<div><strong> Via Powershell otimize a criação de suas VMs (maquinas virtuais)
</strong></div>
<ol>
	<li>
<div>Execute o Powershell como administrador</div>
<ol>
	<li>
<div>Crie uma nova máquina virtual com o nome OCS-client3 com 1 gb de ram sem vhd apontando para o caminho E:\hyper-v\ com o virtual switch VSocs</div>
<ol>
	<li><span style="color:red;">New-VM -MemoryStartupBytes 1gb -Name OCS-client3 -NoVHD -Path E:\hyper-v -SwitchName VSocs –Verbose
</span></li>
</ol>
</li>
	<li>
<div>Crie um virtual switch para essa rede de laboratório com o nome VSocs do tipo interno</div>
<ol>
	<li><span style="color:red;">New-VMSwitch -Name VSocs -SwitchType Internal -MinimumBandwidthMode Default -Verbose
</span></li>
</ol>
</li>
	<li>
<div>Crie um novo disco VHDX diferencial a partir do disco PAI (origem \ parente) que foi criado no item A acima</div>
<ol>
	<li><span style="color:red;">New-VHD –ParentPath E:\hyper-v\parent\winxp.vhd –Path E:\hyper-v\OCS-client3\OCS-client3.vhd -Differencing
</span></li>
</ol>
</li>
	<li>
<div>Adicione esse disco VXDX diferencial a sua nova máquina virtual criada</div>
<ol>
	<li><span style="color:red;">Add-VMHardDiskDrive OCS-client3 -Path E:\hyper-v\OCS-client3\OCS-client3.vhd
</span></li>
</ol>
</li>
	<li>
<div>Inicie a VM após ter o disco adicionado</div>
<ol>
	<li><span style="color:red;">Start-VM OCS-client3
</span></li>
</ol>
</li>
</ol>
</li>
</ol>
</li>
	<li>
<div><strong>O mais importante para um bom laboratório
</strong></div>
<ol>
	<li>
<div>Desenhe o que você quer fazer</div>
<ol>
	<li><img alt="" src="http://thiagobeier.files.wordpress.com/2013/08/080113_0324_hypervdesco5.jpg" /></li>
</ol>
</li>
	<li>Crie uma tabela com o nome do servidor, virtual switch, sistema operacional, rede (interna, dmz, internet) e funções</li>
</ol>
</li>
</ol>
<div style="margin-left:108pt;">
<table style="border-collapse:collapse;" border="0"><col style="width:125px;" /> <col style="width:125px;" /> <col style="width:125px;" /> <col style="width:125px;" /> <col style="width:125px;" />
<tbody valign="top">
<tr>
<td style="padding-left:7px;padding-right:7px;border:solid .5pt;"><strong>Servidor</strong></td>
<td style="padding-left:7px;padding-right:7px;border-top:solid .5pt;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;"><strong>Virtual switch</strong></td>
<td style="padding-left:7px;padding-right:7px;border-top:solid .5pt;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;"><strong>Sistema operacional</strong></td>
<td style="padding-left:7px;padding-right:7px;border-top:solid .5pt;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;"><strong>Rede (int, dmz, ext)</strong></td>
<td style="padding-left:7px;padding-right:7px;border-top:solid .5pt;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;"><strong>Funções</strong></td>
</tr>
<tr>
<td style="padding-left:7px;padding-right:7px;border-top:none;border-left:solid .5pt;border-bottom:solid .5pt;border-right:solid .5pt;">Dc</td>
<td style="padding-left:7px;padding-right:7px;border-top:none;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;">VSinterno</td>
<td style="padding-left:7px;padding-right:7px;border-top:none;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;">Win2012</td>
<td style="padding-left:7px;padding-right:7px;border-top:none;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;">Int</td>
<td style="padding-left:7px;padding-right:7px;border-top:none;border-left:none;border-bottom:solid .5pt;border-right:solid .5pt;">ADDS + ADCS</td>
</tr>
</tbody>
</table>
</div>
<ol style="margin-left:72pt;">
	<li>Tenha também uma tabela de nomes de <a href="http://technet.microsoft.com/pt-br/Library/cc753635(v=ws.10).aspx">DNS e tipos de registros</a></li>
	<li>Leia sempre links e referencias oficiais sobre o produto, função a ser testado leia blogs e artigos fundamentados</li>
	<li>Conhece o <a href="http://social.technet.microsoft.com/wiki/contents/articles/1262.test-lab-guides.aspx">Test Lab Guides</a>?</li>
</ol>
Bons estudos

Thiago Beier

<a href="https://twitter.com/thiagobeier"><span style="color:#da1071;font-family:Arial;font-size:10pt;background-color:white;">https://twitter.com/thiagobeier</span></a><span style="color:#333333;font-family:Arial;font-size:10pt;background-color:white;">
<a href="https://mcp.microsoft.com/authenticate/validatemcp.aspx"><span style="color:#da1071;">https://mcp.microsoft.com/authenticate/validatemcp.aspx</span></a>
Transcript ID: 1049813
Access Code: wantpfe2MSFT</span>
