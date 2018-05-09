---
title: Get-OfficeWebAppsMachine
TOCTitle: Get-OfficeWebAppsMachine
ms:assetid: 02fadf5e-0382-4e73-8d07-e67d088b1a02
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219432(v=office.15)
ms:contentKeyID: 49647094
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsMachine

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2013-12-18_

Retorna detalhes sobre o servidor atual em um farm do Servidor do Office Web Apps.

## Sintaxe

    Get-OfficeWebAppsMachine

## Descrição detalhada

O cmdlet **Get-OfficeWebAppsMachine** retorna detalhes sobre o servidor atual que está no farm do Servidor do Office Web Apps. Estes detalhes incluem as funções e o status de integridade do servidor atual e o nome do servidor mestre do farm.

## Parâmetros

## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------EXEMPLO 1---------------------

    Get-OfficeWebAppsMachine

Este exemplo retorna detalhes sobre o servidor atual que está em um farm do Servidor do Office Web Apps.

\------------------EXEMPLO 2---------------------

    (Get-OfficeWebAppsFarm).Machines

Este exemplo retorna detalhes sobre todos os servidores que estão em um farm do Servidor do Office Web Apps.

## Consulte também


[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

