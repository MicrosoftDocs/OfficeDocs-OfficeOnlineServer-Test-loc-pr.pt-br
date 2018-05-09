---
title: New-OfficeWebAppsMachine
TOCTitle: New-OfficeWebAppsMachine
ms:assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219449(v=office.15)
ms:contentKeyID: 49647124
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsMachine

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Adiciona o servidor atual a um farm do Servidor do Office Web Apps existente.

## Sintaxe

    New-OfficeWebAppsMachine [-MachineToJoin] <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **New-OfficeWebAppsMachine** adiciona o servidor atual a um farm do Servidor do Office Web Apps existente e, como alternativa, define uma ou mais funções no novo servidor.

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
<td><p><strong>MachineToJoin</strong></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome de qualquer servidor que já seja membro do farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirmar</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Considera que a resposta de qualquer solicitação de usuário é Sim.</p></td>
</tr>
<tr class="even">
<td><p><strong>Funções</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String[]</p></td>
<td><p>Especifica um ou mais funções do servidor, separadas por vírgulas, para atribuir ao novo servidor. Se nenhuma função for especificada, o servidor será atribuído com todas as funções.</p>
<p>Os tipos de função são os seguintes:</p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Como prática recomendada, sugerimos que todos os servidores em um farm do Servidor do Office Web Apps executem todas as funções. Atribuir funções não é útil até o farm do Servidor do Office Web Apps conter aproximadamente 50 servidores.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
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

\------------------EXEMPLO 1---------------------

    New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com

Este exemplo adiciona o servidor atual ao farm do Servidor do Office Web Apps executando no servidor chamado server1.contoso.com.

## Consulte também


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

