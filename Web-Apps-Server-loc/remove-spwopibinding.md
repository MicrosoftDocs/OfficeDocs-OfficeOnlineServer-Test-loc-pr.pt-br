---
title: Remove-SPWOPIBinding
TOCTitle: Remove-SPWOPIBinding
ms:assetid: 52855c21-ee2c-497a-b308-bf5eeabe4bbe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219438(v=office.15)
ms:contentKeyID: 49647104
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPIBinding

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Remove as associações com aplicativos, extensões de nome de arquivo e suas ações associadas no farm atual do SharePoint onde esse cmdlet é executado.

## Sintaxe

    Remove-SPWOPIBinding [[-Identity] <SPWopiBindingPipeBind>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WhatIf [<SwitchParameter>]] [-WOPIZone <String>]

    Remove-SPWOPIBinding [-All <SwitchParameter>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Remove-SPWOPIBinding** remove associações com aplicativos, extensões de nome de arquivo e suas ações associadas no farm do SharePoint atual no qual esse cmdlet é executado. Após a execução desse cmdlet, é possível usar o **New-SPWOPIBinding** para recriar os vínculos conforme o necessário. Se você remover todos os vínculos de um aplicativo, os usuários não poderão usar o Office Web Apps ou o recurso SharePoint Share por link para esse aplicativo. Se você remover todos os vínculos no farm do SharePoint no qual esse cmdlet é executado, os usuários não poderão usar o Office Web Apps ou o recurso SharePoint Share por link para qualquer aplicativo na biblioteca do SharePoint.

Se você quiser parar de usar o Office Web Apps para cliques padrão, mas precisar preservar as informações de descoberta dos vínculos e a habilidade de os usuários utilizarem o recurso SharePoint Share por link para enviar um link para um documento e permitir que o destinatário use o Office Web Apps para esse tipo de documento, use o cmdlet **New-SPWOPISuppression**.

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
<td><p><strong>Identity</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Especifica o vínculo.</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a ação da qual os vínculos serão removidos. Por exemplo, “view,&quot; “edit&quot; e “embedview.&quot; Para obter uma lista de ações execute <strong>Get-SPWOPIBinding</strong>. Normalmente, você não usará esse parâmetro. Se você especificar algumas ações, mas não outras, talvez alguns recursos no SharePoint não funcionem.</p></td>
</tr>
<tr class="odd">
<td><p><strong>All</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Remove todos os vínculos.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o aplicativo do qual os vínculos serão removidos. Os possíveis aplicativos são os seguintes: “Word&quot;, “Excel&quot;, “PowerPoint&quot; ou “OneNote&quot;. Execute <strong>Get-SPWOPIBinding</strong> para obter a lista de aplicativos.</p></td>
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
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica as extensões de nome de arquivo das quais os vínculos serão removidos. Execute <strong>Get-SPWOPIBinding</strong> para a lista de extensões de nome de arquivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o ProgID (identificador programático) de um aplicativo do qual os vínculos serão removidos. Execute <strong>Get-SPWOPIBinding</strong> para obter a lista de ProgIDs. Convém usar apenas esse parâmetro para remover as associações com o OneNote.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome do aplicativo WOPI (como Servidor do Office Web Apps) do qual os vínculos serão removidos.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Exibe uma mensagem que descreve o efeito do comando em vez de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a zona da qual os vínculos serão removidos.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO 1-----------------

    Remove-SPWOPIBinding -Application "Excel"

Esse exemplo remove todos os vínculos com o Excel no farm do SharePoint atual no qual esse cmdlet é executado.

\--------------EXEMPLO 2-----------------

    Remove-SPWOPIBinding -All:$true

Esse exemplo remove todos os vínculos no farm do SharePoint atual no qual esse cmdlet é executado.

\--------------EXEMPLO 3-----------------

    Get-SPWOPIBinding -Action "MobileView" | Remove-SPWOPIBinding

Esse exemplo remove todos os vínculos com o Office Mobile Web Apps no farm do SharePoint atual no qual esse cmdlet é executado.

## Consulte também


[New-SPWOPIBinding](new-spwopibinding.md)  
[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

