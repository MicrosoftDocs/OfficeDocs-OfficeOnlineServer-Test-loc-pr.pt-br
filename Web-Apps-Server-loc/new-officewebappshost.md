---
title: New-OfficeWebAppsHost
TOCTitle: New-OfficeWebAppsHost
ms:assetid: f1d523ab-45c6-4e3c-b274-22c0d229a6a0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219459(v=office.15)
ms:contentKeyID: 49647139
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsHost

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-09_

Adiciona um domínio de host à Lista de Permissões de um farm do Servidor do Office Web Apps.

## Sintaxe

    New-OfficeWebAppsHost -Domain <String>

## Descrição detalhada

O novo cmdlet **Get-OfficeWebAppsHost** retorna a lista dos domínios de host para os quais o Servidor do Office Web Apps permite as solicitações de operações de arquivos, como a recuperação de arquivo, recuperação de metadados e as alterações de arquivo. Esta lista, conhecida como a Lista de Permissão, é um recurso de segurança que evita que os hosts não desejados se conectem a um farm do Servidor do Office Web Apps e usem-no para operações de arquivos sem seu conhecimento.


> [!TIP]
> Você pode usar qualquer tipo de domínio, incluindo: nomes de domínio Public, Pool, Farm e Active Directory. No entanto, verifique se o domínio para o qual você está concedendo acesso cumpre com seus requisitos de segurança.



O curinga \* é assumido para qualquer domínio que apareça na Lista de Permissão para que as solicitações para todos os subdomínios também sejam permitidos. Por exemplo, se o domínio contoso.com estiver na Lista de Permissão, o Servidor do Office Web Apps também permite solicitações para os domínios corp.contoso.com e dev.contoso.com. Solicitações para outros domínios (como fabrikam.com) não são permitidas.


> [!WARNING]
> Se não houver domínios na Lista de Permissão, o Servidor do Office Web Apps permite as solicitações de arquivos para hosts em qualquer domínio. Não deixe esta lista em branco se o seu farm do Servidor do Office Web Apps pode ser acessado pela Internet. Caso contrário, qualquer pessoa pode usar seu farm do Servidor do Office Web Apps para exibir e editar conteúdo.



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
<td><p>Especifica o domínio a ser adicionado à Lista de Permissão. Não especifique um asterisco ou inicie com um ponto.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------EXEMPLO 1---------------------

    New-OfficeWebAppsHost -domain "contoso.com"

Este exemplo retorna o domínio contoso.com da Lista de Permissão.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Você não pode adicionar vários domínios de host à Lista de Permissão ao mesmo tempo. É necessário executar o cmdlet New-OfficeWebAppsHost para cada domínio de host que você deseja adicionar à Lista de Permissão.</td>
</tr>
</tbody>
</table>


## Consulte também


[Get-OfficeWebAppsHost](get-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

