---
title: Get-SPWOPIBinding
TOCTitle: Get-SPWOPIBinding
ms:assetid: b757301b-f6c5-43a5-a8ca-2ef33ede0ae8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219450(v=office.15)
ms:contentKeyID: 49647125
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIBinding

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Retorna uma lista de vínculos criados com o **New-SPWOPIBinding** no farm do SharePoint onde esse cmdlet é executado.

## Sintaxe

    Get-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WOPIZone <String>]

## Descrição detalhada

O **Get-SPWOPIBinding** retorna uma lista de vínculos criados usando o **New-SPWOPIBinding** no farm do SharePoint atual onde este cmdlet é executado. Os resultados incluem ações, aplicativos, tipos de arquivo e zonas configuradas para um aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps).

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
<td><p><strong>Action</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a ação para retornar os vínculos.</p></td>
</tr>
<tr class="even">
<td><p><strong>Aplicativo</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o aplicativo para retornar os vínculos.</p></td>
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
<td><p><strong>Extensão</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a extensão do nome de arquivo para retornar os vínculos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o identificador de programação (ProgID) para um aplicativo para retornar os vínculos.</p></td>
</tr>
<tr class="even">
<td><p><strong>Servidor</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome do aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps) para retornar os vínculos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a zona para retornar os vínculos.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO 1-----------------

    Get-SPWOPIBinding -Server "Server.corp.Contoso.com"

Este exemplo retorna uma lista de vínculos criados no farm do SharePoint atual onde este cmdlet é executado para o aplicativo WOPI "Server.corp.Contoso.com”. O aplicativo WOPI pode ser o servidor que executa o Servidor do Office Web Apps.

\--------------EXEMPLO 2-----------------

    Get-SPWOPIZone | Get-SPWOPIBinding

Este exemplo retorna uma lista de vínculos criados no farm do SharePoint atual onde este cmdlet é executado para a zona configurada para o aplicativo WOPI.

## Consulte também


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

