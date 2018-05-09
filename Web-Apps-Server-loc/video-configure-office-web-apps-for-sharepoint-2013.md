---
title: 'VÍdeo: Configurar o Office Web Apps para o SharePoint 2013'
TOCTitle: 'VÍdeo: Configurar o Office Web Apps para o SharePoint 2013'
ms:assetid: 0c02633f-3839-448b-ae83-24f24c254179
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn455088(v=office.15)
ms:contentKeyID: 58487584
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# VÍdeo: Configurar o Office Web Apps para o SharePoint 2013

 

_**Aplica-se a:**Office Web Apps, Office Web Apps Server, SharePoint Foundation 2013, SharePoint Server 2013_

_**Tópico modificado em:**2016-12-16_

**Resumo:** Apresenta as nove etapas principais para configurar um farm do Office Web Apps Server para trabalhar com o SharePoint 2013.

Configurar o Office Web Apps para o SharePoint 2013 é um processo muito simples. Este vídeo ensina como ajustar oServidor do Office Web Apps e configurar o SharePoint 2013 para uso do Servidor do Office Web Apps em um ambiente de teste.


**Assista o vídeo "Configurando o Office Web Apps para o SharePoint 2013" .**

> [!VIDEO https://www.microsoft.com/pt-br/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

Este vídeo abrange os procedimentos realizados em dois servidores: o servidor que executa o Servidor do Office Web Apps, e o servidor que executa o SharePoint 2013. É necessário que sejam servidores distintos, conforme descrito nos [requisitos de software, hardware, e configuração para o Office Web Apps Server](plan-office-web-apps-server.md).

**No sevidor que executa o Servidor do Office Web Apps, o vídeo mostra como:**

1\. Abra o prompt de comando do Windows PowerShell e instale as funções e serviços necessários para o Servidor do Office Web Apps. Consulte [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md). Isso é necessário porque o Servidor do Office Web Apps não será instalado caso estejam faltando as funções e serviços necessários.  
2\. Instale o software do Servidor do Office Web Apps a partir do [Centro de Serviços de Licenciamento por Volume (VLSC)](http://go.microsoft.com/fwlink/p/?linkid=256561). Você deverá ter um contrato de Licenciamento por Volume para baixar o Servidor do Office Web Apps para Office Professional Plus 2013, Office Standard 2013, ou Office para Mac 2011. O download está localizado abaixo dos produtos do Office no portal do VLSC.  
3\. Crie o farm do Servidor do Office Web Apps usando o [New-OfficeWebAppsFarm](new-officewebappsfarm.md).  
4\. Verifique se o farm do Servidor do Office Web Apps foi criado com êxito abrindo uma janela de navegador e acessando http://*ServerName*/hosting/discovery.

**No servidor que executa o SharePoint 2013, o vídeo ensina como:**

5\. Abrir o Shell de Gerenciamento do SharePoint 2013.  
6\. Criar a associação entre o Servidor do Office Web Apps e o SharePoint 2013 utilizando o [New-SPWOPIBinding](new-spwopibinding.md). Isto estabelece uma comunicação entre o servidor que executa o SharePoint 2013 e o servidor que executa o Servidor do Office Web Apps.  
7\. Exibir a zona WOPI do SharePoint 2013 utilizando [Get-SPWOPIZone](get-spwopizone.md). Esta etapa destaca o fato de que dois servidores estão utilizando zonas WOPI diferentes: SharePoint 2013 está usando o https interno, e o Servidor do Office Web Apps está usando o http interno. A zona precisa corresponder ao Office Web Apps para funcionar corretamente.  
8\. Alterar a zona WOPI para o SharePoint 2013 utilizando [Set-SPWOPIZone](set-spwopizone.md) para alterar a zona WOPI para o http interno.  
9\. Verificar se o Office Web Apps está funcionando ao abrir um documento do Office em uma biblioteca de documentos do SharePoint 2013 .

Para obter mais detalhes sobre cada uma dessas etapas, consulte as seções a seguir nos artigos [Implantar o Servidor do Office Web Apps](deploy-office-web-apps-server.md) e [Configurar o Office Web Apps para o SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md).

  - [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md)

  - [Implantar um farm de servidor único do Office Web Apps Server em um ambiente de teste](deploy-office-web-apps-server.md)

  - [Before you configure SharePoint 2013 to use Office Web Apps Server](configure-office-web-apps-for-sharepoint-2013.md)

  - [In a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)

## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
[Como o Office Web Apps funciona no local com o SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

