---
title: Get-OfficeWebAppsFarm
TOCTitle: Get-OfficeWebAppsFarm
ms:assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219434(v=office.15)
ms:contentKeyID: 49647096
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsFarm

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2013-12-18_

Retorna detalhes sobre o objeto OfficeWebAppsFarm do qual o servidor atual é membro.

## Sintaxe

    Get-OfficeWebAppsFarm

## Descrição detalhada

O cmdlet **Get-OfficeWebAppsFarm** retorna detalhes sobre o objeto OfficeWebAppsFarm que o servidor atual é membro. Este objeto representa um grupo de servidores que funcionam como uma unidade para oferecer edição baseada na Web e exibição de documentos do Office. Nenhum parâmetro é usado com o cmdlet **Get-OfficeWebAppsFarm**.

## Parâmetros

## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------EXEMPLO 1---------------------

    Get-OfficeWebAppsFarm

Este exemplo retorna detalhes sobre o objeto OfficeWebAppsFarm.

\------------------EXEMPLO 2---------------------

    (Get-OfficeWebAppsFarm).Machines

Este exemplo retorna detalhes sobre os servidores que são membros do farm do Servidor do Office Web Apps. Estes detalhes incluem o status de integridade e funções de cada servidor.

## Consulte também


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

