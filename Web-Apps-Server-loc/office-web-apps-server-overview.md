---
title: Visão geral do Servidor do Office Web Apps
TOCTitle: 'Visão geral: Servidor do Office Web Apps'
ms:assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219437(v=office.15)
ms:contentKeyID: 49647103
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# Visão geral do Servidor do Office Web Apps

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2017-05-26_

**Resumo:** saiba mais sobre o Office Web Apps Server e como ele fornece funcionalidades do Office com base em navegador para os hosts com suporte.

**Audiência:** profissionais de TI

Servidor do Office Web Apps é um novo produto de servidor de Office que fornece versões baseadas em navegador do Word, PowerPoint, Excel e OneNote. Um único farm do Office Web Apps Server pode oferecer suporte a usuários que acessam arquivos Office por meio de SharePoint 2013, Lync Server 2013, pastas compartilhadas e sites. O novo modelo de implantação autônoma significa que você pode gerenciar atualizações ao seu farm do Office Web Apps Server independentemente de outros produtos de servidor Office que são implantados em sua organização.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este artigo faz parte do <a href="content-roadmap-for-office-web-apps-server.md">Mapa de conteúdo para o Servidor do Office Web Apps</a>. Use o mapa como um ponto inicial para acessar artigos, downloads e vídeos que ajudam a implantar e gerenciar o Servidor do Office Web Apps.<br />
<strong>Deseja obter ajuda com o Office Web Apps em seu desktop ou dispositivo móvel?</strong> É possível encontrar estas informações pesquisando por &quot;Office Web Apps&quot; no <a href="https://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a>.</td>
</tr>
</tbody>
</table>


Neste artigo:

  - Sobre o Servidor do Office Web Apps

  - Como o SharePoint 2013 usa o Servidor do Office Web Apps para exibição e edição de documentos do Office

  - Como o Lync Server 2013 usa o Servidor do Office Web Apps para exibição de transmissões do PowerPoint

  - Como o Office Web Apps Server permite a exibição de arquivos do Office em pastas compartilhadas e sites usando Visualizadores Online

## Sobre o Office Web Apps Server

Servidor do Office Web Apps é um produto de servidor de Office que fornece arquivo baseado em navegador exibindo e editando serviços para Office arquivos. Servidor do Office Web Apps trabalha com produtos e serviços que suportam WOPI, o protocolo de Interface aberta da plataforma do Web app. Esses produtos, conhecidos como hosts, incluem SharePoint 2013 e Lync Server 2013. Um farm de servidor do Office Web Apps pode fornecer serviços de Office para vários hosts local e você pode dimensionar o farm de um servidor para vários servidores conforme sua organização precisa crescer. Embora Servidor do Office Web Apps requer servidores dedicados que não executem nenhum outro aplicativo do servidor, você pode instalar Servidor do Office Web Apps em instâncias de máquina virtual em vez disso.

É mais fácil de implantar e gerenciar Office Web Apps dentro da sua organização, agora que ele é um produto autônomo. Se você implantar SharePoint 2013, por exemplo, você tem mais otimizar a infra-estrutura do SharePoint para suportar o Office Web Apps, que foi estreitamente integrado com SharePoint Server 2010 em versões anteriores. Você também pode aplicar atualizações para o farm do Office Web Apps Server separadamente e uma frequência diferente que você atualizar do SharePoint ou o Lync Server. Ter um farm autônomo do Office Web Apps Server também significa que os usuários podem exibir ou editar Office arquivos que são armazenados externo SharePoint Server, como as pastas compartilhadas ou em outros sites. Essa funcionalidade é proporcionada por um recurso conhecido como visualizadores Online.

As ilustrações abaixo mostram as diferenças entre o modelo antigo de implantação do Office Web Apps e o novo modelo autônomo de implantação do Office Web Apps.

**Diferenças entre os modelos de implantação do Office Web Apps**

![Mostra a diferença entre o modelo de implantação anterior e o novo modelo de implantação autônomo para o Servidor do Office Web Apps](images/JJ219437.f16dd9d1-c9b7-4c8b-a8de-f1f82c0ee1e2(Office.15).gif "Mostra a diferença entre o modelo de implantação anterior e o novo modelo de implantação autônomo para o Servidor do Office Web Apps")

## Como o SharePoint 2013 usa o Office Web Apps Server para exibição e edição de documentos do Office

Quando usado com o SharePoint Server 2013, o Servidor do Office Web Apps fornece versões atualizadas do Word Web App, do Excel Web App, do PowerPoint Web App e do OneNote Web App. Os usuários podem exibir e, em alguns casos, editar os documentos do Office em bibliotecas do SharePoint usando um navegador web com suporte em computadores e em muitos dispositivos móveis, como Windows Phones, iPhones, iPads e tablets com Windows 8. Entre os diversos recursos novos no Office Web Apps, o suporte para toque e os recursos de edição aprimorados permitem que os usuários de iPads e tablets com Windows 8 desfrutem da edição e da exibição de documentos do Office diretamente em seus dispositivos.

A ilustração a seguir resume os recursos de exibição e edição do Office Web Apps em tipos de dispositivos diferentes.

**Recursos de exibição e edição do Office Web Apps**

![Um gráfico que resume as capacidades de exibição e edição do Office Web Apps em diferentes tipos de dispositivo. Ele destaca os que são otimizados para telas sensíveis ao toque.](images/JJ219437.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "Um gráfico que resume as capacidades de exibição e edição do Office Web Apps em diferentes tipos de dispositivo. Ele destaca os que são otimizados para telas sensíveis ao toque.")

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>A Transmissão do PowerPoint foi removida do SharePoint 2013. Está disponível por meio do OneDrive e do Lync Server 2013.</td>
</tr>
</tbody>
</table>


Para obter mais informações sobre o que há de novo no Office Web Apps, consulte [Como o Office Web Apps funciona no local com o SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md).

## Como o Lync Server 2013 usa o Office Web Apps Server para a exibição de transmissões do PowerPoint

No Lync Server 2010, as apresentações do PowerPoint são exibidas usando uma de duas maneiras. Para usuários que executam o Lync 2010, as apresentações do PowerPoint são exibidas usando o formato do PowerPoint 97-2003 e são exibidas usando uma cópia integrada do visualizador do PowerPoint. Para usuários que executam o Lync Web App, as apresentações do PowerPoint são convertidas em arquivos HTML dinâmicos e, em seguida, exibidas usando uma combinação dos arquivos DHTML personalizados e o Silverlight. Embora fosse eficiente na maioria dos casos, essa abordagem tinha algumas limitações:

  - O PowerPoint Visualizador integrado (que proporcionava uma experiência de exibição mais adequada) está disponível somente na plataforma Windows.

  - Muitos dispositivos móveis (incluindo alguns dos celulares mais populares) não são compatíveis com o Silverlight.
    
    A abordagem com o Visualizador do PowerPoint ou com o DHTML/Silverlight não dão suporte a todos os recursos (incluindo transições de slide e vídeo integrado) encontrados nas edições mais recentes do PowerPoint.

Para ajudar a solucionar esses problemas e para aprimorar a experiência geral de qualquer pessoa que apresente ou exiba apresentações do PowerPoint, o Lync Server 2013 usa o Servidor do Office Web Apps para manipular apresentações do PowerPoint. Entre outras vantagens, essa nova abordagem permite os seguintes recursos:

  - Monitores de alta resolução e suporte mais adequado para recursos do PowerPoint, como animações, transições de slide e vídeo integrado.

  - Dispositivos móveis adicionais podem acessar essas apresentações. Isso porque o Lync Server 2013 usa DHTML padrão e JavaScript para transmitir apresentações do PowerPoint em vez de DHTML personalizado e Silverlight.

  - Os usuários que têm privilégios apropriados podem rolar por uma apresentação do PowerPoint independentemente da própria apresentação. Por exemplo, enquanto Ken Myer está apresentando sua apresentação de slide, Pilar Ackerman pode passar por todos os slides e exibir qualquer um que deseje, sem afetar a apresentação de Ken.

Para obter mais informações sobre como configurar Lync Server 2013 para usar Servidor do Office Web Apps, consulte [Implantando o Office Web Apps Server e o Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902).

## Como o Office Web Apps Server permite que os usuários exibam arquivos do Office em pastas compartilhadas e sites usando os Visualizadores Online

Os Visualizadores Online permitem que os usuários utilizem um navegador da web para exibir arquivos do Excel, do PowerPoint e do Word armazenados em servidores da web ou pastas compartilhadas em uma organização. Os usuários podem exibir de forma conveniente os arquivos do Office em um navegador da web sem precisar abrir um aplicativo separado. Além disso, os Visualizadores Online não exigem que o Office 2013 esteja instalado nos computadores dos usuários. Os Visualizadores Online também geram o código necessário para vincular ou incorporar a URL dentro de uma página da web. É possível usar os Visualizadores Online dentro de sua Intranet ou na Internet.

O Servidor do Office Web Apps fornece uma página no endereço http://*NomedoservidordoOfficeWebApps*/op/generate.aspx que pode ser usada para gerar links para documentos disponíveis publicamente que têm endereços UNC ou URL. Quando um usuário seleciona uma URL gerada, os Visualizadores Online permitem que o Servidor do Office Web Apps obtenha o arquivo de seu local e processe-o usando o Office Web Apps. O usuário pode exibir o arquivo do Word, do Excel ou do PowerPoint em um navegador com recursos do Office intactos. A formatação e o layout em documentos do Word são preservados, os dados em pastas de trabalho do Excel podem ser filtrados e classificados e as animações são reproduzidas em apresentações do PowerPoint. No entanto, observe que os Visualizadores Online permitem que os usuários exibam, mas não editem os arquivos, e os Visualizadores Online não podem abrir arquivos que exigem autenticação.

É possível encontrar mais sobre os Visualizadores Online em [Planning for Online Viewers with Office Web Apps Server](plan-office-web-apps-server.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>A Microsoft hospeda uma versão voltada apenas para Internet de Criar URL em <a href="http://go.microsoft.com/fwlink/?linkid=256548%26clcid=0x416">Office.com</a>.</td>
</tr>
</tbody>
</table>


## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Planejar-se para o Servidor do Office Web Apps](plan-office-web-apps-server.md)  
[Implantar o Servidor do Office Web Apps](deploy-office-web-apps-server.md)  
  

[https://technet.microsoft.com/pt-br/library/jj219455](deploy-office-web-apps-server.md)

