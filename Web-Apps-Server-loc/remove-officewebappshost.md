---
title: Remove-OfficeWebAppsHost
TOCTitle: Remove-OfficeWebAppsHost
ms:assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219453(v=office.15)
ms:contentKeyID: 49647131
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsHost

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Remove um domínio de host da Lista de Permissões de um farm do Servidor do Office Web Apps.

## Sintaxe

    Remove-OfficeWebAppsHost -Domain <String>

## Descrição detalhada

O cmdlet **Remove-OfficeWebAppsHost** remove o domínio de host especificado para a Lista de Permissões. A Lista de Permissões contém os domínios de host para os quais o Servidor do Office Web Apps permite solicitações de operações de arquivo.


> [!WARNING]
> Se não houver domínios na Lista de Permissões, o Servidor do Office Web Apps permite as solicitações de arquivos para hosts em qualquer domínio. Não deixe esta lista em branco se o seu farm do Servidor do Office Web Apps é acessível pela Internet. Caso contrário, qualquer pessoa pode usar seu farm do Servidor do Office Web Apps para exibir e editar conteúdo.



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
<td><p><strong>Domain</strong></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o domínio de host para remover da Lista de Permissões.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------EXEMPLO 1---------------------

    Remove-OfficeWebAppsHost -domain "contoso.com"

Este exemplo retorna o domínio contoso.com da Lista de Permissões.

## Consulte também


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Get-OfficeWebAppsHost](get-officewebappshost.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

