---
title: Implantar o Servidor do Office Web Apps
TOCTitle: Implantar o Servidor do Office Web Apps
ms:assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219455(v=office.15)
ms:contentKeyID: 49647134
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Implantar o Servidor do Office Web Apps 

**Aplica-se a:** Office Web Apps Server

**Tópico modificado em:** 2017-10-05

**Resumo:** explica como implantar o Servidor do Office Web Apps no local para uso pelo SharePoint 2013 e pelo Lync Server 2013.

**Audiência:** profissionais de TI

Observe que este artigo abrange a instalação do Servidor do Office Web Apps para a sua empresa. Se você está procurando ajuda com a sua cópia pessoal do Office ou do Office Web Apps, veja <https://support.office.com>.

Implantação do [Servidor do Office Web Apps](office-web-apps-server-overview.md) envolve a instalação de algum software de pré-requisito e a execução de alguns comandos do Windows PowerShell, mas globalmente processo é projetado para ser bastante simples. Este artigo orienta os procedimentos para obter os seus servidores pronto, então lhe fornece os comando do Windows PowerShell para configurar o farm do Servidor do Office Web Apps.

Neste artigo:

  - Assista ao vídeo para ver como isso é feito

  - Examine esses recursos antes de começar

  - Prepare os servidores para executar o Servidor do Office Web Apps

  - Implantar um farm de servidores do Office Web Apps

  - Se você vir as mensagens "500 Exceções de Serviços da Web" ou "500.21 - Erro Interno do Servidor"

## Assista ao vídeo para ver como isso é feito

Assista o video a seguir para ver como definir o Servidor do Office Web Apps em um ambiente de teste. Você tembém terá acesso a uma visualização de como configurar o SharePoint 2013 para usar o Servidor do Office Web Apps.

**Definir o Servidor do Office Web Apps em um ambiente de teste**

> [!VIDEO https://www.microsoft.com/pt-br/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

## Examine esses recursos antes de começar

Certifique-se de considerar estes recursos antes de começar:

  - Para obter detalhes sobre os requisitos de hardware e software, [considere as diretrizes de planejamento](plan-office-web-apps-server.md).

  - Por padrão, o Servidor do Office Web Apps permite visualizar arquivos do Office, mas não editá-los. Para editar arquivos, você precisará de uma licença de edição, sobre a qual você pode saber mais em [Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md) e [Configurar o licenciamento no SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/jj219627\(v=office.15\)).

> [!NOTE]
> É possível realizar tarefas no Pacotes do Office 2013 usando um mouse, atalhos de teclado ou toque. Confira mais informações sobre como usar atalhos de teclado e toque em produtos e serviços do Office em <a href="https://go.microsoft.com/fwlink/p/?linkid=249150">Atalhos de teclado</a> e <a href="https://go.microsoft.com/fwlink/p/?linkid=253163">Guia de Toques do Office</a>.

## Prepare os servidores para executar o Servidor do Office Web Apps

Execute os seguintes procedimentos em todos os servidores que executarão o Servidor do Office Web Apps.

**Figura: Etapas para preparar os servidores para o Servidor do Office Web Apps**

![Os três passos principais para preparação de servidores do Office Web Apps Server.](images/JJ219455.af2a4690-4f8b-42c3-aab5-f7066bc0a936(Office.15).gif "Os três passos principais para preparação de servidores do Office Web Apps Server.") 

## Etapa 1: Instalar o software pré-requisitado para o Servidor do Office Web Apps

O Windows Server 2008 R2, o Windows Server 2012 e o Windows Server 2012 R2 têm requisitos ligeiramente diferentes, portanto, selecione abaixo o procedimento apropriado para instalar o sistema correto para seu sistema operacional.

**No Windows Server 2008 R2**

1.  Instale o seguinte software:
    
      - [Windows Server 2008 R2 Service Pack 1](http://go.microsoft.com/fwlink/p/?linkid=252370)
    
      - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=256560)
    
      - [Windows PowerShell 3.0](https://go.microsoft.com/fwlink/p/?linkid=244693)
    
      - [Atualização de plataforma para o Windows 7 SP1 e o Windows Server 2008 R2 SP1 (KB2670838)](https://go.microsoft.com/fwlink/p/?linkid=293629)

2.  Abra o prompt do Windows PowerShell como administrador e execute esses comandos para instalar as funções e serviços necessários.
    
    ```PowerShell
        Import-Module ServerManager
    ```
    
    Em seguida, execute este comando:
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,Web-Security,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Console,Ink-Handwriting,IH-Ink-Support,NET-Framework,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-Win-CFAC
    ```
    
    Se solicitado, reinicie o servidor.

**No Windows Server 2012**

1.  Abra o prompt do Windows PowerShell como administrador e execute este comando para instalar as funções e serviços necessários.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```
    
    Se solicitado, reinicie o servidor.

**No Windows Server 2012 R2**

1.  Instale o seguinte software:
    
      - [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?linkid=510096)

2.  Abra o prompt do Windows PowerShell como administrador e execute este comando para instalar as funções e serviços necessários.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```
    
    Se solicitado, reinicie o servidor.

## Etapa 2: Instalar o Servidor do Office Web Apps e atualizações relacionadas

Realize estas etapas em qualquer servidor que executará o Servidor do Office Web Apps.

1.  Baixe o Servidor do Office Web Apps no [Centro de Serviços de Licenciamento por Volume (VLSC)](https://go.microsoft.com/fwlink/p/?linkid=256561). Para baixar o Servidor do Office Web Apps, você deve ter uma licença em um Contrato de Licenciamento por Volume para o Office Professional Plus 2013, o Office Standard 2013 ou o Office para Mac 2011. O download está localizado nestes produtos do Office no portal do VLSC.

2.  Siga um destes procedimentos:
    
      - Para o Windows Server 2012 ou Windows Server 2012 R2, abra o arquivo .img diretamente e execute o arquivo **Setup.exe**.
    
      - Para o Windows Server 2008 R2 SP1, use um programa que possa montar ou extrair arquivos .img. Em seguida execute o arquivo **Setup.exe** (com um duplo clique sobre ele).

3.  Na página **Leia os Termos de Licença para Software Microsoft**, selecione **Aceito os termos deste contrato** e clique em **Continuar**.

4.  Na página **Escolher a localização do arquivo** , selecione a pasta onde deseja instalar os arquivos do Servidor do Office Web Apps (por exemplo, C:\\Arquivos de Programa\\Microsoft Office Web Apps) e selecione **Instalar Agora**. Se a pasta especificada não existir, o processo de instalação a criará..
    
    Recomendamos instalar o Servidor do Office Web Apps na unidade do sistema.

5.  Quando a instalação do Servidor do Office Web Apps estiver concluída, selecione **Fechar**.

6.  Baixe e instale o [Office Web Apps Server SP1](https://go.microsoft.com/fwlink/p/?linkid=510097) (recomendado para o Windows Server 2012 e o Windows Server 2008 R2 SP1. Necessário para o Windows Server 2012 R2.)
    
    > [!NOTE]
	> Se você quiser aplicar o Servidor do Office Web Apps SP1 mais tarde, siga as instruções em <a href="apply-software-updates-to-office-web-apps-server.md">Aplicar atualizações de software ao Servidor do Office Web Apps</a>.


7.  Confira as atualizações mais recentes do Servidor do Office Web Apps na lista disponível no [Centro de atualizações do TechNet para Office, servidores do Office e produtos relacionados](https://go.microsoft.com/fwlink/p/?linkid=280271).
    
    > [!NOTE]
	> Se você não tiver instalado o Office Web Apps Server SP1, aplique a <a href="https://go.microsoft.com/fwlink/p/?linkid=296579">KB2810007</a>.


## Etapa 3: Instalar pacotes de idiomas do Servidor do Office Web Apps

Os Pacotes de Idiomas 2013 do Servidor do Office Web Apps permitem que os usuários exibam arquivos do Office com base na web em vários idiomaas, se os mesmos forem abertos a partir das bibliotecas de documentos do SharePoint 2013, Outlook Web Access (como visualizações de anexo), e Lync 2013 (como transmissões do PowerPoint). Saiba mais sobre como os pacotes de idiomas funcionam em [Planning language packs for Office Web Apps Server](plan-office-web-apps-server.md).

Para instalar os pacotes de idiomas, siga estas etapas.


1.  Baixe os Pacotes de Idiomas do Servidor do Office Web Apps no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=263945).

2.  Execute o arquivo **WebAppsServerLP\_en-us\_x64.exe**.

3.  No Assistente se Pacote de Idiomas 2013 do Servidor do Office Web Apps , na página **Leia os Termos de Licença para Software Microsoft** , selecione**Eu aceito os termos dete acordo** e selecione **Continuar**.

4.  Quando a instalação do Servidor do Office Web Apps estiver concluída, selecione **Fechar**.

> [!IMPORTANT]
> <ul>
> <li><p>Para instalar pacotes de idiomas depois da criação do farm do Servidor do Office Web Apps, você deve remover o servidor do farm, instalar o pacote de idiomas nele e adicioná-lo de volta ao farm.</p></li>
> <li><p>Para o pacote de idiomas funcionar corretamente, será necessário instalar isso em todos os servidores no farm.</p></li>
> </ul>

## Implantar um farm de servidores do Office Web Apps

Siga os procedimentos em uma das três seçoes a seguir, baseado no tipo de farm do Servidor do Office Web Apps que você deseja criar.


> [!TIP]
> Se o Windows PowerShell não reconhecer o cmdlet <STRONG>New-OfficeWebAppsFarm</STRONG> ao executá-lo, pode ser necessário importar o módulo <STRONG>OfficeWebApps</STRONG> . Use este comando:<BR><CODE>Import-Module -Name OfficeWebApps</CODE>



## Implantar um farm de servidor único do Servidor do Office Web Apps que usa HTTP

Se estiver implantando o Servidor do Office Web Apps para testes ou uso interno e não precisar fornecer a funcionalidade do Servidor do Office Web Apps ao Lync Server 2013, este é o procedimento ideal para você. Aqui você instala uma farm do Servidor do Office Web Apps em um único servidor usando HTTP. Não é necessário um certificado ou balanceador de carga, mas você precisará de um servidor físico dedicado ou uma instância de máquina virtual que não esteja executando nenhum outro aplicativo de servidor.

Você pode usar este farm do Servidor do Office Web Apps para fornecer a funcionalidade do Office Web Apps ao SharePoint 2013.

**Figura: Etapas para implantar o Servidor do Office Web Apps**

![Os três passos principais para implantação de um único farm de servidores do Office Web Apps Server.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "Os três passos principais para implantação de um único farm de servidores do Office Web Apps Server.")

## Etapa 1: criar o farm do Servidor do Office Web Apps

Use o comando **New-OfficeWebAppsFarm** para criar um novo farm Servidor do Office Web Apps que consiste em um único servidor, como mostrado no exemplo a seguir.

```PowerShell
    New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled
```

**Parâmetros**

  - **–InternalURL** é o nome do servidor que executa o Servidor do Office Web Apps, como **http://servername**.

  - **–AllowHttp** configura o farm para uso do HTTP.

  - **–EditingEnabled** permite a edição no Office Web Apps quando usado com o SharePoint 2013. Esse parâmetro: não é usado pelo Lync Server 2013 porque esse host não oferece suporte para edição.

Parâmetros adicionais que configuram serviços de tradução, servidores de proxy, suporte a ClipArt e Visualizadores Online são descritos em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Se você vir as mensagens "500 Exceções de Serviços da Web" ou "500.21 - Erro Interno do Servidor"

## Etapa 2: verificar se o farm do Servidor do Office Web Apps foi criado com êxito

Depois da criação da farm, seus detalhes são exibidos no prompt do Windows PowerShell. Para verificar se o Servidor do Office Web Apps foi instalado e configurado corretamente, use um navegador Web para acessar a URL de descoberta do Servidor do Office Web Apps, conforme mostrado no exemplo a seguir. A URL de descoberta é o parâmetro *InternalUrl* especificado ao configurar a farm do Servidor do Office Web Apps, seguido de **/hosting/discovery**, por exemplo:

```
    http://servername/hosting/discovery
```

Se o Servidor do Office Web Apps estiver funcionando corretamente, deve haver um arquivo XML de descoberta WOPI no navegador Web. As primeiras linhas do arquivo devem se parecer com o seguinte.

```XML
    <?xml version="1.0" encoding="utf-8" ?> 
    - <wopi-discovery>
    - <net-zone name="internal-http">
    - <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
    <action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```

## Etapa 3: configurar o host

O farm está pronto para fornecer a funcionalidade do Office Web Apps aos hosts via HTTP. Visite [Configurar o Office Web Apps para o SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md) para saber mais sobre como configurar os hosts.

## Implantar um farm de servidor único do Servidor do Office Web Apps que usa HTTPS
<a name="singlehttps"> </a>

Para a maioria dos ambientes de produção, recomendamos com toda a veemência o uso do HTTPS para seus recursos de segurança. Além disso, HTTPS é necessário se você desejar fornecer funionalidade do Servidor do Office Web Appspara o Lync Server 2013, que permite aos usuários visualizarem transmissões do PowerPoint em um navegador. Veja como instalar um farm do Servidor do Office Web Apps de servidor único que usa HTTPS. Será necessário instalar um certificado no servidor, conforme descrito nas [comunicações do Securing Servidor do Office Web Apps utilizando HTTPS](plan-office-web-apps-server.md).

Este farm do Servidor do Office Web Apps fornecerá a funcionalidade do Office Web Apps para o SharePoint 2013 e o Lync Server 2013.

**Figura: Etapas para implantar o Servidor do Office Web Apps**

![Os três passos principais para implantação de um único farm de servidores do Office Web Apps Server.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "Os três passos principais para implantação de um único farm de servidores do Office Web Apps Server.")

## Etapa 1: criar o farm do Servidor do Office Web Apps

Use o comando **New-OfficeWebAppsFarm** para criar um novo farm Servidor do Office Web Apps que consiste em um único servidor, como mostrado no exemplo a seguir.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled
```

**Parâmetros**

  - **–InternalURL** é um nome de domínio totalmente qualificado (FQDN) do servidor que executa o Servidor do Office Web Apps, como **http://nomeservidor.contoso.com**.

  - **–ExternalURL** é o FQDN que pode ser acessado na Internet.

  - **–CertificateName** é o nome amigável do certificado.

  - **–EditingEnabled** é opcional e permite a edição no Office Web Apps quando usado com o SharePoint 2013. Esse parâmetro: não é usado pelo Lync Server 2013 porque esse host não oferece suporte para edição.

Parâmetros adicionais que configuram serviços de tradução, servidores de proxy, suporte a ClipArt e Visualizadores Online são descritos em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Se você vir as mensagens "500 Exceções de Serviços da Web" ou "500.21 - Erro Interno do Servidor"

## Etapa 2: verificar se o farm do Servidor do Office Web Apps foi criado com êxito

Depois da criação da farm, seus detalhes são exibidos no prompt do Windows PowerShell. Para verificar se o Servidor do Office Web Apps foi instalado e configurado corretamente, use um navegador Web para acessar a URL de descoberta do Servidor do Office Web Apps, conforme mostrado no exemplo a seguir. A URL de descoberta é o parâmetro *InternalUrl* especificado ao configurar a farm do Servidor do Office Web Apps, seguido de **/hosting/discovery**, por exemplo:

```
    https://server.contoso.com/hosting/discovery
```

Se o Servidor do Office Web Apps funcionar conforme o esperado, você deverá ver um arquivo XML de descoberta do WOPI (Interface de Plataforma Aberta de aplicativo Web) em seu navegador da web. As primeiras linhas desse arquivo devem se parecer com o exemplo a seguir:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="xls"/><action name="view" 
```

> [!NOTE]
> Dependendo das configurações de segurança de seu navegador da Web, talvez você veja uma mensagem que solicita a seleção de <strong>Mostrar todo conteúdo</strong> antes de o conteúdo do arquivo XML de descoberta ser exibido.


## Etapa 3: configurar o host

O farm está pronto para fornecer a funcionalidade do Office Web Apps aos hosts sobre HTTPS. Visite os artigos a seguir para obter mais informações sobre como configurar os hosts.

  - [Configurar o Office Web Apps para o SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Implantando o Servidor do Office Web Apps e o Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

## Implantar um farm com múltiplos servidores e carga equilibrada do Servidor do Office Web Apps que usa HTTPS
<a name="multihttps"> </a>

Se você antecipar muito tráfego para seu farm do Servidor do Office Web Apps , e desejar que ele esteja disponível através da Internet, bem como na sua rede interna, este tipo de topologia é o caminho a percorrer. Esta seção mostra como instalar um farm do Servidor do Office Web Apps de servidor múltiplo que usa um balanceador de carga e HTTPS. Se você estiver interessado, [leia mais sobre esta topologia](plan-office-web-apps-server.md).

Antes de começar, verifique se o balanceador de carga está configurado conforme descrito em [Load balancer requirements for Office Web Apps Server](plan-office-web-apps-server.md). Além disso, você precisará instalar um certificado no balanceador de carga, conforme descrito em [Protegendo as comunicações do Office Web Apps Server com o uso do HTTPS](plan-office-web-apps-server.md). Esse farm do Servidor do Office Web Apps fornecerá a funcionalidade do Office Web Apps para o SharePoint 2013 e o Lync Server 2013.

**Figura: Etapas para implantar o Servidor do Office Web Apps**

![Os quatro passos principais para implantação de um farm múltiplo de servidores do Office Web Apps Server..](images/JJ219455.4c4b31cb-961b-4efd-b755-a18bdcb5c191(Office.15).gif "Os quatro passos principais para implantação de um farm múltiplo de servidores do Office Web Apps Server..")

## Etapa 1: criar o farm do Servidor do Office Web Apps no primeiro servidor

Use o comando **New-OfficeWebAppsFarm** para criar um novo farm do Servidor do Office Web Apps no primeiro servidor, conforme mostrado no exemplo a seguir.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled
```

**Parâmetros**

  - **–InternalURL** é um nome de domínio totalmente qualificado (FQDN) do servidor que executa o Servidor do Office Web Apps, como **http://nomeservidor.contoso.com**.

  - **–ExternalURL** é o nome do FQDN que pode ser acessado na Internet.

  - **-SSLOffloaded** habilita o descarregamento da terminação SSL para o balanceador de carga.

  - **–EditingEnabled** é opcional e permite a edição no Office Web Apps quando usado com o SharePoint 2013. Esse parâmetro: não é usado pelo Lync Server 2013 porque esse host não oferece suporte para edição.

Outros parâmetros que configuram serviços de tradução, servidores de proxy, suporte a ClipArt e Visualizadores Online são descritos em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

Se você vir as mensagens "500 Exceções de Serviços da Web" ou "500.21 - Erro Interno do Servidor"

## Etapa 2: adicionar mais servidores ao farm

Depois que o primeiro servidor estiver executando o Servidor do Office Web Apps, execute o comando **New-OfficeWebAppsMachine** em cada servidor que deseja adicionar à farm do Servidor do Office Web Apps. Para o parãmetro **–MachineToJoin**, use o nome do computador de um servidor que já está na farm do Servidor do Office Web Apps. Por exemplo, se servidor1.contoso.com já estiver na farm, use o seguinte:

```PowerShell
    New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
```

Deseja mais informações sobre esses parâmetros? Encontre-os no [New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps).

## Etapa 3: verificar se o farm do Servidor do Office Web Apps foi criado com êxito

Depois da criação da farm, seus detalhes são exibidos no prompt do Windows PowerShell. Para verificar se o Servidor do Office Web Apps foi instalado e configurado corretamente, use um navegador Web para acessar a URL de descoberta do Servidor do Office Web Apps, conforme mostrado no exemplo a seguir. A URL de descoberta é o parâmetro *InternalUrl* especificado ao configurar a farm do Servidor do Office Web Apps, seguido de **/hosting/discovery**, por exemplo:

```
    https://server.contoso.com/hosting/discovery
```

Se o Servidor do Office Web Apps funcionar conforme o esperado, você deverá ver um arquivo XML de descoberta do WOPI (Interface de Plataforma Aberta de aplicativo Web) em seu navegador da web. As primeiras linhas desse arquivo devem se parecer com o exemplo a seguir:

```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xlsb"/> 
```

> [!NOTE]
> Dependendo das configurações de segurança de seu navegador da Web, talvez você veja uma mensagem que solicita a seleção de <strong>Mostrar todo conteúdo</strong> antes de o conteúdo do arquivo XML de descoberta ser exibido.

## Etapa 4: configurar o host

O farm está pronto para fornecer a funcionalidade do Office Web Apps aos hosts sobre HTTPS. Visite os artigos a seguir para obter mais informações sobre como configurar os hosts.

  - [Configurar o Office Web Apps para o SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Implantando o Servidor do Office Web Apps e o Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

## Se você vir as mensagens "500 Exceções de Serviços da Web" ou "500.21 – Erro Interno do Servidor"

Se recursos do .NET Framework 3.5 forem instalados e depois removidos, você poderá ver as mensagens “500 Exceções de Serviços da Web” ou “500.21 – Erro Interno do Servidor” ao executar cmdlets do OfficeWebApps. Para corrigir, execute os comandos de exemplo a seguir, a partir de um prompt de comando com privilégios elevados para excluir as configurações que poderiam impedir o funcionamento correto do Servidor do Office Web Apps:

**Para o Windows Server 2008 R2**

```PowerShell
    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -iru

    iisreset /restart /noforce
```

**Para o Windows Server 2012 ou Windows Server 2012 R2**

```PowerShell
    dism /online /enable-feature /featurename:IIS-ASPNET45
```

## Consulte também


[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Planejar-se para o Servidor do Office Web Apps](plan-office-web-apps-server.md)  
[Configurar o Office Web Apps para o SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)  


[Implantando o Servidor do Office Web Apps e o Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)  
  

[](configure-office-web-apps-for-sharepoint-2013.md)

