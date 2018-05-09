---
title: Windows PowerShell para Office Web Apps Server
TOCTitle: Windows PowerShell para Office Web Apps Server
ms:assetid: 56bfd3b3-f563-423d-aea0-65b331f73b96
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ee890080(v=office.15)
ms:contentKeyID: 49647105
ms.date: 01/04/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Windows PowerShell para Office Web Apps Server

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2016-12-16_

**Resumo:** Encontre artigos sobre os cmdlets do Windows PowerShell OfficeWebApps que configuram o Office Web Apps Server.

**Público:** profissionais de TI

O Servidor do Office Web Apps é um novo produto de servidor do Office que fornece versões baseadas no navegador do Word, do PowerPoint, do Excel e do OneNote. Um único farm do Office Web Apps Server é capaz de atender a usuários que acessam arquivos do Office por meio do SharePoint 2013, do Lync Server 2013, do Exchange Server 2013, de pastas compartilhadas e de sites da web.

![Logotipo do Office 2013](images/JJ219456.a106e261-2cd0-43b7-af77-92de7e4b6fb9(Office.15).png "Logotipo do Office 2013")A tabela a seguir lista e descreve os artigos para cada cmdlet do Windows PowerShell do OfficeWebApps para o Servidor do Office Web Apps.


> [!TIP]
> Se o Windows PowerShell não reconhecer esses cmdlets ao executá-los, será necessário importar o módulo <STRONG>OfficeWebApps</STRONG>. Utilize este comando:<BR><CODE>Import-Module -Name OfficeWebApps</CODE>




### Cmdlets do Windows PowerShell OfficeWebApps

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Artigo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="get-officewebappsfarm.md">Get-OfficeWebAppsFarm</a></p></td>
<td><p>Retorna detalhes sobre o objeto OfficeWebAppsFarm do qual o servidor atual é membro.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-officewebappshost.md">Get-OfficeWebAppsHost</a></p></td>
<td><p>Retorna a lista de domínios do host que estão na Lista de Permissão para um farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-officewebappsmachine.md">Get-OfficeWebAppsMachine</a></p></td>
<td><p>Retorna detalhes sobre o servidor atual em um farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><a href="new-officewebappsfarm.md">New-OfficeWebAppsFarm</a></p></td>
<td><p>Cria um novo farm do Servidor do Office Web Apps no computador local.</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-officewebappshost.md">New-OfficeWebAppsHost</a></p></td>
<td><p>Adiciona um domínio de host para a Lista de Permissões para um farm existente do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><a href="new-officewebappsmachine.md">New-OfficeWebAppsMachine</a></p></td>
<td><p>Adiciona o servidor atual para um farm existente do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><a href="remove-officewebappshost.md">Remove-OfficeWebAppsHost</a></p></td>
<td><p>Remove um domínio de host da Lista de Permissões para um farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><a href="remove-officewebappsmachine.md">Remove-OfficeWebAppsMachine</a></p></td>
<td><p>Remove o servidor atual do farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><a href="repair-officewebappsfarm.md">Repair-OfficeWebAppsFarm</a></p></td>
<td><p>Remove todos os servidores sinalizados como não íntegros de um farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><a href="set-officewebappsfarm.md">Set-OfficeWebAppsFarm</a></p></td>
<td><p>Define as configurações de um farm existente do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-officewebappsmachine.md">Set-OfficeWebAppsMachine</a></p></td>
<td><p>Altera as configurações do servidor atual que está em um farm do Servidor do Office Web Apps.</p></td>
</tr>
</tbody>
</table>


### Outros recursos do Office para profissionais de TI

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/JJ219457.22cad0f4-303d-4a40-90a3-fa08e69dfdaf(Office.15).png" title="Ícone de novidades (caixa)" alt="Ícone de novidades (caixa)" /></p></td>
<td><p><strong>Conteúdo publicado recentemente</strong></p></td>
<td><p>Consulte o seguinte artigo para obter uma lista de artigos do Servidor do Office Web Apps novos ou atualizados recentemente.</p>
<ul>
<li><p><a href="https://technet.microsoft.com/pt-br/library/ff433481(v=office.15)">Conteúdo publicado recentemente para Office Web Apps e Office Web Apps Server</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><img src="images/Dn135237.6b2d6dfa-7dc8-40fb-8335-af68b575f8cb(Office.15).png" title="Introdução" alt="Introdução" /></p></td>
<td><p><strong>Introdução</strong></p></td>
<td><p>Baixe o Servidor do Office Web Apps.</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256561">Centro de Serviços de Licenciamento por Volume (VLSC)</a></p>
<p>Para baixar o Servidor do Office Web Apps, você deve ter um contrato de Licenciamento por Volume para Office Professional Plus 2013, Office Standard 2013 ou Office para Mac 2011. O download está localizado abaixo desses produtos do Office no portal do VLSC.</p></li>
</ul>
<p>Efetue download dos pacotes de idioma para Servidor do Office Web Apps.</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=263945">Centro de Download da Microsoft</a></p></li>
</ul>
<p>Saiba mais sobre o Office Web Apps Server.</p>
<ul>
<li><p><a href="deploy-the-infrastructure-office-web-apps-server.md">Implantar a infraestrutura: Servidor do Office Web Apps</a></p></li>
</ul>
<p>Explore esses links para saber como os produtos do Office Server podem usar o Servidor do Office Web Apps para fornecer exibição e edição com base na web, de arquivos do Office.</p>
<ul>
<li><p><a href="use-office-web-apps-with-sharepoint-2013.md">Usar o Office Web Apps com o SharePoint 2013</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256902">Implantando os Servidor do Office Web Apps e o Lync Server 2013</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256611">Integração do Servidor do Office Web Apps (Exchange Server 2013)</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ219456.6fa793ee-ede9-4476-901c-de96ea37fc3a(Office.15).png" title="Ícone de chat" alt="Ícone de chat" /></p></td>
<td><p><strong>Faça comentários</strong></p></td>
<td><p>Para fazer comentários sobre a documentação do Office 2013Office 365 ProPlus, clique no link <strong>Comentários</strong> na parte inferior da página. Assim, seu comentário é enviado diretamente para a equipe de documentação.</p>
<p><img src="images/JJ219456.1863f854-8ce5-40e4-bd40-9bbe16591834(Office.15).png" title="email" alt="email" />  Para sugerir conteúdo ou solicitar mais documentação (ou informar sobre um erro), entre em contato conosco pelo email <a href="mailto:feedork@microsoft.com">feedork@microsoft.com</a>.</p></td>
</tr>
</tbody>
</table>


## Encontre treinamento e outros recursos sobre o Office


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Download</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/evalcenter/hh973391">Office 365 ProPlus</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=507653">Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/evalcenter/ee390818.aspx">Office 2013</a></p></li>
<li><p><a href="https://code.msdn.microsoft.com/office/">Exemplos de códigos do Office</a></p></li>
<li><p><a href="https://gallery.technet.microsoft.com/office/">Scripts e arquivos de exemplo do Office</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/office/aa905351">Downloads para desenvolvedores do Office</a></p></li>
<li><p><a href="http://www.microsoft.com/pt-br/download/office.aspx?q=office">Downloads do Office</a></p></li>
<li><p><a href="https://www.microsoft.com/pt-br/download/search.aspx?q=office+365">Downloads do Office 365</a></p></li>
</ul></td>
<td><p><strong>Como fazer</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/pt-br/library/jj220060.aspx">Criar aplicativos para Office</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/library/cc178982.aspx">Implantar o Office 2013</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/library/cc179068.aspx">Gerenciar o Office 2013</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/office/ff381682.aspx">Treinamento para usuários finais do Office 2010</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/office/aa905496.aspx">SDKs do Office</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/office/aa905375">Treinamento para desenvolvedores do Office</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=odc%26from=mscomodc">Vídeos para desenvolvedores do Office</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=o365%26from=mscomo365">Vídeos para desenvolvedores do Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/office/ff519671">Treinamento para profissionais de TI do Office</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/en-us/office/media/video/video.html?cid=otc%26from=mscomotc">Vídeos para profissionais de TI do Office</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/en-us/office/media/video/video.html?cid=o365%26from=mscomo365">Vídeos para profissionais de TI do Office 365</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/openspecifications/">Especificações abertas</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/library/cc307282(v=office.12).aspx">Protocolos do Office</a></p></li>
</ul></td>
<td><p><strong>Sites</strong></p>
<ul>
<li><p><a href="https://msdn.microsoft.com/pt-br/office">Desenvolvedores do Office</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/office">Profissionais de TI do Office</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/office/hh506337">Desenvolvedores do Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/hh912691">Profissionais de TI do Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/library/cc303401.aspx">Kit de Recursos do Office 2013</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/sharepoint">Desenvolvedores do SharePoint</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/sharepoint">Profissionais de TI do SharePoint</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/vstudio/aa718325">Desenvolvedores do Visual Studio</a></p></li>
<li><p><a href="http://office.microsoft.com/">Office.com</a></p></li>
</ul></td>
<td><p><strong>Help</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/pt-br/office/ee748587.aspx">Atualizações do Office</a></p></li>
<li><p><a href="https://blogs.msdn.com/b/officeapps">Blog sobre Aplicativos do Office e do SharePoint</a></p></li>
<li><p><a href="https://social.msdn.microsoft.com/forums/pt-br/category/officedev%2coldevelopment%2csharepoint2010%2csharepoint%2cprojectserver2010%2cprojectprofessional2010%2cuc/">Fóruns: Office para Desenvolvedores</a></p></li>
<li><p><a href="https://answers.microsoft.com/pt-br/msoffice">Fóruns: Office 365</a></p></li>
<li><p><a href="https://social.technet.microsoft.com/wiki/pt-br">Wiki do TechNet</a></p></li>
<li><p><a href="https://stackoverflow.com/search?q=office">StackOverflow: Office</a></p></li>
<li><p><a href="https://mvp.microsoft.com/pt-br/mvp/search-mvp.aspx?kw=office">MVPs do Office</a></p></li>
<li><p><a href="https://technet.microsoft.com/pt-br/ms772425">Suporte para profissionais de TI do Office</a></p></li>
<li><p><a href="https://msdn.microsoft.com/pt-br/office/aa905515">Suporte para desenvolvedores do Office</a></p></li>
</ul></td>
</tr>
</tbody>
</table>


[](use-office-web-apps-with-sharepoint-2013.md)

