---
title: Configurar o Office Web Apps para o SharePoint 2013
TOCTitle: Configurar o Office Web Apps para o SharePoint 2013
ms:assetid: a5276781-133b-413c-beca-b851e17c2081
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ff431687(v=office.15)
ms:contentKeyID: 49647117
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Configurar o Office Web Apps para o SharePoint 2013

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2016-12-16_

**Resumo:** Explica como configurar o SharePoint 2013 para usar o Office Web Apps.

**Público:** profissionais de TI

O presente arquivo ressalta onde [Implantar o Servidor do Office Web Apps](deploy-office-web-apps-server.md) foi ignorado. No mesmo artigo, vocÊ adicionará o Servidor do Office Web Apps. Neste, você irá configurar o SharePoint 2013 para usar o Servidor do Office Web Apps. Primeiro, será necessário executar alguns cmdlets do Windows PowerShell a patrir do SharePoint 2013, após o qual os usuários serão capazes de abrir arquivos doOffice a partir das bibliotecas de documentos do SharePoint 2013 em um navegador.

Se você não está familiarizado com os recursos doServidor do Office Web Apps, [confira o tópico visão geral](office-web-apps-server-overview.md).

Neste artigo:

  - Antes de configurar o SharePoint 2013 para usar o Servidor do Office Web Apps

  - Configurar o SharePoint 2013 para usar o Office Web Apps Server

  - Solução de problemas de erros no Office Web Apps ao usá-lo com o SharePoint 2013

  - Desconecte o SharePoint 2013 do Office Web Apps Server

## Antes de configurar o SharePoint 2013 para usar o Servidor do Office Web Apps

Alguns aspéctos que devem ser verificados antes de iniciar:

  - Instalar SharePoint 2013. Consulte [Instalar o SharePoint 2013](https://technet.microsoft.com/pt-br/library/cc303424\(v=office.15\)) para obter uma orientação.

  - Certifique-se de que todos os aplicativos Web do SharePoint 2013 usam autenticação baseada em declarações. O processamento e a edição do Office Web Apps não funcionarão nos aplicativos Web do SharePoint 2013 que usam a autenticação no modo clássico. Saiba mais em [Requisitos de autenticação do SharePoint para os Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

  - Para permitir que os usuários editem (e não apenas leiam) documentos do Office em um navegador da Web, será necessário uma licença de edição. Também será necessário habilitar a edição no farm do Servidor do Office Web Apps É poddível saber mais sobre os requisitos de licenciamento em [Licenciamento de Office Web Apps para edição de arquivos do Office](plan-office-web-apps-used-with-sharepoint-2013.md).

  - Se entrar no SharePoint 2013 usando a Conta do sistema, não será possível testar a conexão entre o SharePoint 2013 e o Servidor do Office Web Apps. Entre com uma conta diferente para testar a conexão.

  - Condições de memória insuficiente podem fazer com que visualizações de documentos do Office falhem no Office Web Apps. Examine o artigo, [Requisitos de hardware - servidores Web, servidores de aplicativos e instalações de servidor único](https://technet.microsoft.com/pt-br/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver) para o SharePoint 2013, que são os mesmos requisitos que o Servidor do Office Web Apps usa.

## Configurar o SharePoint 2013 para usar o Office Web Apps Server

Escolha uma das seguintes seções, dependendo se você quer usar HTTP ou HTTPS. HTTP geralmente é recomendado apenas para ambientes de teste. Em ambientes de produção, o protocolo HTTPS, mais seguro é a melhor opção.

## Em um ambiente de teste que usa HTTP

Para esta configuração, certifique-se de definir o Servidor do Office Web Apps seguindo as etapas em [Implantar um farm de servidor único do Office Web Apps Server em um ambiente de teste](deploy-office-web-apps-server.md). Configure a farm do Servidor do Office Web Apps para usar uma URL e um HTTP internos. O [VÍdeo: Configurar o Office Web Apps para o SharePoint 2013](video-configure-office-web-apps-for-sharepoint-2013.md) mostra como configurar o Servidor do Office Web Apps e o SharePoint 2013 para usar o Servidor do Office Web Apps em um ambiente de teste.

## Etapa 1: Abrir um Shell de Gerenciamento do SharePoint 2013 privilegiado

Escolha o procedimento que corresponde ao seu sistema operacional de servidor.

**No Windows Server 2008 R2**

1.  Clique em **Iniciar** \> **Todos os Programas** \> **Produtos do Microsoft SharePoint 2013**.

2.  Clique com o botão direito do mouse em **Shell de Gerenciamento do SharePoint 2013**, e clique em **Executar como administrador**.

**No Windows Server 2012**

1.  Pressione a tecla com o logotipo do Windows + Q, ou passe o dedo na borda da tela para exibir os botões e depois clique em **Pesquisa** para ver topdos os aplicativos que estão instalados no computador

2.  Clique com o botão direito do moiuse em**Shell de Gerenciamento do SharePoint 2013** para exibir a barra de aplicativos.

3.  Na barra de aplicativos, clique em **Executar como administrador**.

## Etapa 2: criar a associação entre o SharePoint 2013 e o Office Web Apps Server

Execute o seguinte comando, em que \<WacServerName\> é o nome de domínio totalmente qualificado (FQDN) da URL definida para a URL interna. Este é o ponto de entrada de tráfego do Servidor do Office Web Apps. Para este ambiente de teste, é preciso especificar o parâmetro –AllowHTTP para permitir que o SharePoint 2013 receba informações descobertas da farm do Servidor do Office Web Apps usando o HTTP. Se não especificar –AllowHTTP, o SharePoint 2013 tentará usar HTTPS para se comunicar com a farm do Servidor do Office Web Apps e este comando não funcionará.

    New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP

Após executar este comando, você deverá ver uma lista de vínculos exibida no prompt de comando do Windows PowerShell.

Precisa de ajuda? Consulte [New-SPWOPIBinding](new-spwopibinding.md).

## Etapa 3: exibir as zonas WOPI para as associações do SharePoint

O Servidor do Office Web Apps usa zonas para determinar qual URL (interna ou externa) e qual protocolo (HTTP ou HTTPS) deve ser usado durante a comunicação com o host, neste caso, o SharePoint 2013. Por padrão, o SharePoint Server 2013 usa a zona **internal-https**. Execute o seguinte comando para ver a zona atual.

    Get-SPWOPIZone

A zona WOPI exibida pore este comando deve ser **internal-http**. Se ela for exibida corretamente, pule para a etapa 5. caso contrário, veja a próxima etapa.

Precisa de ajuda? Consulte [Get-SPWOPIZone](get-spwopizone.md).

## Etapa 4: alterar a zona WOPI para internal-http

Se o resultado da Etapa 3 for **internal-https**, execute o seguinte comando para alterar a zona para **internal-http**. É preciso fazer esta alteração porque a zona do SharePoint 2013 deve corresponder à zona da farm do Servidor do Office Web Apps.

    Set-SPWOPIZone -zone "internal-http"

Verifique se a nova zona é **internal-http** executando o **Get-SPWOPIZone** novamente.

Precisa de ajuda? Consulte [Set-SPWOPIZone](set-spwopizone.md) e [Get-SPWOPIZone](get-spwopizone.md).

## Etapa 5: alterar a configuração AllowOAuthOverHttp no SharePoint 2013 para True

Para usar o Office Web Apps com o SharePoint 2013 em HTTP em um ambiente de teste, é preciso definir AllowOAuthOverHttp como **True** (Verdadeiro). Caso contrário, o Office Web Apps não funcionará. Você pode verificar o status atual executando o seguinte exemplo.

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

Se este comando retornar **False**, execute os seguintes comandos para defini-lo como **True**.

```
    $config = (Get-SPSecurityTokenServiceConfig)
```
```
    $config.AllowOAuthOverHttp = $true
```
```
    $config.Update()
```

Execute o comando a seguir novamente para verificar se a configuraçãoAllowOAuthOverHttp está agora definida como **True**.

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

Precisa de ajuda? Consulte [Get-SPSecurityTokenServiceConfig](https://technet.microsoft.com/pt-br/library/ff607642\(v=office.15\)).

## Etapa 6: verificar se o Office Web Apps está funcionando

No SharePoint 2013, certifique-se de não estar conectado como Conta do Sistema. pois você não será capaz de editar ou visualizar documentos com o Office Web Apps. Vá para uma biblioteca de documentos do SharePoint 2013 que contebha documentos do Office e visualize um arquivo do Word, doPowerPoint, Excel, ou do OneNote. O documento deve abrir em um navegador que exibe o arquivo utilizando oOffice Web Apps.

Se este etapa falhar, consulte Solução de erros no Office Web Apps.

## Em um ambiente de produção que usa HTTPS

Antes de iniciar os seguintes procedimentos, verifique se você configurou o Servidor do Office Web Apps seguindo as etapas em [Implantar um farm do Servidores do Office Web Apps em um único servidor que usa HTTPS](e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5\(office.15\)#singlehttps) ou [Implantar um farm de Servidores do Office Web Apps com balanceamento de carga e vários servidores que usa HTTPS](e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5\(office.15\)#multihttps).

## Etapa 1: abra o Shell de Gerenciamento do SharePoint 2013

Escolha o procedimento que corresponde ao seu sistema operacional de servidor.

**No Windows Server 2008 R2**

1.  Selecione **Iniciar** \> **Todos os Programas** \> **Produtos do Microsoft SharePoint 2013** .

2.  Clique com o botão direito do mouse em**SharePoint 2013 Management Shell** para exibir o menu de atalho, e clique em **Executar como administrador**.

**No Windows Server 2012**

1.  Pressione a tecla com o logotipo do Windows + Q, ou passe o dedo na borda da tela para exibir os botões e depois clique em **Pesquisa** para ver topdos os aplicativos que estão instalados no computador.

2.  Clique com o botão direito do mouse em **SharePoint 2013 Management Shell** para exibir a barra de aplicativos.

3.  Na barra de aplicativos, clique em **Executar como administrador**.

## Etapa 2: criar a associação entre o SharePoint 2013 e Office Web Apps Server

Execute o comando a seguir, em que \<WacServerName\> é o nome de domínio totalmente qualificado (FQDN) da URL que você definiu para a URL interna. Esse é o ponto de entrada para o tráfego do Servidor do Office Web Apps.

    New-SPWOPIBinding -ServerName <WacServerName> 

Precisa de ajuda? Consulte [New-SPWOPIBinding](new-spwopibinding.md).

## Etapa 3: ver a zona WOPI do SharePoint 2013

O Servidor do Office Web Apps usa o conceito de zonas para determinar qual URL (interna ou externa) e qual o protocolo (HTTP ou HTTPS) usar ao se comunicar com o host, que nesse caso é SharePoint 2013. Por padrão, o SharePoint Server 2013 usa a zona **https interno**. Verifique se esta é a zona atual, a executar o seguinte comando:

    Get-SPWOPIZone

Anote a zona do WOPI exibida.

Precisa de ajuda? Consulte [Get-SPWOPIZone](get-spwopizone.md).

## Etapa 4: Alterar a zona WOPI, se necessário

Dependendo do seu ambiente, pode ser necessário alterar a zona WOPI. Se houver uma farm interna e externa do SharePoint, especifique externa. Se houver uma farm somente interno do SharePoint, especifique interna.

Se os resultados da Etapa 3 mostrarem **https interno** e o farm do SharePoint for apenas interno, você poderá pular esta etapa. Se tiver um farm do SharePoint que é interno e externo, você deverá executar o seguinte comando para alterar a zona para **https externo**.

    Set-SPWOPIZone -zone "external-https"

Precisa de ajuda? Consulte [Set-SPWOPIZone](set-spwopizone.md).

## Etapa 5: verificar se o Office Web Apps está funcionando

No SharePoint 2013, certifique-se de não estar conectado como Conta do Sistema. pois você não será capaz de editar ou visualizar documentos com o Office Web Apps. Vá para uma biblioteca de documentos do SharePoint 2013 que contebha documentos do Office e visualize um arquivo do Word, doPowerPoint, Excel, ou do OneNote. O documento deve abrir em um navegador que exibe o arquivo utilizando oOffice Web Apps.

Se este etapa falhar, consulte Solução de erros no Office Web Apps.

## Solucionar erros no Office Web Apps quando ele é usado com o SharePoint 2013

Se o Office Web Apps não estiver funcionando corretamente quando usado em conjunto com o SharePoint 2013, localize o sintoma abaixo e expanda o título para encontrar etapas de solução de problemas.

## Problema: quando você selecionar o link "novo documento" em uma biblioteca do SharePoint, você será solicitado a carregar um documento, em vez de ter a opção de criar um novo documento do Office. Escolher (através de clique único) um documento do Office abre o arquivo no aplicativo cliente. Visualizações de documentos do Office não são exbidas.

Aqui estão algumas opções de solução de problemas para tentar.

**Verifique se a autenticação baseada em declarações é usada pelo aplicativo Web do SharePoint que é usado para criar o novo documento**

Somente aplicativos Web que usam a autenticação baseada em declarações podem abrir arquivos no Office Web Apps. Para determinar o provedor de autenticação para um aplicativo Web, siga estes etapas:

1.  No Administração Central do SharePoint 2013, clique em **Gerenciar aplicativos Web**.

2.  Selecione o aplicativo Web que deseja verificar e clique em **Provedores de Autenticação** na faixa de opções.

O provedor de autenticação deve ser apresentado como **Autenticação Baseada em Declarações** para o Office Web Apps funcionar corretamente com o aplicativo Web. Para resolver esse problema, é possível excluir o aplicativo Web e recriá-lo usando a autenticação baseada em declarações ou pode alterar o método de autenticação do aplicativo Web. Você pode encontrar mais informações em [Requisitos de autenticação do SharePoint para o Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

**Certifique-se de que as zonas WOPI são correspondentes no SharePoint 2013 e no farm de Servidores do Office Web Apps.**

Para fazer isso, execute o seguinte comando no SharePoint Server:

    Get-SPWopiZone 

O resultado será um dos seguintes:.

  - internal-https

  - internal-http

  - external-https

  - external-http

Em seguida, execute o seguinte comando no SharePoint Server.

    Get-SPWOPIBinding

Na saída, procure **WopiZone: *zona***. Se os resultados do Get-SPWopiZone não corresponderem à zona retornada pelo Get-SPWOPIBinding, execute o cmdlet **Set-SPWOPIZone -Zone** no SharePoint Server para alterar a zona WOPI para corresponder ao resultado de Get-SPWOPIBinding. Para obter ajuda sobre o uso desses cmdlets, consulte [Get-SPWOPIBinding](get-spwopibinding.md), [Set-SPWOPIBinding](set-spwopibinding.md) e [Get-SPWOPIZone](get-spwopizone.md).

## Problema: Você recebe uma mensagem de erro “Lamento, este documento não pode ser aberto para edição” ao tentar editar um documento do Office nos Office Web Apps.

Em algumas situações, os usuários que são membros dos Grupos de Segurança do Active Directory (AD) podem ser incapazes de editar documentos no navegador. A solução é garantir que o Aplicativo de Serviço de Perfil de Usuário (UPA) está devidamente configurado e totalmente sincronizado com o usuário e associações de grupo. Para obter mais informações, consulte o artigo KB[SharePoint 2013 não é capaz de editar arquivos do Office Web Apps 2013 com usuários que são membros de grupos de segurança](http://support.microsoft.com/kb/2908321?ln=pt-br).

## Problema: você recebe uma mensagem de erro "algo deu errado" quando tenta visualizar um documento do Office no Office Web Apps.

Certifique-se de não eestar conectado como Conta do Sistema, pois você não será capaz de editar ou visualizar um documento. Faça logon como um usuário diferente e tente acessar o Office Web Apps novamente.

## Problema: você recebe uma mensagem de erro "houve um problema e não podemos abrir este documento" quando tenta visualizar um documento do Office no Office Web Apps.

Se você configurar o Office Web Apps em um ambiente de teste que usa HTTP, certifique-se de definir a configuração AllowOAuthOverHttp como **True** (Verdadeiro), conforme descrito em Etapa 5: Alterar a configuração AllowOAuthOverHttp no SharePoint 2013 para True.

Se você adicionou domínios à lista de permissões usando o cmdlet [New-OfficeWebAppsHost](new-officewebappshost.md), certifique-se de que você está acessando o Office Web Apps de um domínio do host que está na Lista de Permissões. Para visualizar os domínios de host na Lista de Permissões, no Servidor do Office Web Apps abra o prompt do Windows PowerShell como administrador e execute o cmdlet [Get-OfficeWebAppsHost](get-officewebappshost.md). Para adicionar um domínio à Lista de Permissões, use o cmdlet [New-OfficeWebAppsHost](new-officewebappshost.md).

## Problema: você recebe uma mensagem de erro "o Word Web App não pode abrir este documento, pois o serviço está ocupado. Tente novamente mais tarde" quando você tenta visualizar um documento do Office no Office Web Apps.

  - Você instalou o Servidor do Office Web Apps em um controlador de domínio? Infelizmente, o Servidor do Office Web Apps não pode ser executado em um controlador de domínio. O Servidor do Office Web Apps deve ser instalado em um servidor separado que faz parte de um domínio. Para obter mais informações, consulte [Requisitos de software, hardware e configuração para o Office Web Apps Server](plan-office-web-apps-server.md).

  - Certifique-se de que você está executando a compilação 15.0.4420.1017 do SharePoint 2013 ou posterior. No servidor do SharePoint 2013, siga essas etapas para verificar o número da compilação:
    
    1.  Vá para **Iniciar** \> **Todos os Programas** \> **Produtos do Microsoft SharePoint 2013** \> **Administração Central do SharePoint 2013**.
    
    2.  Escolha **Configurações do Sistema** \> **Gerenciar os servidores neste farm**.
    
    Verifique se a **Versão do banco de dados de configuração** é **15.0.4420.1017** ou superior. Caso não seja, vá para a [Central de atualizações para o Office, servidores do Office, e produtos relacionados](http://go.microsoft.com/fwlink/p/?linkid=160585) para obter mais informações.

## Problema: você recebe uma mensagem de erro "Arquivo não encontrado. A URL do arquivo original não é válida ou o documento não é acessível publicamente. Verifique se a URL está correta e entre em contato com o proprietário do documento" quando tenta visualizar um documento do Office no Office Apps da Web usando uma URL gerada pelo usuário.

Você está tentando abrir um documento maior do que 10 megabytes por meio de uma URL gerada pelo usuário? Certifique-se de que o documento não excede 10 megabytes.

## Problema: visualizações de documentos do Office não aparecem no SharePoint 2013. Em vez disso, elas mostram a mensagem de erro "Este conteúdo não pode ser exibido em um quadro."

Memória insuficiente pode ocasionar problemas referentes à visualização de documentos do Office. Conheça [Requisitos de hardware-servidores Web, servidores de aplicativos e instalações de servidor único](https://technet.microsoft.com/pt-br/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver) para conhecer os requisitos de memória para o SharePoint 2013. São os mesmos requisitos utilizados pelo Servidor do Office Web Apps.

## Problema: Você recebe a mensagem ““Uma conexão de dados é definida para sempre usar o arquivo de conexão e {0: excelWebApp} não oferece suporte a arquivos de conexão externa. Falha ao atualizar as seguintes conexões: Conexões de dados” erro.

Isso acontece porque o Servidor do Office Web Apps não dá suporte à conexão de dados do arquivo ODC (Conexão de Dados) do Office que armazena as informações de conexão de dados. Para corrigir esse problema, siga estes etapas:

1.  Abra a pasta de trabalho em um aplicativo cliente do Excel.

2.  Clique em **Dados** \> **Conexões**.

3.  Selecione as conexões de dados listadas na mensagem, e clique em **Propriedades**.

4.  Clique na guia **Definição**.

5.  Desmarque a caixa de seleção **Sempre usar caixa de seleção para arquivo de conexão**.

6.  Reenvie a pasta de trabalho para a biblioteca de documentos do SharePoint.

Para que as pessoas possam interagir com pastas de trabalho que contêm um modelo de dados ou modos de exibição do Power View em uma janela do navegador, configure o SharePoint Server para exibir pastas de trabalho. Isso requer que um administrador do SharePoint execute o cmdlet New-SPWOPISupressionSetting no servidor onde o SharePoint Server. Para obter mais informações, consulte [New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md) e [Administrar o Excel Services no SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/ee681487\(v=office.15\)).

## Desconecte o SharePoint 2013 do Office Web Apps Server

Se, por qualquer motivo, você deseja desconectar o SharePoint 2013 de Servidor do Office Web Apps, use o seguinte exemplo de comando.

    Remove-SPWOPIBinding -All:$true

Precisa de ajuda? Consulte [Remove-SPWOPIBinding](remove-spwopibinding.md).

## Consulte também


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIZone](set-spwopizone.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar o Servidor do Office Web Apps](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

