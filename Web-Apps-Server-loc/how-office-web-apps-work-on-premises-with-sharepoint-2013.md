---
title: Como o Office Web Apps funciona no local com o SharePoint 2013
TOCTitle: Office Web Apps local com o SharePoint 2013
ms:assetid: 8480064e-14a4-4b46-ad6b-0c836b192af2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Ff431685(v=office.15)
ms:contentKeyID: 49647112
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Como o Office Web Apps funciona no local com o SharePoint 2013

 

_**Aplica-se a:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2016-12-16_

**Resumo:** Fornece informações sobre o Office Web Apps, Office Web Apps Server e como eles funcionam no local com o SharePoint 2013.

**Audiência:** profissionais de TI

Quando usado junto com o SharePoint Server 2013, oServidor do Office Web Apps fornece versões atualizadas do Word Web App,do Excel Web App, do PowerPoint Web App, e do OneNote Web App. Os usuários podem visualizar e, em alguns casos, editar documentos do Office nas bibliotecas do SharePoint usando um navegador da web com suporte para computadores e diversos dispositivos móveis, como Windows Phones, iPhones, iPads, Windows 8 tablets, e dispositivos Android.


**Figura: Os recursos de visualização e edição do Office Web Apps em diferentes tipos de dispositivos.**

![Um gráfico que resume as capacidades de exibição e edição do Office Web Apps em diferentes tipos de dispositivo. Ele destaca os que são otimizados para telas sensíveis ao toque.](images/JJ219437.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "Um gráfico que resume as capacidades de exibição e edição do Office Web Apps em diferentes tipos de dispositivo. Ele destaca os que são otimizados para telas sensíveis ao toque.")

## Servidor do Office Web Apps agora está instalado como um servidor autônomo

O Office Web Apps não é instalado nos mesmos servidores que executam o SharePoint 2013. Em vez disso, você implanta um ou mais servidores virtuais ou físicos que executam o Servidor do Office Web Apps. Em seguida, configura o farm do SharePoint 2013 para usar o farm do Servidor do Office Web Apps a fim de fornecer a funcionalidade Office Web Apps aos usuários que criam ou abrem arquivos do Office a partir de bibliotecas do SharePoint. Para obter mais informações, consulte [Visão geral do Servidor do Office Web Apps](office-web-apps-server-overview.md).

## Opções para licenciamento do Office Web Apps quando utilizado com o SharePoint 2013

O licenciamento do Office Web Apps oferece duas opções:

  - **Somente exibição**. Por padrão, o Office Web Apps é apenas exibido. A funcionalidade somente exibição é fornecida gratuitamente.

  - **Edição e exibição**. É necessário comprar uma licença de edição para usar os recursos de edição do Office Web Apps com o SharePoint 2013. Ao criar o farm do Servidor do Office Web Apps a edição é habilitada.

Se sua organização estiver licenciada para o Office 2013 através de um programa de Licenciamento por Volume, é possível habilitar a edição do Office Web Apps para o SharePoint 2013 local. Isso ajuda a garantir que os usuários possuam recursos de edição do Office em casa ou em outras localidades onde clientes do Office possam não estar instalados. Licenças de edição para o Office Web Apps não estão disponíveis para compra separada.

Para obter detalhes precisos sobre sua licença, consulte os Termos de Licença do Software Microsoft exibido ao instalar o Servidor do Office Web Apps.

O SharePoint 2013 oferece novas aplicações de licença que funcionam com o Office Web Apps. Se habilitar o licenciamento do SharePoint e, depois, habilitar a edição do Office Web Apps, somente os usuários que têm as licenças apropriadas poderão realmente editar os arquivos do Office em um navegador. Se nenhuma licença de edição do Office Web Apps for aplicada para os usuários, apenas a exibição é possível.

Para obter mais informações sobre como funciona o licenciamento do SharePoint 2013, consulte [Configurar o licenciamento no SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/jj219627\(v=office.15\)). O parâmetro EditingEnabled que possibilita a edição está descrito em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) e em [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps).

Arquivos enviados pelo Compartilhamento pelo recurso de link no SharePoint 2013 podem ser editados no Office Web Apps mesmo quando nenhuma licença de edição estiver presente e quando a edição estiver desabilitada para o farm do Servidor do Office Web Apps.

## Utilize os Visualizadores Móveis do Office para acessar arquivos nos sites do SharePoint

O Servidor do Office Web Appsfornece Visualizadores Móveis do Office para disponibilizar o Office Web Apps para usuários móveis que acessam sites do SharePoint Server. Por padrão, os Visualizadores Móveis do Office estão habilitados, mas não podem ser desativados pelo administrador do site do SharePoint Server. Os usuários quando habilitados podem navegar pelo site do SharePoint Server usando o navegador em seus dispositivos móveis, tocar no documento que desejam abrir na biblioteca do SharePoint Server e o documento será aberto no navegador móvel. .

Saiba mais sobre como usar dispositivos móveis em [Novidades em dispositivos móveis no SharePoint 2013](https://technet.microsoft.com/pt-br/library/fp161352\(v=office.15\)) and [Overview of mobile devices and SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/fp161351\(v=office.15\)). Para saber mais sobre como usar os Visualizadores Móveis do Office em seu dispositivo móvel, consulte [Usar os Office Web Apps no Android, iPhone ou Windows Phone](http://go.microsoft.com/fwlink/p/?linkid=271045).Se você optar por desativar os Visualizadores Móveis do Office noSharePoint 2013, use o cmdlet [Remove-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps).

## Diferenças entre o Excel Web App e os Serviços do Excel no SharePoint

. O Excel Web App e o Excel Services no SharePoint possuem muito em comum, mas não são a mesma coisa. O Excel Services está disponível apenas no Enterprise edition do SharePoint Server 2013. O Excel Web App está disponível no SharePoint Server 2013 e no SharePoint Foundation 2013. Ambos os aplicativos permitem a visualização de pastas de trabalho na janela de um navegador e ambos permitem a interação e exploração de dados.

Porém, existem determinadas diferenças entre oExcel Web App e o Excel Services no SharePoint. Por exemplo, Excel Services oferece suporte a conexões de dados externos, modelos de dados, e capacidade de interagir com ítens que usam modelos de dados (como relatórios do PivotChart, relatórios do PivotTable e controle da linha do tempo). Excel Services fornece mais funcionalidade de inteligência empresarial do que o Excel Web App, mas Excel Services não possibilita que os usuários criem ou editem pastas de trabalho em uma janela do navegador.

. Para obter detalhes sobre as diferenças entre o Excel Web App e o Excel Services, consulte [Visão geral do Excel Services no SharePoint Server 2013](https://technet.microsoft.com/pt-br/library/ee424405\(v=office.15\)) e [Comparando os Serviços do Excel no SharePoint com o Excel Web App](http://go.microsoft.com/fwlink/p/?linkid=255460).

Se sua organização decidir usar o Excel Services em vez do Excel Web App para exibir pastas de trabalho no navegador, você poderá usar o cmdlet Windows PowerShell **New-SPWOPISuppressionSettings** para desativar o Excel Web App para pastas de trabalho do Excel. Para obter mais informações, consulte [New-SPWOPISuppressionSetting](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps).

## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
  

[](plan-office-web-apps-used-with-sharepoint-2013.md)

