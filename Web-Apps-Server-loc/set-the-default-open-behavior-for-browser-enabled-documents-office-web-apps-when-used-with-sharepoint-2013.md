---
title: Definir o comportamento padrão de abertura para documentos habilitados para navegadores (Office Web Apps quando usados com o SharePoint 2013)
TOCTitle: Definir o comportamento padrão de abertura para documentos habilitados para navegadores
ms:assetid: e27e0bc8-5fb5-4bb1-8157-d7c90654175e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ee837425(v=office.15)
ms:contentKeyID: 50181270
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Definir o comportamento padrão de abertura para documentos habilitados para navegadores (Office Web Apps quando usados com o SharePoint 2013)

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2016-12-16_

**Resumo:** explica como configurar o comportamento de abertura padrão de documentos do Office nos conjuntos de sites e bibliotecas de documentos do SharePoint.

**Público:** profissionais de TI

Para abrir rapidamente um documento em uma biblioteca do SharePoint 2013, basta clicar em seu título. O que acontecerá em seguida (se o arquivo será aberto em um aplicativo cliente ou no navegador) dependerá de vários fatores, como qual é o tipo de arquivo, como você configurou seu farm do Servidor do Office Web Apps e como foram definidas as configurações do recurso OpenInClient da biblioteca ou do conjunto de sites. As etapas a seguir mostram como configurar o comportamento de abertura padrão para documentos do Office onde você tiver o SharePoint 2013 configurado para usar o Servidor do Office Web Apps.

## Definir como os documentos são abertos de bibliotecas do SharePoint 2013

Por padrão, depois que o SharePoint 2013 for configurado para usar o Servidor do Office Web Apps, clicar em um arquivo do Word, do PowerPoint, do Excel ou do OneNote o abrirá no navegador. Os documentos PDF abrem no Word Web App. Há duas maneiras de alterar o comportamento padrão a fim de permitir que aplicativos clientes abram os arquivos diretamente:

  - **Para o farm doSharePoint 2013** Você pode ajustar o comportamento de abertura padrão por tipo de arquivo para o farm do SharePoint 2013 usando os cmdlets [New-SPWOPIBinding](new-spwopibinding.md) e [Set-SPWOPIBinding](set-spwopibinding.md) do Windows PowerShell. Esses cmdlets também podem ser usados para[ajustar o comportamento de documentos PDF](http://go.microsoft.com/fwlink/p/?linkid=330246).

  - **Em conjuntos de sites ou bibliotecas de documento** Os administradores e usuários de conjunto de sites podem usar o recurso OpenInClient do SharePoint 2013 para especificar se os arquivos do Office serão abertos no aplicativo cliente ou no navegador. Os usuários podem alterar essa configuração nas propriedades da biblioteca de documento e os administradores do conjunto de sites podem alterar essa configuração na Administração do Conjunto de Sites ou usando o cmdlet [Enable-SPFeature](https://technet.microsoft.com/pt-br/library/ff607803\(v=office.15\)) para habilitar o recurso OpenInClient. Consulte a próxima seção para obter vários métodos diferentes para habilitar o recurso OpenInClient.

Em geral, o recurso OpenInClient substitui quaisquer associações WOPI definidas entre o SharePoint 2013 e o Servidor do Office Web Apps. Em outras palavras, se o recurso OpenInClient de uma biblioteca ou conjunto de sites do SharePoint 2013 estiver habilitado, os documentos serão abertos no aplicativo cliente, mesmo se o servidor do SharePoint 2013 tiver sido configurado para utilizar o Servidor do Office Web Apps.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>A configuração do comportamento de abertura padrão de documentos habilitados para navegador não afetará se os usuários podem usar os recursos <strong>Check-out</strong> e <strong>Enviar para</strong> no SharePoint 2013 para baixar documentos. Para obter informações sobre como configurar as permissões de checkout, de download e de exibição no SharePoint 2013, consulte <a href="https://technet.microsoft.com/pt-br/library/cc262939(v=office.15)">Planejamento de permissões para sites e conteúdo no SharePoint 2013</a>.</td>
</tr>
</tbody>
</table>


## Definir o recurso OpenInClient para uma biblioteca de documentos ou coleção de sites

Utilize um dos seguintes procedimentos para definir o recurso OpenInClient no SharePoint 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alguns destes procedimentos usam o Shell de Gerenciamento do SharePoint 2013 para executar cmdlets do SharePoint. Se você optar por usar o console do Windows PowerShell, deverá adicionar o snap-in Microsoft.SharePoint.PowerShell usando o cmdlet <strong>Add-PSSnapin</strong>. Para obter mais informações sobre como usar o Windows PowerShell com o SharePoint 2013, consulte <a href="use-windows-powershell-to-administer-sharepoint-2013.md">Usar o Windows Powershell para administrar o SharePoint 2013</a>.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Você pode completar tarefas em todos Pacotes do Office 2013 usando um mouse, atalhos de teclado ou toque. Para obter informações sobre como usar atalhos de teclado e toque com produtos e serviços do Office, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=249150">Atalhos de teclado</a> e <a href="http://go.microsoft.com/fwlink/p/?linkid=253163">Guia de Toque do Office</a>.</td>
</tr>
</tbody>
</table>


 **Definir o recurso OpenInClient para conjuntos de sites**

1.  No conjunto de sites do SharePoint, escolha o ícone **Configurações** \> **Configurações do Site**.

2.  Na página **Configurações do Site**, sob **Administração do Conjunto de Sites**, escolha **Recursos do Conjunto de Sites**.

3.  Na página **Recursos**, para o recurso **Abrir Documentos em Aplicativos Cliente por Padrão**, escolha **Ativar** para habilitar o recurso OpenInClient (os documentos serão abertos no aplicativo cliente), ou **Desativar** para desabilitar o recurso OpenInClient (os documentos serão abertos no navegador).

 **Definir o comportamento de abertura padrão para conjuntos de sites usando o Windows PowerShell**

1.  Primeiro, verifique se você possui as seguintes associações:
    
      - A função de servidor fixa **securityadmin** na instância SQL Server.
    
      - A função de banco de dados fixa **db\_owner** em todos os bancos de dados que devem ser atualizados.
    
      - Grupo de administradores no servidor onde você está executando cmdlets do Windows PowerShell.
    
    Além disso, dê uma olhada em [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) e adicione qualquer outra associação necessária.
    
    Um administrador pode usar o cmdlet **Add-SPShellAdmin** para conceder permissões para usar cmdlets do SharePoint 2013.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Se você não possui permissões, entre em contato com seu administrador de Configuração ou com o administrador do SQL Server para solicitá-las. Para obter informações adicionais sobre permissões do Windows PowerShell, consulte <a href="use-windows-powershell-to-administer-sharepoint-2013.md">Permissões</a> e <a href="https://technet.microsoft.com/pt-br/library/ff607596(v=office.15)">Add-SPShellAdmin</a>.</td>
    </tr>
    </tbody>
    </table>


2.  Abra um Shell de Gerenciamento do SharePoint 2013 elevado:
    
    **No Windows Server 2008**
    
    1.  No menu **Iniciar**, selecione **Todos os Programas**.
    
    2.  Selecione **Produtos Microsoft SharePoint 2013**.
    
    3.  Escolha **Shell de Gerenciamento do SharePoint 2013** para exibir a barra de aplicativos (clique com o botão direito).
    
    4.  Do menu de atalho, escolha **Executar como administrador**.
    
    **No Windows Server 2012**
    
    1.  Passe o dedo a partir da borda da tela para mostrar os botões e selecione **Pesquisar** para consultar todos os aplicativos que estão instalados no computador.
    
    2.  Escolha (clique com o botão direito do mouse) **Shell de Gerenciamento do SharePoint 2013** para exibir a barra de aplicativos.
    
    3.  Na barra de aplicativos, selecione **Executar como administrador**.

3.  No prompt de comando do Windows PowerShell, digite um dos seguintes comandos:
    
      - Para habilitar o recurso OpenInClient para um conjunto de sites específico (para abrir documentos no aplicativo cliente), digite este comando:
        
            Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        onde *\<SiteCollURL\>* é a URL do conjunto de sites.
    
      - Para habilitar o recurso OpenInClient para todos os conjuntos de sites (para abrir documentos no aplicativo cliente), digite este comando:
        
            Get-SPSite -limit ALL |foreach{ Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
    
      - Para desabilitar o recurso OpenInClient para um conjunto de sites específico (para abrir documentos no navegador), digite este comando:
        
            Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        onde *\<SiteCollURL\>* é a URL do conjunto de sites.
    
      - Para desabilitar o recurso OpenInClient para todos os conjuntos de sites (para abrir documentos no navegador), digite este comando:
        
            Get-SPSite -limit ALL |foreach{ Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }

 **Definir o comportamento de abertura padrão para uma biblioteca de documentos usando a página de configurações de biblioteca de documentos**

1.  Na página da biblioteca de documentos, escolha a guia **Biblioteca**.

2.  No grupo **Configurações**, escolha **Configurações da Biblioteca**.

3.  Na página **Configurações da Biblioteca de Documentos**, escolha **Configurações avançadas**.

4.  Na página **Configurações Avançadas**, em **Abrindo Documento no Navegador**, selecione uma destas opções:
    
      - **Abrir no aplicativo cliente**   quando um usuário escolher um documento dessa biblioteca, o documento será aberto no aplicativo cliente correspondente, se estiver disponível.
    
      - **Abrir no navegador**   quando um usuário escolher um documento nessa biblioteca, o documento será aberto no navegador da Web no aplicativo da Web para o tipo de documento. Quando o documento for aberto no aplicativo da Web, o usuário poderá decidir abrir o documento no aplicativo cliente.
    
      - **Usar o padrão do servidor**   Quando um usuário escolher um documento nessa biblioteca, o documento será aberto usando o comportamento de abertura padrão especificado para o servidor que estiver executando o SharePoint 2013.

 **Definir o comportamento de abertura padrão para bibliotecas de documentos protegidas por IRM usando o Windows PowerShell**

1.  Primeiro, verifique se você possui as seguintes associações:
    
      - A função de servidor fixa **securityadmin** na instância SQL Server.
    
      - A função de banco de dados fixa **db\_owner** em todos os bancos de dados que devem ser atualizados.
    
      - Grupo de administradores no servidor onde você está executando cmdlets do Windows PowerShell.
    
    Além disso, dê uma olhada em [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) e adicione qualquer outra associação necessária.
    
    Um administrador pode usar o cmdlet **Add-SPShellAdmin** para conceder permissões para usar cmdlets do SharePoint 2013.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Se você não possuir permissões, entre em contato com seu administrador de Configuração ou com o administrador do SQL Server para solicitá-las. Para obter informações adicionais sobre permissões do Windows PowerShell, consulte <a href="use-windows-powershell-to-administer-sharepoint-2013.md">Permissões</a> e <a href="https://technet.microsoft.com/pt-br/library/ff607596(v=office.15)">Add-SPShellAdmin</a>.</td>
    </tr>
    </tbody>
    </table>


2.  Abra um Shell de Gerenciamento do SharePoint 2013 elevado:
    
    **No Windows Server 2008**
    
    1.  No menu **Iniciar**, selecione **Todos os Programas**.
    
    2.  Selecione **Produtos Microsoft SharePoint 2013**.
    
    3.  Escolha **Shell de Gerenciamento do SharePoint 2013** para exibir o menu de atalho (clique com o botão direito).
    
    4.  Do menu de atalho, escolha **Executar como administrador**.
    
    **No Windows Server 2012**
    
    1.  Passe o dedo a partir da borda da tela para mostrar os botões e selecione **Pesquisar** para consultar todos os aplicativos que estão instalados no computador.
    
    2.  Escolha (clique com o botão direito) **Shell de Gerenciamento do SharePoint 2013** para exibir a barra de aplicativos.
    
    3.  Na barra de aplicativos, selecione **Executar como administrador**.

3.  No prompt de comando do Windows PowerShell, digite este comando:
    
        Get-SPWeb -site <SiteCollURL> | % {$_.Lists} | where {$_.IrmEnabled -eq $true} | % {$_.DefaultItemOpen =[Microsoft.Sharepoint.DefaultItemOpen]::<DefaultItemOpenSetting>; $_.Update()}
    
    no qual:
    
      - *\<SiteCollURL\>* é a URL do conjunto de sites onde residem as bibliotecas de documentos.
    
      - *\<DefaultItemOpenSetting\>* é um valor da enumeração **DefaultItemOpen** que especifica o comportamento de abertura padrão. Use **PreferClient** para abrir documentos no aplicativo cliente associado (se estiver disponível). Use **Browser** para abrir documentos no navegador.

## Consulte também


[Get-SPWOPIBinding](get-spwopibinding.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Usar o Windows Powershell para administrar o SharePoint 2013](use-windows-powershell-to-administer-sharepoint-2013.md)  
[Servidor do Office Web Apps](office-web-apps-server.md)  


[Get-SPWeb](https://technet.microsoft.com/pt-br/library/ff607807\(v=office.15\))  
[Get-SPSite](https://technet.microsoft.com/pt-br/library/ff607950\(v=office.15\))  
[Get-SPFeature](https://technet.microsoft.com/pt-br/library/ff607945\(v=office.15\))

