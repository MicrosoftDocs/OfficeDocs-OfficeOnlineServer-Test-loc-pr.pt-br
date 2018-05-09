---
title: Repair-OfficeWebAppsFarm
TOCTitle: Repair-OfficeWebAppsFarm
ms:assetid: 083d8e25-ce82-4884-9bbc-06375185011c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219433(v=office.15)
ms:contentKeyID: 49647095
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Repair-OfficeWebAppsFarm

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Remove todos os servidores sinalizados como não íntegros de um farm do Servidor do Office Web Apps.

## Sintaxe

    Repair-OfficeWebAppsFarm [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **Repair-OfficeWebAppsFarm** remove todos os servidores sinalizados como não íntegros de um farm do Servidor do Office Web Apps. Este cmdlet atualiza a topologia do farm mas não limpa serviços e aplicativos web no servidores de onde foram removidos. Por isso, é recomendável fazer todo esforço possível para executar o cmdlet **Remove-OfficeWebAppsMachine** nos servidores não íntegros para que sejam removidos corretamente do farm. Use o cmdlet **Repair-OfficeWebAppsFarm** somente se os servidores não íntegros falharem e você não conseguir executar o cmdlet **Remove-OfficeWebAppsMachine** diretamente neles.

Se houver vários servidores não íntegros, você será questionado antes de cada servidor ser removido. Se não existirem servidores não íntegros, este cmdlet não faz nada.

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
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Assume que a resposta para qualquer prompt do usuário é Sim.</p></td>
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

    (Get-OfficeWebAppsFarm).Machines

Este exemplo mostra o status de integridade de todos os servidores no farm do Servidor do Office Web Apps.

\------------------EXEMPLO 2---------------------

    Repair-OfficeWebAppsFarm

Este exemplo remove todos os servidores não íntegros do farm do Servidor do Office Web Apps.

## Consulte também


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

