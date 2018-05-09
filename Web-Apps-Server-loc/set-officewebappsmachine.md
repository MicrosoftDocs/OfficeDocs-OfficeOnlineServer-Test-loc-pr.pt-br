---
title: Set-OfficeWebAppsMachine
TOCTitle: Set-OfficeWebAppsMachine
ms:assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219448(v=office.15)
ms:contentKeyID: 49647123
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsMachine

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Altera as configurações do servidor atual que está em um farm do Servidor do Office Web Apps.

## Sintaxe

    Set-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-Master <String>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Set-OfficeWebAppsMachine** altera as configurações do servidor atual que está em um farm do Servidor do Office Web Apps. As configurações incluem as funções detidas pelo servidor atual e o servidor mestre designado para o farm.

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
<td><p><strong>Confirmar</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Master</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p></p>
<p>Especifica o servidor que armazena os arquivos de configuração do farm mestre.</p>
<p>Se configurar o servidor local como o mestre, você deverá executar <strong>Set-OfficeWebAppsMachine -Master</strong> em todos os demais servidores no farm do Servidor do Office Web Apps para apontá-los para o novo mestre.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Funções</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String[]</p></td>
<td><p>Especifica a lista de funções de servidor para atribuir ao servidor local, separadas por vírgulas.</p>
<p>Os tipos de função são os seguintes:</p>
<p><strong>Tudo</strong></p>
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

\------------------ EXEMPLO 1 ---------------------

    (Get-OfficeWebAppsFarm).Machines

Este exemplo mostra as funções detidas por cada servidor no farm do Servidor do Office Web Apps.

\------------------ EXEMPLO 2 ---------------------

    Set-OfficeWebAppsMachine -Roles FrontEnd

Este exemplo configura o servidor atual como um servidor front-end.

\------------------ EXEMPLO 3 ---------------------

    Set-OfficeWebAppsMachine -Roles All

Este exemplo configura o servidor atual para hospedar todas as funções.

## Consulte também


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

