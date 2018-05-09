---
title: Remove-OfficeWebAppsMachine
TOCTitle: Remove-OfficeWebAppsMachine
ms:assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219440(v=office.15)
ms:contentKeyID: 49647107
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsMachine

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Remove o servidor atual do farm do Servidor do Office Web Apps.

## Sintaxe

    Remove-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Remove-OfficeWebAppsMachine** remove o servidor atual do farm do Servidor do Office Web Apps. Como parte deste processo, o cmdlet remove os aplicativos Web e desliga os serviços relacionados ao Servidor do Office Web Apps. Caso não seja possível executar o cmdlet **Remove-OfficeWebAppsMachine** a partir do servidor que se deseja remover, use o cmdlet **Repair-OfficeWebAppsFarm** de qualquer outro servidor no farm do Office Web Apps.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Se o servidor local for designado como o servidor mestre no farm do Servidor do Office Web Apps, não é possível removê-lo do farm até que outro servidor seja atribuído como mestre usando o cmdlet <strong>Set-OfficeWebAppsMachine</strong> ou até que todos os outros servidores sejam removidos do farm.</td>
</tr>
</tbody>
</table>


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

    Remove-OfficeWebAppsMachine

Este exemplo remove o servidor atual do farm do Servidor do Office Web Apps.

## Consulte também


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

