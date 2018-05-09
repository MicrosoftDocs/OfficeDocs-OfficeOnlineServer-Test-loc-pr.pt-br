---
title: Set-SPWOPIBinding
TOCTitle: Set-SPWOPIBinding
ms:assetid: e373528f-e69b-4e25-9df4-3a5f80ab64ac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219454(v=office.15)
ms:contentKeyID: 49647133
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIBinding

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2015-03-09_

Atualiza a ação de clique padrão para um aplicativo ou associação de extensão de nome de arquivo.

## Sintaxe

    Set-SPWOPIBinding [-Identity] <SPWopiBindingPipeBind> -DefaultAction <SwitchParameter> [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Set-SPWOPIBinding** atualiza a ação de clique padrão para um aplicativo ou associação de extensão do nome de arquivo. Por exemplo, é possível definir a ação de clique padrão para exibir um documento do Word em uma biblioteca do SharePoint. Para isso, você define a ação padrão como verdadeiro para as associações “exibição”-“Word”.

Normalmente, você usaria a saída do comando **Get-SPWOPIBinding** como o valor para a propriedade -Identity deste comando. Para obter mais informações, consulte [Get-SPWOPIBinding](get-spwopibinding.md)

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Você só pode definir associações que foram criadas usando o comando <strong>New-SPWOPIBinding</strong>. Para substituir uma associação interna, por exemplo, a medida tomada durante a exibição de um documento do Word em uma biblioteca do SharePoint, crie uma nova associação usando <strong>New-SPWOPIBinding</strong> e atribua uma ação diferente. Para obter mais informações, consulte <a href="new-spwopibinding.md">New-SPWOPIBinding</a>.</td>
</tr>
</tbody>
</table>


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
<td><p>Obrigatório</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Especifica a associação. Normalmente, você usaria a saída do comando <strong>Get-SPWOPIBinding</strong> como o valor de –Identity.</p></td>
</tr>
<tr class="even">
<td><p><strong>DefaultAction</strong></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Especifica se o vínculo deve ser definido como a ação de clique padrão para um aplicativo ou extensão do nome de arquivo no vínculo.</p></td>
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

</div>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
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

    Get-SPWOPIBinding -Action "view" -Application "Word"| Set-SPWOPIBinding -DefaultAction

Este exemplo define a ação de clique padrão para exibir um documento do Word em uma biblioteca do SharePoint. É possível verificar a ação de clique padrão definida para visualizar o Word executando o cmdlet **Get-SPWOPIBinding –Action “view” –Application “Word”**. O valor **IsDefaultAction** é definido para “True.”

## Consulte também


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  
[New-SPWOPIBinding](new-spwopibinding.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Office Web Apps com o SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

