---
title: Get-SPWOPIZone
TOCTitle: Get-SPWOPIZone
ms:assetid: 5a37e106-272c-43e9-ae09-20888b296af0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219439(v=office.15)
ms:contentKeyID: 49647106
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIZone

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Retorna a zona configurada no farm atual do SharePoint do aplicativo WOPI a ser usado.

## Sintaxe

    Get-SPWOPIZone [-AssignmentCollection <SPAssignmentCollection>]

## Descrição detalhada

O cmdlet **Get-SPWOPIZone** retorna a zona configurada no farm do SharePoint atual para o aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps) a ser usado.

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

</div>
<p></p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO-----------------

    Get-SPWOPIZone

Este exemplo retorna a zona configurada do aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps) a ser usado. Os valores de retorno podem ser “internal-http”, “internal-https”, “external-http” ou “external-https”.

## Consulte também


[Set-SPWOPIZone](set-spwopizone.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

