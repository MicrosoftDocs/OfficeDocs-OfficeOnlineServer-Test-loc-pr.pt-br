---
title: Aplicar atualizações de software ao Servidor do Office Web Apps
TOCTitle: Aplicar atualizações de software ao Servidor do Office Web Apps
ms:assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ966220(v=office.15)
ms:contentKeyID: 56710022
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Aplicar atualizações de software ao Servidor do Office Web Apps 

**Aplica-se a:** Office Web Apps Server

**Tópico modificado em:** 2016-12-16

**Resumo:** explica como aplicar atualizações de software a um farm do Office Web Apps Server.

**Audiência:** profissionais de TI

Depois do lançamento de uma nova versão do Servidor do Office Web Apps, a Microsoft disponibiliza uma série de atualizações de software para ajudar a aumentar a segurança, o desempenho e a confiabilidade dos servidores. Este artigo descreve como aplicar atualizações de software a servidores individuais em um farm do Servidor do Office Web Apps.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este artigo faz parte do <a href="content-roadmap-for-office-web-apps-server.md">Mapa de conteúdo para o Servidor do Office Web Apps</a>. Use o mapa como um ponto inicial para acessar artigos, downloads e vídeos que ajudam a implantar e gerenciar o Servidor do Office Web Apps.<br />
<strong>Deseja obter ajuda com o Office Web Apps em seu desktop ou dispositivo móvel?</strong> É possível encontrar estas informações pesquisando por &quot;Office Web Apps&quot; no <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.</td>
</tr>
</tbody>
</table>

> [!WARNING]
> A aplicação de atualizações do Servidor do Office Web Apps usando o processo de atualizações automáticas não é compatível com o Servidor do Office Web Apps por que as atualizações do Servidor do Office Web Apps devem ser aplicadas de forma específica, conforme descrito neste artigo. Se as atualizações do Servidor do Office Web Apps forem aplicadas automaticamente, os usuários poderão não conseguir exibir ou editar documentos no Office Web Apps. Caso isto ocorra, é necessário reestruturar seu farm do Servidor do Office Web Apps. Para reestruturar um farm, é necessário remover o Servidor do Office Web Apps do farm usando o <A href="https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps">Remove-OfficeWebAppsMachine</A>, desinstalar o Servidor do Office Web Apps por meio do Adicionar ou remover programas, para depois reinstalar o Servidor do Office Web Apps seguindo as etapas descritas no <A href="deploy-office-web-apps-server.md">Implantar o Servidor do Office Web Apps</A>. Depois de reinstalá-lo, aplique a atualização seguindo os passos descritos neste artigo.<BR>É importante ler com atenção as diretrizes constantes em <A href="plan-office-web-apps-server.md">Planejamento de atualizações para o Office Web Apps Server</A> para estabelecer um processo de atualização para o farm do Servidor do Office Web Apps.

## Antes de iniciar

Veja a lista das mais recentes atualizações do Servidor do Office Web Apps no [blog Atualizações do Microsoft Office](http://go.microsoft.com/fwlink/p/?linkid=280269) e no [Centro de atualização do Office, servidores do Office e produtos relacionados](http://go.microsoft.com/fwlink/p/?linkid=280271).

As atualizações lançadas para o Servidor do Office Web Apps atualizarão o Servidor do Office Web Apps e todos os pacotes de idiomas do Servidor do Office Web Apps que estiverem instalados. Não há atualizações separadas para os pacotes de idiomas do Servidor do Office Web Apps.

Como parte do processo de atualização, será necessário recriar o farm do Servidor do Office Web Apps. Para preparar a recriação do farm do Servidor do Office Web Apps, reveja as propriedades atuais do seu farm do Servidor do Office Web Apps executando o cmdlet **Get-OfficeWebAppFarm** do Windows PowerShell e reveja os parâmetros para [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps). Os parâmetros usados para **New-OfficeWebAppsFarm** devem ser os mesmos usados na configuração inicial do farm do Servidor do Office Web Apps.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Você pode executar as tarefas deste artigo usando um mouse, atalhos de teclado ou toque. Para obter mais informações, consulte os seguintes recursos:
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=249150">Atalhos de teclado</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=249151">Toque</a></p></li>
</ul></td>
</tr>
</tbody>
</table>

## Aplicação de atualizações de software a um farm do Office Web Apps Server com um único servidor

Para aplicar atualizações de software a um farm do Servidor do Office Web Apps com um único servidor, remova o Servidor do Office Web Apps do farm, aplique a atualização de software e recrie o farm Servidor do Office Web Apps. Caso você tenha apenas um servidor em seu farm do Servidor do Office Web Apps, os usuários não conseguirão usar o Office Web Apps durante a atualização do servidor. Por isso, considere atualizar o Servidor do Office Web Apps fora do expediente ou fora de horários críticos de uso do servidor.

**Para aplicar atualizações de software a um farm de um único servidor**

1.  Se a atualização ainda não tiver sido baixada para o Servidor do Office Web Apps, baixe a atualização do Servidor do Office Web Apps que deve ser aplicada no [Centro de Download da Microsoft](http://go.microsoft.com/fwlink/p/?linkid=280274).

2.  No Servidor do Office Web Apps em que deve ser aplicada a atualização de software, abra o prompt Windows PowerShell como um administrador e execute o seguinte comando.
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

3.  Instale a atualização do Servidor do Office Web Apps no servidor. Se solicitado, reinicie o servidor.

4.  Abra o prompt do Windows PowerShell como administrador e execute o cmdlet **New-OfficeWebAppsFarm** para recriar um farm do Servidor do Office Web Apps. A URL especificada para o parâmetro **–InternalURL** é o nome do servidor que executa o Servidor do Office Web Apps, por exemplo, **http://Contoso-WAC**. Neste caso, seria usado o mesmo nome do farm antigo do Servidor do Office Web Apps. Use os mesmos parâmetros adicionais usados na primeira criação do farm do Servidor do Office Web Apps. Por exemplo, o parâmetro **–AllowHttp** configura o farm para usar HTTP, enquanto o parâmetro **–EditingEnabled** permite a edição no Office Web Apps quando é usado junto com o SharePoint 2013. O parâmetro **–EditingEnabled** não é usado pelo Lync Server 2013 ou pelo Exchange Server 2013 porque esses hosts não são compatíveis com edição.
    
    O código no exemplo a seguir cria um novo farm do Servidor do Office Web Apps chamado http://Contoso-WAC.
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    Parâmetros adicionais que configuram serviços de tradução, servidores de proxy, suporte a clip-art e Visualizadores Online são descritos em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

## Aplicação de atualizações de software a um farm do Office Web Apps Server com vários servidores

Para aplicar atualizações de software a um farm do Servidor do Office Web Apps com vários servidores, primeiro remova um dos servidores do pool do balanceador de carga e do farm, aplique a atualização de software e crie um farm atualizado do Servidor do Office Web Apps. Depois, remova e atualize os outros servidores no farm do Servidor do Office Web Apps e adicione-os ao novo farm atualizado. A tráfego de balanceamento é carregado ao novo farm quando há servidores suficientes no novo farm para sustentar o tráfego atual. Ao usar este processo de atualização, os usuários podem abrir e editar documentos Office Web Apps sem interrupções.

**Para aplicar atualizações de software a um farm com vários servidores**

1.  Baixe a atualização do Servidor do Office Web Apps que deve ser aplicada do [Centro de Download da Microsoft](http://go.microsoft.com/fwlink/p/?linkid=280274) para um local da rede disponível no farm do Servidor do Office Web Apps.

2.  Remova do pool do balanceador de carga o Servidor do Office Web Apps no qual deve ser aplicada a atualização de software.

3.  No Servidor do Office Web Apps removido, abra o prompt do Windows PowerShell como administrador e execute o seguinte comando.
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

4.  Instale a atualização do Servidor do Office Web Apps no servidor. Se solicitado, reinicie o servidor.

5.  Abra o prompt do Windows PowerShell como administrador e crie um farm atualizado do Servidor do Office Web Apps usando o cmdlet **New-OfficeWebAppsFarm**. A URL especificada para o parâmetro **–InternalURL** é o nome do servidor que executa o Servidor do Office Web Apps, por exemplo, **http://Contoso-WAC**. Neste caso, seria usado o mesmo nome do farm antigo do Servidor do Office Web Apps. Use os mesmos parâmetros adicionais usados na primeira criação do farm do Servidor do Office Web Apps. Por exemplo, o parâmetro **–AllowHttp** configura o farm para usar HTTP, enquanto o parâmetro **–EditingEnabled** permite a edição no Office Web Apps quando é usado junto com o SharePoint 2013. O parâmetro **–EditingEnabled** não é usado pelo Lync Server 2013 ou pelo Exchange Server 2013 porque esses hosts não são compatíveis com edição.
    
    O código no exemplo a seguir cria um novo farm do Servidor do Office Web Apps chamado http://Contoso-WAC.
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    Parâmetros adicionais que configuram serviços de tradução, servidores de proxy, suporte a clip-art e Visualizadores Online são descritos em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

6.  Dependendo de quantos servidores há no farm do Servidor do Office Web Apps, carregue o tráfego de balanceamento para o novo farm. Esta etapa pode ser adiada até que haja mais servidores atualizados para serem adicionados ao farm.

7.  Siga estas etapas para cada servidor remanescente no farm.
    
    1.  Remova o próximo Servidor do Office Web Apps do pool do balanceador de carga.
    
    2.  Instale a atualização do Servidor do Office Web Apps no servidor. Se solicitado, reinicie o servidor.
    
    3.  Abra o prompt do Windows PowerShell como administrador e execute o seguinte comando. O parâmetro **–MachineToJoin** adiciona o servidor atual a um farm atual do Servidor do Office Web Apps. Neste caso, o objetivo é adicionar o servidor ao farm atualizado do Servidor do Office Web Apps. Para isso, use o nome do computador de um dos servidores no farm atualizado do Servidor do Office Web Apps.
        
        ```PowerShell
            New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
        ```

## Consulte também


[Remove-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[Get-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/get-officewebappsfarm?view=officewebapps-ps)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
  

[](content-roadmap-for-office-web-apps-server.md)

