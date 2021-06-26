---
layout: post
title: Resolvendo problemas de permissões de usuários no IIS
date: 2012-09-15 01:52
author: beierca
comments: true
categories: [IIS]
---
<strong>Descrição</strong>

Neste artigo iremos abordar como resolver problemas de permissão de gravação em diretórios de aplicações web rodando em Servidor IIS (durante upload de arquivos).

<strong>Pre-requisitos</strong>

Servidor IIS – local ou integrado com domínio e com suporte a paginas ASP

Projeto - ASP file upload
<a href="http://www.motobit.com/dlldownload/ScptUtl/ScptUtl-eval-2-3-1-x64.exe">http://www.motobit.com/dlldownload/ScptUtl/ScptUtl-eval-2-3-1-x64.exe</a>

<strong>Instalação</strong>

Instale o servidor windows 2003 X64

Instale o servidor de aplicação via Application Server through Control Panel &gt; Add or Remove Programs &gt; Add/Remove Windows Componentes

Habilite Active Server Pages no World Wide Web Service e pressione OK

Navegue no diretório c:\inetpub\wwwroot\ e crie a pasta root para o seu servidor web de testes (c:\inetpub\wwwroot\siteroot\) depois crie o diretório para <strong><em>uploads</em></strong> de arquivos dentro da pasta root

Instale o projeto ASP file upload executando-o em c:\temp\ ScptUtl-eval-2-3-1-x64

Crie um arquivo asp básico para testes em c:\inetpub\wwwroot\siteroot\

<strong>---INICIO DO CODIGO---</strong>

&lt;%

Dim Form: Set Form = CreateObject("ScriptUtils.ASPForm")

If Form.State = 0 Then

Form.Files.Save "c:\inetpub\wwwroot\siteroot\uploads"

Description = Form("Description") 'Do something with &lt;input name=description&gt;

Else

'Handle other form states, errors.

End If

%&gt;

&lt;Body&gt;

&lt;form method="post" ENCTYPE="multipart/form-data"&gt;

&lt;input type="submit" value="Upload the files &gt;&gt;"&gt;&lt;br&gt;

File 1 : &lt;input type="file" name="File1"&gt;&lt;br&gt;

File 2 : &lt;input type="file" name="File2"&gt;&lt;br&gt;

Description : &lt;input name="Description"&gt;

&lt;/form&gt;

&lt;/body&gt;

<strong>---FIM DO CODIGO---</strong>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image001.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image001" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image001_thumb.png" alt="clip_image001" width="244" height="95" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image003.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image003" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image003_thumb.jpg" alt="clip_image003" width="244" height="122" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image004.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image004" src="http://handsonbrasil.files.wordpress.com/2012/09/clip_image004_thumb.png" alt="clip_image004" width="244" height="223" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image005.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image005" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image005_thumb.png" alt="clip_image005" width="244" height="109" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image006.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image006" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image006_thumb.png" alt="clip_image006" width="244" height="92" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image007.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image007" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image007_thumb.png" alt="clip_image007" width="244" height="107" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image008.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image008" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image008_thumb.png" alt="clip_image008" width="244" height="108" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image010.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image010" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image010_thumb.jpg" alt="clip_image010" width="244" height="175" border="0" /></a>

Acesse o IIS e configure um site padrao para este teste

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image012.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image012" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image012_thumb.jpg" alt="clip_image012" width="244" height="104" border="0" /></a>

Clique em New &gt; Web Site , para adicionar um novo site.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image013.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image013" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image013_thumb.png" alt="clip_image013" width="244" height="189" border="0" /></a>

Digite um nome para para este site

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image014.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image014" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image014_thumb.png" alt="clip_image014" width="244" height="190" border="0" /></a>

Configure parâmetros para “endereço ip pelo qual o site irá responder assim como nome de cabeçalho do site “host header”.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image015.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image015" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image015_thumb.png" alt="clip_image015" width="244" height="190" border="0" /></a>

Configure o caminho físico onde irão ficar os arquivos do site.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image016.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image016" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image016_thumb.png" alt="clip_image016" width="244" height="191" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image017.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image017" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image017_thumb.png" alt="clip_image017" width="244" height="191" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image018.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image018" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image018_thumb.png" alt="clip_image018" width="244" height="190" border="0" /></a>

Configure permissões de Read e Run Scripts para este site.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image019.png"><img style="background-image:none;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image019" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image019_thumb.png" alt="clip_image019" width="244" height="189" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image020.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image020" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image020_thumb.png" alt="clip_image020" width="244" height="190" border="0" /></a>

Navegue em properties e Documents no novo site e configure o arquivo upload.asp como a pagina padrão deste site.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image021.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image021" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image021_thumb.png" alt="clip_image021" width="244" height="243" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image022.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image022" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image022_thumb.png" alt="clip_image022" width="242" height="244" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image023.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image023" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image023_thumb.png" alt="clip_image023" width="244" height="160" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image025.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image025" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image025_thumb.jpg" alt="clip_image025" width="244" height="90" border="0" /></a>

<strong>Teste 1 – carregue o site padrão de teste e tente enviar 02 arquivos para este servidor</strong>

Você recebera a seguinte mensagem de erro

“access denied” = “acesso negado”

Adicione as permissões de escrita “WRITE ACCESS” para o grupo “everyone” / “todos”

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image027.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image027" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image027_thumb.jpg" alt="clip_image027" width="244" height="87" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image029.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image029" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image029_thumb.jpg" alt="clip_image029" width="244" height="175" border="0" /></a>

Nas telas acima voce pode visualizar o processo w3wp.exe (referente ao IIS) tentando criar o arquivo “abc.txt” e teve como resposta acesso negado HANDSON\IUSR_DC1 (o usuário local que o IIS usa para executar o site padrão de testes)

Você encontrará o seguinte erro via Proccess Monitor

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image031.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image031" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image031_thumb.jpg" alt="clip_image031" width="244" height="176" border="0" /></a>

Clique duas vezes sobre a linha que deseja verificar mais informações sobre.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image032.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image032" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image032_thumb.png" alt="clip_image032" width="213" height="244" border="0" /></a>

Veja que o log é mais detalhado

Verifique as permissões NTFS no diretório de uploads

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image034.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image034" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image034_thumb.jpg" alt="clip_image034" width="244" height="175" border="0" /></a>

Verifique que o usuário HANDSON\IUSR_DC1 possui permissões especiais mas não as permissões para modificar neste mesmo diretório.

É melhor utilizar um usuário especifico para cada aplicação que for ser hospedada neste servidor.

Crie um usuário (domain user) conforme este exemplo e dê a ele permissões neste web site via IIS e também ao diretório onde estarão os arquivos desta aplicação (principalmente para o diretório upload “change”.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image035.png"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image035" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image035_thumb.png" alt="clip_image035" width="244" height="184" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image037.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image037" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image037_thumb.jpg" alt="clip_image037" width="244" height="184" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image039.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image039" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image039_thumb.jpg" alt="clip_image039" width="244" height="171" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image041.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image041" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image041_thumb.jpg" alt="clip_image041" width="244" height="171" border="0" /></a>

<strong>
</strong>

&nbsp;

<strong>Teste 2 – Carregue o site novamente e faça o upload de 2 arquivos para este servidor apos fazer as alterações necessárias.</strong>

Você perceberá que o resultado será diferente do teste anterior.

Resultado - “SUCCESS” , SUCESSO

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image043.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image043" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image043_thumb.jpg" alt="clip_image043" width="244" height="175" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image045.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image045" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image045_thumb.jpg" alt="clip_image045" width="244" height="175" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image047.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image047" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image047_thumb.jpg" alt="clip_image047" width="244" height="175" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image049.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image049" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image049_thumb.jpg" alt="clip_image049" width="244" height="176" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image051.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image051" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image051_thumb.jpg" alt="clip_image051" width="244" height="176" border="0" /></a>

Veja que os 2 arquivos foram criados no diretório “uploads” desta aplicação web.

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image053.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image053" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image053_thumb.jpg" alt="clip_image053" width="244" height="167" border="0" /></a>

Verifique também via <strong>process monitor</strong> que o arquivo foi criado com sucesso para o usuário que roda a aplicação (foco deste artigo).

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image055.jpg"><img style="background-image:none;margin:0;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image055" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image055_thumb.jpg" alt="clip_image055" width="244" height="175" border="0" /></a>

<a href="http://thiagobeier.files.wordpress.com/2012/09/clip_image057.jpg"><img style="background-image:none;padding-left:0;padding-right:0;display:inline;padding-top:0;border:0;" title="clip_image057" src="http://thiagobeier.files.wordpress.com/2012/09/clip_image057_thumb.jpg" alt="clip_image057" width="244" height="171" border="0" /></a>

<strong>Resolvendo problemas</strong>

1. Utilize das ferramentas sysinternals <a href="http://technet.microsoft.com/en-us/sysinternals/bb842062">http://technet.microsoft.com/en-us/sysinternals/bb842062</a>

2. filemon.exe foi retirado e substituído pelo process monitor procmon.exe

3. utilize como campo pesquisa o nome do processo, visto em taskmgr.exe “w3wp.exe” quando for fazer resolução de problemas para IIS

<strong>Melhores praticas</strong>

1. Para cada aplicação criada ou executada neste servidor (web) crie um usuário (local no servidor ou de domínio)

2. Configure este usuário como o usuário que irá executar/rodar a aplicação “authentication methods” na aba de segurança do IIS “ IIS Directory Security”

3. Permita que este usuário tenha acesso NFTS no diretório da aplicação quando necessário (para gravar arquivos/enviar arquivos)

a. Quando utilizar o mesmo diretório para aplicação web e também para serviço FTP publicado lembre-se de utilizar um grupo dedicado para simplificar a administração.

<strong>Links</strong>

Sysinternals <a href="http://technet.microsoft.com/en-us/sysinternals/bb842062">http://technet.microsoft.com/en-us/sysinternals/bb842062</a>

Projeto ASP file upload
<a href="http://www.motobit.com/dlldownload/ScptUtl/ScptUtl-eval-2-3-1-x64.exe">http://www.motobit.com/dlldownload/ScptUtl/ScptUtl-eval-2-3-1-x64.exe</a>

Servidor IIS – <a href="http://www.iis.net">www.iis.net</a>
