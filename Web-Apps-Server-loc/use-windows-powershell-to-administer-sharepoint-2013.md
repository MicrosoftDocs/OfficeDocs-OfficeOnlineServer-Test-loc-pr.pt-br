---
title: Usar o Windows Powershell para administrar o SharePoint 2013
TOCTitle: Usar o Windows Powershell para administrar o SharePoint 2013
ms:assetid: ae4901b4-505a-42a9-b8d4-fca778abc12e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ee806878(v=office.15)
ms:contentKeyID: 49647122
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Usar o Windows Powershell para administrar o SharePoint 2013

 

_**Aplica-se a:**SharePoint Foundation 2013, SharePoint Server 2013 Enterprise, SharePoint Server 2013 Standard_

_**Tópico modificado em:**2016-12-16_

**Resumo:**Aprenda sobre cmdlets e conceitos básicos do Windows PowerShell e como usar o Windows PowerShell com o SharePoint 2013.

Neste artigo:

  - Visão geral

  - Acesso do Windows PowerShell para o SharePoint 2013

  - Permissões

  - Scripts e políticas de execuçã

  - Aprendizado do Windows PowerShell

## Visão geral

Windows PowerShell é um shell de linha de comando e linguagem de script que concede acesso total a um administrador às interfaces de programação de aplicativos (APIs) aplicáveis. Os administradores podem interagir diretamente com o SharePoint 2013 para manipular aplicativos Web, conjuntos de sites, sites, listas e muito mais. Além disso, um administrador pode roteirizar cmdlets (que se lê "command-lets").

Windows PowerShell 3.0 é um pré-requisito para instalar o SharePoint 2013. Será instalado quando você executar o Ferramenta de Preparação de Produtos do Microsoft SharePoint, caso ainda não esteja instalado. Por padrão, o Windows PowerShell está localizado no seguinte caminho: \<%SystemRoot%\>\\System32\\WindowsPowerShell\\v1.0\\PowerShell.exe.

Para obter uma lista dos novos recursos do Windows PowerShell 3.0, consulte [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/p/?linkid=272782)

Para obter uma ferramenta interativa e um guia que ajude você a conhecer a sintaxe do Windows PowerShell, consulte a [Ferramenta Compilador de Comandos do Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=229854) e o [Guia de introdução](http://www.microsoft.com/download/en/details.aspx?id=27588).

Convém usar o Windows PowerShell ao executar tarefas administrativas de linha de comando. A ferramenta de linha de comando Stsadm foi preterida, mas está incluída para oferecer suporte à compatibilidade com versões anteriores do produto.

## Acesso do Windows PowerShell para o SharePoint 2013

Depois de instalar o SharePoint 2013, cmdlets aplicáveis do Windows PowerShell estão disponíveis no Shell de Gerenciamento do SharePoint 2013. Você pode gerenciar a maioria dos aspectos do SharePoint 2013 no SharePoint Management Shell. Também pode criar novos conjuntos de site, aplicativos Web, contas de usuário, aplicativos de serviço, proxies e mais. Os comandos que você digita no SharePoint Management Shell retornam objetos do SharePoint baseados no Microsoft .NET Framework. E pode aplicar esses objetos como entrada a comandos subsequentes ou pode armazenar os objetos em variáveis locais para uso posterior.

Com o SharePoint Management Shell, você não tem que registrar o snap-in que contém os cmdlets. O registro do módulo do Microsoft.SharePoint.PowerShell.dll para os cmdlets do SharePoint 2013 é automático, como resultado da linha do `Add-PSSnapin Microsoft.SharePoint.PowerShell` no arquivo SharePoint.ps1 que está localizado no *%CommonProgramFiles%*\\Microsoft Shared\\Web Server Extensions\\15\\Config\\PowerShell\\Registration. Para usar o console do Windows PowerShell é preciso se registrar esse snap-in manualmente.

Se você usa o console do SharePoint Management Shell ou do Windows PowerShell, também poderá carregar snap-ins adicionais. Para mais informações, consulte [Como personalizar perfis](http://technet.microsoft.com/pt-br/magazine/2008.10.windowspowershell.aspx).

**Para acessar o SharePoint Management Shell**

1.  Inicie o SharePoint Management Shell.
    
      - Para o Windows Server 2008 R2:
        
          - Clique em **Iniciar**, clique em **Produtos do Microsoft SharePoint 2013** e, em seguida, em **SharePoint Management Shell**.
    
      - Para o Windows Server 2012:
        
          - Na tela **Iniciar**, clique em **SharePoint Management Shell**.
            
            Se o **SharePoint Management Shell** não estiver na tela **Iniciar**:
        
        <!-- end list -->
        
          - Clique com o botão direito do mouse em **Computador**, clique em **Todos os aplicativos** e, em seguida, em **SharePoint Management Shell**.
    
    Para saber mais sobre como interagir com o Windows Server 2012, consulte [Tarefas de gerenciamento comuns e navegação no Windows Server 2012](http://technet.microsoft.com/pt-br/library/hh831491.aspx).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Os consoles do Shell de Gerenciamento do SharePoint 2013 e do Windows PowerShell também diferente no uso da opção <code>ReuseThread</code>, que define como o modelo de threading é usado. O uso do Shell de Gerenciamento do SharePoint 2013 é definido por esta linha, <code>{Host.Runspace.ThreadOptions = &quot;ReuseThread&quot;}</code>, que está no arquivo SharePoint.ps1. Para mais informações, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=183145">Opções do PS Thread</a>.</td>
</tr>
</tbody>
</table>


## Permissões

## No local

Antes que você possa usar o cmdlet do **Add-SPShellAdmin** para conceder permissões a usuários para executar cmdlets do SharePoint 2013, verifique se você atende a todos os requisitos mínimos a seguir:

  - Você deve ser membro da função de servidor fixo no **securityadmin** na instância do SQL Server

  - Você deve ser membro na função de banco de dado fixo no **db\_owner** em todos os bancos de dados que devam ser atualizados.

  - Você deve ser um membro do grupo de Administradores no servidor no qual você está executando o cmdlet Windows PowerShell.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Se as permissões não forem satisfeitas, entre em contato com seu Administrador da instalação ou com o administrador do SQL Server para solicitar essas permissões.</td>
</tr>
</tbody>
</table>


Para mais informações sobre as permissões do Windows PowerShell, consulte Permissões e [Add-SPShellAdmin](https://technet.microsoft.com/pt-br/library/ff607596\(v=office.15\))

Se você não for membro da função **SharePoint\_Shell\_Access** ou do grupo local **WSS\_Admin\_WPG**, use o cmdlet **Add-SPShellAdmin** para adicionar o grupo **WSS\_Admin\_WPG** em todos os servidores Web front-end no farm do SharePoint farm e na função **SharePoint\_Shell\_Access**. Se o banco de dados do SQL Server não tem a função **SharePoint\_Shell\_Access**, ela é automaticamente criada ao executar o cmdlet **Add-SPShellAdmin**. Depois de executar o cmdlet **Add-SPShellAdmin** , os usuários podem executar os cmdlets do SharePoint Windows PowerShell em um ambiente de farm de vários servidores.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Ao instalar o SharePoint 2013, a conta de usuário da qual você executa a instalação obtém as permissões apropriadas para executar os cmdlets Windows PowerShell. Se nenhum usuário tiver sido adicionado para executar o cmdlet Windows PowerShell, você pode usar o cmdlet <strong>Add-SPShellAdmin</strong> para adicioná-los.</td>
</tr>
</tbody>
</table>


É preciso executar o cmdlet **Add-SPShellAdmin** para todos os bancos de dados aos quais você concede acesso. Se nenhum banco de dados for especificado, será usado o banco de dados de configuração do farm. Se você especificar um banco de dados, o banco de dados do conteúdo do farm será incluído no banco de dados de configuração do farm que você especificar.

Para visualizar uma lista de todos os cmdlets do **SPShellAdmin**, em um prompt de comando Windows PowerShell, digite `Get-Command -Noun SPShellAdmin`.

## SharePoint Online

Verifique se você tem as permissões administrativas a seguir:

  - Você deve receber a função de administrador global no site do SharePoint Online, no qual está executando o cmdlet Windows PowerShell. Para mais informações, consulte [Funções administrativas padrão e grupos de usuário](http://go.microsoft.com/fwlink/p/?linkid=242451).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Você pode usar um grupo específico do Windows PowerShell com o SharePoint Online. Para obter mais informações, consulte <a href="https://technet.microsoft.com/pt-br/library/fp161362(v=office.15)">PowerShell do Office 365 para SharePoint Online</a>.</td>
    </tr>
    </tbody>
    </table>


## Scripts e política de execução

Embora você possa usar o Windows PowerShell para realizar uma tarefa administrativa única, você também pode usar um script para automatizar uma série de tarefas. Um script é um arquivo de texto que contém um ou mais comandos Windows PowerShell. Os scripts Windows PowerShell têm uma extensão de arquivo chamada .ps1.

Para executar os scripts, a política de execução mínima exigida para o SharePoint 2013 é RemoteSigned, embora a política padrão para o Windows PowerShell seja Restrita. Se a política for deixada como Restrita, o Shell de Gerenciamento do SharePoint 2013 mudará a política do Windows PowerShell para RemoteSigned. Isto significa que você deve selecionar **Executar como administrador** para iniciar o Shell de Gerenciamento do SharePoint 2013 com uma permissão administrativa elevada. Essa mudança será aplicada em todas as sessões do Windows PowerShell. Para mais informações, consulte [Enumeração ExecutionPolicy](http://go.microsoft.com/fwlink/p/?linkid=242452).

Para mais informações sobre scripts e políticas de execução, consulte [about\_scripts](http://go.microsoft.com/fwlink/p/?linkid=144310) e [about\_Execution\_Policies](http://technet.microsoft.com/pt-br/library/dd347641.aspx), respectivamente.

## Aprendizado do Windows PowerShell

Há vários recursos de aprendizado do Windows PowerShell para profissionais de TI do SharePoint.

**Centro de Scripts do TechNet**

O Centro de Scripts do TechNet inclui vários recursos para ajudar você a aprender o básico do Windows PowerShell. Também contém repositórios de script com amostras ques geralmente são usadas com vários produtos da Microsoft. A tabela a seguir mostra os principais recursos de aprendizado.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Página</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://technet.microsoft.com/pt-br/library/bb978526.aspx">Documentação do Windows PowerShell no TechNet</a></p></td>
<td><p>Esta seção do TechNet Library contém cópias dos tópicos centrais de ajuda do Windows PowerShell. A seção também tem cópias da Web do documento Guia de Introdução do Windows PowerShell, da ajuda PowerShell.exe e de um manual Windows PowerShell.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://technet.microsoft.com/pt-br/scriptcenter/dd742419.aspx">Scripts com o Windows PowerShell</a></p></td>
<td><p>A home page dos recursos de aprendizado de scripts do Windows PowerShell.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187817">Manual do proprietário do Windows PowerShell</a></p></td>
<td><p>Guia da Web para introdução ao Windows PowerShell.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187819">Referência rápida do Windows PowerShell</a></p></td>
<td><p>Cópia baixável do documento de Referência Rápida instalado com o Windows PowerShell.</p></td>
</tr>
</tbody>
</table>


À medida que você for lendo esses recursos, considere que os seguintes conceitos e cmdlets sejam úteis e devem ser aprendidos antes de usar o Windows PowerShell para o SharePoint 2013:

  - [Get-Command](http://technet.microsoft.com/pt-br/library/dd347726.aspx)

  - [Get-Member](http://technet.microsoft.com/pt-br/library/dd315351.aspx)

  - [Get-Help](http://technet.microsoft.com/pt-br/library/dd347639.aspx)

  - [Aliasing](http://go.microsoft.com/fwlink/p/?linkid=113207)

  - [Pipes e pipeline no Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=187808)

  - [Conjuntos de parâmetros do cmdlet](http://go.microsoft.com/fwlink/p/?linkid=187810)

  - [Foreach-Object](http://go.microsoft.com/fwlink/p/?linkid=187812)

  - [Where-Object](http://go.microsoft.com/fwlink/p/?linkid=187811)

