---
title: Get-OfficeWebAppsHost
TOCTitle: Get-OfficeWebAppsHost
ms:assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219446(v=office.15)
ms:contentKeyID: 49647119
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsHost

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2013-12-18_

Retorna a lista de domínios de host que estão na Lista de Permissões para um farm do Servidor do Office Web Apps.

## Sintaxe

    Get-OfficeWebAppsHost

## Descrição detalhada

O cmdlet **Get-OfficeWebAppsHost** retorna a lista de domínios de host para os quais o Servidor do Office Web Apps permite solicitações de operações de arquivo, como recuperação de arquivos, recuperação de metadados e alterações de arquivos. Essa lista, conhecida como a Lista de Permissões, é um recurso de segurança que impede hosts indesejados de se conectarem a um farm do Servidor do Office Web Apps e usá-lo para operações de arquivo sem seu conhecimento.

O caractere curinga \* é assumido para qualquer domínio que apareça na Lista de Permissões, assim, as solicitações para todos os subdomínios também são permitidas. Por exemplo, se o domínio contoso.com está na lista de permissões, o Servidor do Office Web Apps também permite solicitações para os domínios corp.contoso.com e dev.contoso.com. Solicitações para outros domínios (como fabrikam.com) não são permitidas.


> [!WARNING]
> Se não houver domínios na lista de permissões, o Servidor do Office Web Apps permitirá solicitações de arquivos para hosts em qualquer domínio. Não deixe esta lista em branco se seu farm do Servidor do Office Web Apps for acessível pela Internet. Caso contrário, qualquer pessoa poderá usar seu farm do Servidor do Office Web Apps para visualizar e editar conteúdo.



## Parâmetros

## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------ EXEMPLO 1 ---------------------

    Get-OfficeWebAppsHost

Este exemplo retorna os domínios de host que estão na Lista de Permissões.

## Consulte também


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

