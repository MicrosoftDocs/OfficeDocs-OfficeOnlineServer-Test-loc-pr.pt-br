---
title: Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)
TOCTitle: Planejar o Office Web Apps
ms:assetid: 3bd0a617-5f12-4a7e-bb75-b15c86c7e504
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ff431682(v=office.15)
ms:contentKeyID: 49647102
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2016-12-16_

**Resumo:** revisar a orientação de planejamento para o Office Web Apps quando usado com o SharePoint 2013 local.

**Audiência:** profissionais de TI

Para planejar como o Office Web Apps é usado com o SharePoint 2013 local, você deve analisar o suporte do navegador, os requisitos de autenticação do SharePoint e considerações de licenciamento para visualizar e editar arquivos do Office usando o Office Web Apps. Então, você poderá decidir se deseja que o SharePoint 2013 use o navegador ou um aplicativo cliente quando o usuário abrir arquivos do Office a partir de uma biblioteca de documentos do SharePoint 2013.

> [!IMPORTANT]
> Este artigo faz parte do <a href="content-roadmap-for-office-web-apps-server.md">Mapa de conteúdo para o Servidor do Office Web Apps</a>. Use o mapa como um ponto de partida para artigos, downloads e vídeos que ajudam você a implantar e gerenciar o Servidor do Office Web Apps.<br />
<strong>Deseja obter ajuda com o Office Web Apps em seu desktop ou dispositivo móvel?</strong> É possível encontrar estas informações pesquisando por &quot;Office Web Apps&quot; no <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.


Neste artigo:

  - Sobre o planejamento para o Office Web Apps

  - Suporte de navegador para Office Web Apps

  - Requisitos de autenticação do SharePoint para o Office Web Apps

  - Licenciando o Office Web Apps para edição de arquivos do Office

  - Considerações para clientes que implantaram o Office Web Apps com o SharePoint 2010

  - Comportamento de abertura padrão para documentos abertos a partir de documentos do SharePoint 2013

## Sobre o planejamento para o Office Web Apps

A orientação neste artigo é um subconjunto do planejamento geral que você realizará ao implantar o Servidor do Office Web Apps localmente em sua organização. Por exemplo, requisitos de hardware, software e virtualização, dimensionamento e topologia de farm, e segurança fazem parte do planejamento do Servidor do Office Web Apps. Depois de tomar essas decisões, você pode planejar como configurar a funcionalidade do Office Web Apps específica ao SharePoint 2013. Se você não tiver ouvido falar do Servidor do Office Web Apps ou revisado seus requisitos e orientação de planejamento, consulte [Visão geral do Servidor do Office Web Apps](office-web-apps-server-overview.md) e [Planejar-se para o Servidor do Office Web Apps](plan-office-web-apps-server.md).

## Suporte de navegador para Office Web Apps

Suporte de navegador para o Office Web Apps é o mesmo que para SharePoint 2013. Consulte o artigo [Plano de suporte do navegador no SharePoint 2013](https://technet.microsoft.com/pt-br/library/cc263526\(v=office.15\)) para obter mais informações.

## Requisitos de autenticação do SharePoint para o Office Web Apps

O Office Web Apps pode ser usado somente por aplicativos da web do SharePoint 2013 que usam autenticação com base em declarações. O processamento e a edição do Office Web Apps não funcionarão em aplicativos da web do SharePoint 2013 que usam a autenticação no modo clássico. Se você migrar os aplicativos da web do SharePoint 2010 que usam a autenticação no modo clássico para SharePoint 2013, será necessário migrá-los para autenticação com base em declarações a fim de permitir que eles funcionem com o Office Web Apps. Para saber mais, consulte [Migrar da autenticação de modo clássico para a autenticação baseada em declarações SharePoint 2013](https://technet.microsoft.com/pt-br/library/gg251985\(v=office.15\)).

## Licenciando o Office Web Apps para edição de arquivos do Office

Clientes corporativos que estiverem licenciados para o Office 2013, através de um programa de Licenciamento por Volume, podem habilitar a edição do Office Web Apps para o SharePoint 2013 local. Isso ajuda a garantir que os usuários possuam recursos de edição do Office em casa ou em outras localidades onde clientes do Office possam não estar instalados. Licenças de edição para o Office Web Apps não estão disponíveis para compra separada.

Para detalhes exatos sobre sua licença, consulte os Termos de Licença do Software Microsoft exibido ao instalar o Servidor do Office Web Apps. Para saber mais sobre como o licenciamento funciona no SharePoint 2013, consulte [Configurar o licenciamento no SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/jj219627\(v=office.15\)).

## Considerações para clientes que usam o método de anexação de banco de dados para atualizar a partir do SharePoint 2010

Se você instalou o Office Web Apps juntamente com o SharePoint 2010, o Office Web Apps não estará disponível depois da atualização para o SharePoint 2013. Você deve implantar o Servidor do Office Web Apps e então conectar o SharePoint 2013 a ele depois que os bancos de dados de conteúdo estiverem atualizados. Não é necessário esperar até que os conjuntos de sites estejam atualizados porque o Servidor do Office Web Apps oferece suporte a ambos, os modos de conjunto de site 2010 e 2013 no SharePoint 2013. Para mais informações sobre o método de anexação de banco de dados, consulte [Visão geral do processo de atualização do SharePoint 2013](https://technet.microsoft.com/pt-br/library/cc262483\(v=office.15\)).

## Comportamento de abertura padrão para documentos abertos a partir de bibliotecas de documentos do SharePoint 2013

É possível configurar se os arquivos do Word, do PowerPoint, do Excel e do OneNote são abertos em um aplicativo cliente (caso esteja instalado) ou no navegador. Por padrão, após a configuração do SharePoint 2013 para usar o Servidor do Office Web Apps, os arquivos do Office são abertos no navegador. Há duas maneiras de alterar o comportamento padrão a fim de permitir que aplicativos clientes abram os arquivos diretamente:

  - **Para o farm do SharePoint 2013** Você pode ajustar o comportamento de abertura padrão por tipo de arquivo para o farm do SharePoint 2013 usando os cmdlets [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) e [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps) do Windows PowerShell.

  - **Em conjuntos de sites ou bibliotecas de documento** Os administradores e usuários de conjunto de site podem especificar se os arquivos do Office são abertos em aplicativos clientes, se estiverem instalados. Os usuários podem alterar essa configuração nas propriedades da biblioteca de documento e os administradores do conjunto de sites podem alterar essa configuração na Administração do Conjunto de Sites ou usando o cmdlet Install-SPFeature para instalar o recurso OpenInClient. Para obter mais informações, consulte [Install-SPFeature](https://technet.microsoft.com/pt-br/library/ff607825\(v=office.15\)).

## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Como o Office Web Apps funciona no local com o SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  


[In a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

