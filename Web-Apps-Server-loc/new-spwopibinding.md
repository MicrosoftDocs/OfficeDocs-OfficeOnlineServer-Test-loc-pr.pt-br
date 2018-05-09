---
title: New-SPWOPIBinding
TOCTitle: New-SPWOPIBinding
ms:assetid: 696f01b4-a144-431b-9bae-1c3ede78609d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219441(v=office.15)
ms:contentKeyID: 49647108
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPIBinding

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Cria um novo vínculo para associar extensões de nome de arquivo ou aplicativos com ações no farm atual do SharePoint no qual esse cmdlet é executado.

## Sintaxe

    New-SPWOPIBinding -ServerName <String> [-Action <String>] [-AllowHTTP <SwitchParameter>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-FileName <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **New-SPWOPIBinding** associa extensões de nome de arquivo ou aplicativos a ações no farm do SharePoint no qual esse cmdlet é executado. Cada vínculo permite o uso do aplicativo WOPI para exibir ou editar arquivos em sua biblioteca do SharePoint. Por exemplo, quando um usuário vê um documento do Word em uma lista de documentos do SharePoint, a lista do SharePoint exibe as opções disponíveis para exibição ou edição do documento, com base nas ações vinculadas ao Word nesse farm do SharePoint.

Para usar um aplicativo WOPI, como um servidor que executa o Servidor do Office Web Apps, para Office Web Apps, é necessário executar este cmdlet no farm do SharePoint antes de poder usar o Office Web Apps.

O cmdlet **New-SPWOPIBinding** falhará se for executado para um aplicativo ou extensão de nome de arquivo no qual o vínculo (ou associação) já existe.

SharePoint Management Shell

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ServerName</strong></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome ou o nome de domínio totalmente qualificado (FQDN) do aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps).</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a ação a ser vinculada. Por exemplo, “view,” “edit” e “embedview”. Para obter uma lista de ações suportadas pelo aplicativo WOPI, execute <strong>Get-SPWOPIBinding</strong>. Normalmente, não parâmetro não é usado. Talvez alguns recursos do SharePoint não funcionem se algumas ações forem especificadas sem que outras tenham sido especificadas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHTTP</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Especifica se o cmdlet pode usar HTTP para descoberta do que é com suporte do aplicativo WOPI. Se isso for especificado como True, as informações de descoberta do aplicativo WOPI serão enviadas em uma conexão não segura.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica os aplicativos para vínculo. Os aplicativos possíveis são os seguintes: “Word”, “Excel”, “PowerPoint” ou “OneNote”. Execute o cmdlet <strong>Get-SPWOPIBinding</strong> para obter a lista completa de aplicativos com suporte do aplicativo WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Gerencia objetos para o devido descarte. O uso de objetos, como <strong>SPWeb</strong> ou <strong>SPSite</strong>, pode consumir grandes quantidades de memória. Além disso, o uso desses objetos em scripts do Windows PowerShell requer o devido gerenciamento da memória. Usando o objeto <strong>SPAssignment</strong>, você pode atribuir objetos a uma variável e descartá-los quando eles não forem mais necessários, a fim de liberar espaço na memória. Quando usar os objetos <strong>SPWeb</strong>, <strong>SPSite</strong> e <strong>SPSiteAdministration</strong>, eles serão automaticamente descartados caso não use um conjunto de atribuições ou o parâmetro <strong>Global</strong>.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Quando usa o parâmetro <strong>Global</strong>, todos os objetos são incluídos no repositório global. Quando os objetos não são usados imediatamente ou são descartados com o uso do comando <strong>Stop-SPAssignment</strong>, pode ocorrer um cenário de memória insuficiente.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Extensão</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica as extensões de nome do arquivo para vínculo. Execute o cmdlet <strong>Get-SPWOPIBinding</strong> para obter a lista de extensões de nome de arquivo com suporte do aplicativo WOPI.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o caminho do arquivo xml que contém as informações de descoberta do aplicativo WOPI. É possível carregar as informações de descoberta de um arquivo xml em vez de solicitar diretamente do aplicativo WOPI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o ProgID (identificador programático) de um aplicativo para vínculo. Execute o cmdlet <strong>Get-SPWOPIBinding</strong> para obter a lista de ProgIDs com suporte do aplicativo WOPI. Convém usar apenas esse parâmetro para associar uma ação a uma pasta OneNote.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Exibe uma mensagem que descreve o efeito do comando em vez de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO 1-----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com"

Esse exemplo cria associações com todos os aplicativos e extensões de nome de arquivo com suporte do aplicativo WOPI no farm do SharePoint atual no qual esse cmdlet é executado.

\--------------EXEMPLO 2-----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com" -Application "Excel"

Esse exemplo associa Excel a todas as ações com suporte do aplicativo WOPI para Excel no farm do SharePoint atual no qual esse cmdlet é executado.

## Consulte também


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

