---
title: Set-SPWOPIZone
TOCTitle: Set-SPWOPIZone
ms:assetid: bc751cc4-8ac8-45f7-b6ea-da6fcb5473ac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219451(v=office.15)
ms:contentKeyID: 49647126
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIZone

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Configura a zona que o farm atual do SharePoint usará para navegar até o aplicativo WOPI.

## Sintaxe

    Set-SPWOPIZone [[-Zone] <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Set-SPWOPIZone** configura a zona que o farm do SharePoint atual usará para navegar o navegador para o aplicativo WOPI (como o servidor que executa o Servidor do Office Web Apps). A página SharePoint Server no navegador cria um quadro que contém uma página no aplicativo WOPI. A zona para a URL da página do aplicativo WOPI é determinada por esta configuração.

Se você não definir a zona, o padrão é “Internal-HTTP”. Se você selecionar uma zona não suportada pelo aplicativo WOPI, o Office Web Apps não funcionária. Use apenas HTTP quando estiver em uma rede segura completa que usa IPSEC (criptografia completa) ou em um ambiente de teste que não contém dados sensíveis.

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
<td><p><strong>Zone</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a zona. Para obter uma lista de zonas que o aplicativo WOPI suporta, execute <strong>Get-SPWOPIBinding</strong>.</p>
<p>Se você possui um farm do SharePoint que é interno e externo, especifique externo. Se você possui um farm do SharePoint que é apenas interno, especifique interno. Use apenas HTTP quando estiver em uma rede totalmente segura que usa IPSEC (criptografia completa) ou em um ambiente de teste que não contém dados sensíveis. As opções são as seguintes:</p>
<p>- Internal-HTTP</p>
<p>- Internal-HTTPS</p>
<p>- External-HTTP</p>
<p>- External-HTTPS</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Exibe uma mensagem que descreve o efeito do comando em vez de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\--------------EXEMPLO-----------------

    Set-SPWOPIZone -Zone "external-https"

Este exemplo configura o farm do SharePoint atual para usar conexões externas através de HTTPS para o aplicativo WOPI (como um servidor que executa o Servidor do Office Web Apps).

## Consulte também


[Get-SPWOPIZone](get-spwopizone.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

