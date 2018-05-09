---
title: Update-SPWOPIProofKey
TOCTitle: Update-SPWOPIProofKey
ms:assetid: fe7f3a87-082e-4a43-a5f3-7be41d8e91a3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219460(v=office.15)
ms:contentKeyID: 49647140
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Update-SPWOPIProofKey

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Atualiza a chave pública usada para se conectar ao aplicativo WOPI no farm atual do SharePoint onde esse cmdlet é executado.

## Sintaxe

    Update-SPWOPIProofKey [-AssignmentCollection <SPAssignmentCollection>] [-ServerName <String>]

## Descrição detalhada

O cmdlet **Update-SPWOPIProofKey** atualiza a chave pública usada para conectar ao aplicativo WOPI (que pode ser um servidor executando o Servidor do Office Web Apps) no farm do SharePoint atual onde este cmdlet é executado. Você pode desejar usar este cmdlet se as chaves se tornarem dessincronizadas entre o farm do SharePoint e o aplicativo WOPI. Se as chaves estão dessincronizadas, os documentos podem não abrir no navegador e as mensagens como “Invalid Proof Signature for file…” ou “Invalid Proof Signature for folder...” são encontradas nos logs do ULS (Unified Logging System).

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

</div></td>
</tr>
<tr class="even">
<td><p><strong>ServerName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o aplicativo WOPI de onde obter a chave. Este pode ser um servidor executando o Servidor do Office Web Apps. Se este parâmetro estiver ausente, as chaves públicas para todos os aplicativos WOPI que estão conectados ao farm do SharePoint atual serão usadas.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO-----------------

    Update-SPWOPIProofKey -ServerName "Server.corp.Contoso.com"

Este exemplo obtém a chave pública atual do aplicativo WOPI (como um servidor executando o Servidor do Office Web Apps) e atualiza a chave armazenada no farm do SharePoint.

## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

