---
title: Planejar-se para o Servidor do Office Web Apps
TOCTitle: Planejar-se para o Servidor do Office Web Apps
ms:assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219435(v=office.15)
ms:contentKeyID: 49647097
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# Planejar-se para o Servidor do Office Web Apps

 

_<strong>Aplica-se a:</strong>Office Web Apps Server_

_<strong>Tópico modificado em:</strong>2017-10-10_

**Resumo:** descreve os requisitos e os pré-requisitos do Servidor do Office Web Apps, incluindo HTTPS, certificados, virtualização, balanceamento de carga, topologias e segurança.

**Audiência:** profissionais de TI

Servidor do Office Web Apps entrega versões dos aplicativos do Office com base no navegador, em um ambiente local, fornecendo mais flexibilidade e oportunidades de colaboração aos usuários. Este artigo, descreve os requisitos e etapas necessárias para instalar o Servidor do Office Web Apps em sua organização.

É importante planejar cuidadosamente para que todos os hosts, como SharePoint 2013 e Lync Server 2013, podem se comunicar com o Servidor do Office Web Apps. Para obter orientação adicional sobre como configurar os hosts, consulte os seguintes recursos:

  - [Planejar o Office Web Apps (usado com os produtos do SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)

  - [Implantando o Servidor do Office Web Apps e o Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

> [!NOTE]
> Produtos do SharePoint 2010 não pode ser um host para Servidor do Office Web Apps. Servidor do Office Web Apps não é suportado por SharePoint Foundation 2010 ou SharePoint Server 2010. Servidor do Office Web Apps também não é suportado pelo Exchange Server 2013.


Neste artigo:

  - Requisitos de software, hardware e configuração para o Servidor do Office Web Apps

  - Suporte para virtualização do Servidor do Office Web Apps

  - Requisitos de firewall para o Servidor do Office Web Apps

  - Requisitos do balanceador de carga para o Servidor do Office Web Apps

  - Requisitos de DNS para o Servidor do Office Web Apps

  - Planejando pacotes de idiomas para o Servidor do Office Web Apps

  - Planejamento de topologia para o Servidor do Office Web Apps

  - Planejamento de segurança para o Servidor do Office Web Apps

  - Planejamento de Visualizadores Online com o Servidor do Office Web Apps

  - Planejamento de atualizações para o Servidor do Office Web Apps

## Requisitos de software, hardware e configuração para o Servidor do Office Web Apps

É possível instalar o Servidor do Office Web Apps como um farm do Servidor do Office Web Apps de servidor único, ou como um multisservidor, farm do Servidor do Office Web Apps com balanceamento de carga. É possível utilizar servidores físicos ou instâncias de máquina virtual, mas não é possível instalar outros aplicativos do servidor (como SharePoint 2013 ou SQL Server) no mesmo servidor como Servidor do Office Web Apps.

Em ambientes que contêm dados de usuário reais, sempre recomendamos o uso de HTTPS, para o qual você terá de obter um certificado. Se você estiver usando vários servidores em seu farm, será necessário configurar uma solução de balanceamento de carga de hardware ou de software. Você aprenderá sobre esses cenários nas seções a seguir.

## Requisitos de hardware para Servidor do Office Web Apps

O Servidor do Office Web Apps usa os mesmos requisitos mínimos de hardware que o SharePoint Server 2013. É possível encontrar o conjunto completo de requisitos do SharePoint 2013 em [Requisitos de hardware - servidores Web, servidores de aplicativos e instalações de servidor único](https://technet.microsoft.com/pt-br/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver).

## Sistemas operacionais suportados para Servidor do Office Web Apps

É possível executar o Servidor do Office Web Apps nos seguintes sistemas operacionais:

  - A edição de 64 bits do Windows Server 2008 R2 Service Pack 1 (SP1) Standard, Enterprise ou Datacenter com a [atualização para Windows Server 2008 R2 x64 Edition](https://go.microsoft.com/fwlink/p/?linkid=236954) instalado

  - A edição de 64 bits do Windows Server 2012 Standard, Enterprise ou Datacenter

  - A edição de 64 bits do Windows Server 2012 R2. Para usar este sistema operacional, você deve usar o Servidor do Office Web Apps Service Pack 1 (SP1).

## Requisitos de domínio para Servidor do Office Web Apps

Todos os servidores no farm do Servidor do Office Web Apps precisam fazer parte de um domínio. Eles podem estar no mesmo domínio (recomendado) ou em domínios que estejam na mesma floresta. Entretanto, o Servidor do Office Web Apps não funcionará se você tentar instalá-lo em um controlador de domínio.

## Funções de servidor, serviços e outro software necessários para o Servidor do Office Web Apps

Em primeiro lugar, aqui estão alguns exemplos do que você NÃO deve fazer ao implantar o Servidor do Office Web Apps.

  - **Não instale qualquer outro aplicativo de servidor no servidor que esteja executando o Servidor do Office Web Apps**. Isso inclui o Exchange Server, o SharePoint Server, o Lync Server e o SQL Server. Se não houver servidores suficientes, considere a execução do Servidor do Office Web Apps em uma instância de máquina virtual em dos servidores que você tiver.

  - **Não instale quaisquer serviços ou funções que dependam da função Servidor Web (IIS) na porta 80, 443 ou 809**, pois o Servidor do Office Web Apps remove periodicamente os aplicativos Web dessas portas.

  - **Não instale qualquer versão do Office**. Se ele já estiver instalado, será necessário desinstalá-lo antes da instalação do Servidor do Office Web Apps.

  - **Não instale o Servidor do Office Web Apps em um controlador de domínio**. Ele não poderá ser executado em um servidor com Serviços de Domínio Active Directory (AD DS).

Agora para os itens que você PRECISA instalar. Consulte a tabela a seguir, para obter os detalhes.

> [!IMPORTANT]
> Servidor do Office Web Apps só está disponível para download a partir do <a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Volume Licensing Service Center (VLSC)</a>. Para baixar Servidor do Office Web Apps, você deve ter uma licença, sob um contrato de licenciamento por Volume, para Office Professional Plus 2013, Office Standard 2013 ou Office para Mac 2011. O download está localizado nesses produtos Office no portal VLSC.


### Downloads, funções de servidor e recursos necessários para o Servidor do Office Web Apps

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Download, função de servidor, ou recurso</th>
<th>Se você estiver instalando no Windows Server 2008 R2</th>
<th>Se você estiver instalando no Windows Server 2012</th>
<th>Se você estiver instalando no Windows Server 2012 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Download:</strong> Servidor do Office Web Apps</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Download:</strong> Servidor do Office Web Apps SP1</p></td>
<td><p>Recomendado</p></td>
<td><p>Recomendado</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510097">O Office Web Apps Server SP1</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Download:</strong> Versão correta do .NET Framework</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256560">.NET Framework 4.5</a></p></td>
<td><p>O .NET framework 4.5 já está instalado</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510096">.NET Framework 4.5.2</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Download:</strong> atualização do Windows Server 2008 R2 x64 Edition</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=236954">Atualização para Windows Server 2008 R2 x64 Edition</a></p></td>
<td><p>Não aplicável</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="odd">
<td><p><strong>Download:</strong> Windows PowerShell 3.0</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=244693">Windows PowerShell 3.0</a></p></td>
<td><p>Já instalado</p></td>
<td><p>Já instalado</p></td>
</tr>
<tr class="even">
<td><p><strong>Função de servidor:</strong> servidor Web (IIS)</p></td>
<td><p>A lista a seguir descreve os serviços de função mínimos exigidos para a função de servidor <strong>Servidor Web (IIS)</strong>.</p>
<p><strong>Recursos HTTP Comuns</strong></p>
<ul>
<li><p>Conteúdo estático</p></li>
<li><p>Documento padrão</p></li>
</ul>
<p><strong>Desenvolvimento de Aplicativos</strong></p>
<ul>
<li><p>ASP.NET</p></li>
<li><p>Extensibilidade .NET</p></li>
<li><p>Extensões ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p><strong>Segurança</strong></p>
<ul>
<li><p>Autenticação do Windows</p></li>
<li><p>Filtragem de Solicitações</p></li>
</ul>
<p><strong>Ferramentas de gerenciamento</strong></p>
<ul>
<li><p>Console de Gerenciamento do IIS</p></li>
</ul>
<p>As opções a seguir são recomendadas, mas não obrigatórias:</p>
<p><strong>Desempenho</strong></p>
<ul>
<li><p>Compressão de Conteúdo Estático</p></li>
<li><p>Compactação de conteúdo dinâmico</p></li>
</ul></td>
<td><p>Veja a seguir os serviços de função mínimos exigidos para a função do <strong>Servidor Web (IIS)</strong>.</p>
<p><strong>Ferramentas de Gerenciamento</strong></p>
<ul>
<li><p>Console de Gerenciamento do IIS</p></li>
</ul>
<p><strong>Servidor Web</strong></p>
<ul>
<li><p>Recursos HTTP Comuns</p></li>
<li><p>Documento Padrão</p></li>
<li><p>Conteúdo Estático</p></li>
</ul>
<p><strong>Segurança</strong></p>
<ul>
<li><p>Filtragem de Solicitações</p></li>
<li><p>Autenticação do Windows</p></li>
</ul>
<p><strong>Desenvolvimento de Aplicativos</strong></p>
<ul>
<li><p>Extensibilidade do .NET 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>Extensões ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p>Os seguintes serviços são recomendados, mas não obrigatórios:</p>
<p><strong>Desempenho</strong></p>
<ul>
<li><p>Compressão de Conteúdo Estático</p></li>
<li><p>Compactação de conteúdo dinâmico</p></li>
</ul></td>
<td><p>Veja a seguir os serviços de função mínimos exigidos para a função do <strong>Servidor Web (IIS)</strong>.</p>
<p><strong>Ferramentas de Gerenciamento</strong></p>
<ul>
<li><p>Console de Gerenciamento do IIS</p></li>
</ul>
<p><strong>Servidor Web</strong></p>
<ul>
<li><p>Recursos HTTP Comuns</p></li>
<li><p>Documento Padrão</p></li>
<li><p>Conteúdo Estático</p></li>
</ul>
<p><strong>Segurança</strong></p>
<ul>
<li><p>Filtragem de Solicitações</p></li>
<li><p>Autenticação do Windows</p></li>
</ul>
<p><strong>Desenvolvimento de Aplicativos</strong></p>
<ul>
<li><p>Extensibilidade do .NET 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>Extensões ISAPI</p></li>
<li><p>Filtros ISAPI</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p>Os seguintes serviços são recomendados, mas não obrigatórios:</p>
<p><strong>Desempenho</strong></p>
<ul>
<li><p>Compressão de Conteúdo Estático</p></li>
<li><p>Compressão de Conteúdo Dinâmico</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Recurso:</strong> serviços de tinta e manuscrito</p></td>
<td><p><strong>Serviços de Tinta e Manuscrito</strong></p>
<ul>
<li><p>Suporte para entrada à tinta</p></li>
</ul></td>
<td><p><strong>Serviços de Tinta e Manuscrito</strong></p>
<ul>
<li><p>Não é necessário suporte para entrada de tinta.</p></li>
</ul></td>
<td><p><strong>Serviços de Reconhecimento de Manuscrito</strong></p>
<ul>
<li><p>Não é necessário suporte para entrada à tinta.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Suporte para virtualização do Servidor do Office Web Apps

O Servidor do Office Web Apps tem suporte total quando você o implanta usando a tecnologia Windows ServerHyper-V. Se você planeja virtualizar o Servidor do Office Web Apps, siga estas diretrizes:

  - Instale o Servidor do Office Web Apps em sua própria instância de máquina virtual. Não instale quaisquer outros aplicativos de servidor, como o SharePoint 2013, nessa instância.

  - É possível instalar o Servidor do Office Web Apps em uma instância de máquina virtual hospedada por um servidor que executa o SharePoint 2013.

  - Para farms do Servidor do Office Web Apps com vários servidores, cada instância deve estar em uma máquina virtual separada. Dessa forma, o farm do Servidor do Office Web Apps ainda estará disponível se um dos hosts falhar.

## Requisitos de firewall para o Servidor do Office Web Apps

Os firewalls podem causar problemas ao bloquearem a comunicação entre o navegador da Web, os servidores que executam o Servidor do Office Web Apps e os servidores que executam o SharePoint 2013. Esses problemas poderão ser mais complicados quando os servidores estiverem em partes diferentes de uma rede.

Verifique se as portas a seguir não estão bloqueadas por firewalls no servidor que executa o Servidor do Office Web Apps ou no balanceador de carga:

  - Porta 443 para tráfego HTTPS

  - Porta 80 para tráfego HTTP

  - Porta 809 para tráfego provado entre os servidores que executam o Servidor do Office Web Apps (se você estiver configurando um farm com múltiplos servidores)

## Requisitos do balanceador de carga para o Servidor do Office Web Apps

Recomendamos uma solução de balanceamento de carga quando você executar o Servidor do Office Web Apps em dois ou mais servidores. Quase todas as soluções de balanceamento de carga funcionarão, incluindo um servidor que execute a função Servidor Web (IIS) executando o ARR (Application Request Routing). Na verdade, é possível executar o ARR em um dos servidores que executa o Servidor do Office Web Apps. Se você não tiver uma solução de balanceamento de carga, veja alguns recursos para o uso do IIS com ARR:

  - [Roteamento de solicitação de aplicativo de instalação](https://go.microsoft.com/fwlink/?linkid=236955)

  - [Ajuda do roteamento de solicitação de aplicativo](https://go.microsoft.com/fwlink/?linkid=236956)

O ideal é que você tente encontrar uma solução de balanceamento de carga que dê suporte aos seguintes recursos:

  - Roteamento de Camada 7

  - Habilitação da afinidade do cliente ou afinidade de front-end

  - Habilitação de descarregamento SSL

Se você usar um balanceador de carga, deverá instalar o certificado no balanceador de carga como descrito em Protegendo as comunicações do Servidor do Office Web Apps usando HTTPS.

## Requisitos de DNS para o Servidor do Office Web Apps

Em ambientes que usam HTTPS e balanceamento de carga, é necessário atualizar o DNS de modo que o FQDN do certificado seja resolvido para o endereço IP do servidor que executa o Servidor do Office Web Apps ou para o endereço IP atribuído ao balanceador de carga do farm do Servidor do Office Web Apps.

## Planejando pacotes de idiomas para o Servidor do Office Web Apps

Os Pacotes de Idioma do Servidor do Office Web Apps 2013 permitem que os usuários exibam arquivos do Office baseados na web em vários idiomas a partir de bibliotecas de documento do SharePoint 2013, do Aplicativo Web do Outlook (como visualizações de anexo) e do Lync 2013 (como difusões do PowerPoint). No entanto, isso depende dos idiomas configurados no host. Para exibir arquivos do Office baseados na Web a partir de hosts em vários idiomas, o seguinte precisa ser verdade:

  - O host (por exemplo, SharePoint Server 2013 ou Lync Server 2013 ) está configurado para executar aplicativos em idiomas adicionais. O processo de instalação e configuração de pacotes de idiomas no host é independente da instalação de um pacote de idiomas no farm Servidor do Office Web Apps.

  - Os idiomas são instalados e estão disponíveis em todos os servidores no farm do Servidor do Office Web Apps.

Aqui é onde [baixar os pacotes de idioma para o Office Web Apps Server](https://go.microsoft.com/fwlink/p/?linkid=263945).

## Planejamento de topologia para o Servidor do Office Web Apps

No mínimo, uma topologia de Servidor do Office Web Apps incluirá um física ou máquina virtual que executa o Servidor do Office Web Apps e pelo menos um host (por exemplo, um servidor executando o Lync Server 2013 ou SharePoint 2013 ). E, obviamente, será necessário um PC cliente ou dispositivo me conectar a um dos hosts e usar a funcionalidade de Office Web Apps. Da topologia desse mínima, você pode adicionar mais hosts e mais servidores ao farm Servidor do Office Web Apps conforme necessário para se adequar às necessidades da sua organização.

A seguir está uma lista de recomendações que você deve ter em mente, como sua topologia de Servidor do Office Web Apps fica mais complexa.

  - **Plano para redundância.** Se você utilizar instâncias de máquina virtual, certifique-se de colocá-las em hosts de máquinas virtuais separados para redundância. Não há problema se outras instâncias no host executarem aplicativos de servidor—simplesmente não execute outros aplicativos de servidor na mesma instância, como Servidor do Office Web Apps.

  - **Dê preferência a apenas um centro de dados.** Os servidores em um farm do Servidor do Office Web Apps devem estar no mesmo data center. Não distribua-os geograficamente. Geralmente você precisa apenas de um farm, a menos que você tenha necessidades de segurança que exijam uma rede isolada, que possui seu próprio farm do Servidor do Office Web Apps.

  - **Quanto mais próximos os hosts, melhor.** O farm do Servidor do Office Web Apps não precisar estar no mesmo data center como os hosts que ele atende, no entanto para uso de edições carregadas, recomendamos que você coloque o farm do Servidor do Office Web Apps o mais próximo possível dos hosts. Isso tem menos importância para as organizações que utilizam o Office Web Apps basicamente para visualizar arquivos do Office.

  - **Planeje suas conexões.** Conecte todos os servidores no farm do Servidor do Office Web Apps apenas uns aos outros. Para conectá-los a uma rede mais ampla, faça isso usando um firewall do balanceador de carga de proxy reverso.

  - **Configure o firewall para os requisitos de HTTP ou HTTPS.** Certifique-se de que o firewall permite que os servidores executem o Servidor do Office Web Apps para iniciar os requisitos de HTTP ou HTTPS para hosts.

  - **Plano para comunicações de entrada e de saída.** Em uma implantação voltada para a Internet, encaminhe todas as comunicações de saída por meio de um dispositivo NAT. Em um farm com múltiplos servidores, trate de todas as comunicações de entrada usando um balanceador de carga.

  - **Certifique-se de que todos os servidores do farm do Servidor do Office Web Apps se unam a um domínio e que façam parte da mesma unidade de organização (OU).** Use o parâmetro **FarmOU** no cmdlet [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) para impedir que outros servidores que não estejam nessa UO ingressem no farm.

  - **A topologia usa HTTPS (Hypertext Transfer Protocol Secure) para todas as solicitações de entrada.**

  - **Se você tiver um IPsec implantado na rede, utilize-o para criptografar o tráfego entre os servidores.**

  - **Planeje os recursos do Office que usam a Internet.** Se recursos como clip-art e serviços de tradução forem necessários e se os servidores no farm não puderem iniciar solicitações para a Internet, um servidor proxy precisa ser configurado para o farm do Servidor do Office Web Apps. Isso permitirá solicitações HTTP para sites externos.

## Planejamento de segurança para o Servidor do Office Web Apps

As informações a seguir apresentam orientação de segurança para Servidor do Office Web Apps.

## Protegendo as comunicações do Servidor do Office Web Apps usando HTTPS

Servidor do Office Web Apps podem se comunicar com SharePoint 2013 e Lync Server 2013 usando o protocolo HTTPS. Em ambientes de produção, é altamente recomendável que você use HTTPS. Você precisará instalar um certificado de servidor de Internet que pode ser atribuído ao servidor que executa o Servidor do Office Web Apps (se você estiver usando um único servidor) ou para o balanceador de carga (se você estiver usando vários servidores que executam o Servidor do Office Web Apps ).

Em ambientes de teste que não contêm nenhum dado de usuário, você pode usar HTTP para SharePoint 2013 e ignorar o requisito de certificado. Lync Server 2013 suporta apenas o HTTPS.

Os certificado usados pelo Servidor do Office Web Apps precisam atender aos seguintes requisitos:

  - O certificado precisa vir de uma Autoridade de Certificação e incluir o nome de domínio totalmente qualificado (FQDN) de seu farm do Servidor do Office Web Apps no campo SAN (Nome alternativo da entidade). (Se o FQDN não estiver no SAN, quando você tentar usar o certificado, o navegador mostrará avisos de segurança ou não processará a resposta).

  - O certificado precisa ter uma chave privada exportável. Em farms de um único servidor, essa opção é selecionada por padrão quando você usa o snap-in Serviços de Informações da Internet (IIS) Manager para importar o certificado.

  - O campo Nome amigável precisa ser exclusivo dentro do repositório Autoridades de Certificação de raiz confiáveis. Se você tiver múltiplos certificados que compartilham um campo Nome Amigável, a criação do farm falhará pois os cmdlets New-OfficeWebAppsFarm não saberão qual desses certificados usar.

  - O Servidor do Office Web Apps não exige uma propriedade ou extensão especifica de certificado. Por exemplo, as extensões do EKU (Client Enhanced Key Usage) ou as extensões do Server EKU não são necessárias.

  - No Windows Server 2012 ou Windows Server 2012 R2, você deve instalar o recurso do Windows Communication Foundation (WCF) "Permitir ativação de HTTP".

O certificado deve ser importado da seguinte maneira:

  - **Para farms com um único servidor** É necessário importar o certificado diretamente no servidor que executa o Servidor do Office Web Apps. Não vincule o certificado manualmente. O cmdlet New-OfficeWebAppsFarm que você executará posteriormente fará isso para você. Se você vincular o certificado manualmente, ele será excluído sempre que o servidor reiniciar.

  - **Para farms com balanceamento de carga**   Se você estiver descarregando o SSL, o certificado deverá ser importado no balanceador de carga de hardware. Se você não estiver descarregando o SSL, será necessário instalar o certificado em cada servidor no farm do Servidor do Office Web Apps.

> [!NOTE]
> Não use certificados autoassinados, exceto em ambientes de teste não críticos.


Para obter mais informações sobre certificados, consulte [como obter um certificado SSL](https://go.microsoft.com/fwlink/p/?linkid=269700).

## Usando o descarregamento de SSL para balanceadores de carga de hardware

Por padrão, quando você configura um novo farm do Servidor do Office Web Apps, o descarregamento de SSL é definido como desativado. Se você estiver usando um balanceador de carga de hardware, recomendamos a definição do descarregamento de SSL como ativado, de forma que cada Servidor do Office Web Apps no farm possa se comunicar como balanceador de carga usando HTTP. A definição do descarregamento de SSL como ativado também oferece as seguintes vantagens:

  - Gerenciamento simplificado de certificados

  - Afinidade de software aprimorada

  - Desempenho aprimorado

Observe que quando você usa HTTP, o tráfego do balanceador de carga para os servidores que executam o Servidor do Office Web Apps não é criptografado; portanto, você precisa se certificar de que a própria rede seja segura. O uso de uma sub-rede privada pode ajudar a proteger o tráfego.

## Restringir quais servidores podem ingressar em um farm do Servidor do Office Web Apps com base na associação da UO

É possível impedir que servidores não autorizados ingressem em um farm do Servidor do Office Web Apps criando uma unidade organizacional para esses servidores e especificando o parâmetro FarmOU ao criando o farm. Para obter mais informações sobre o parâmetro FarmOU, consulte [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

## Limitar o acesso do host para Servidor do Office Web Apps usando a Lista de Permissões

A Lista de Permissões é um recurso de segurança que impede hosts indesejados de se conectar a um farm do Servidor do Office Web Apps e de usá-lo para operações de arquivo sem seu consentimento. Ao adicionar os domínios que contêm os hosts aprovados à Lista de Permissões, é possível limitar os hosts aos quais o Servidor do Office Web Apps permite solicitações de operações de arquivo, como recuperação de arquivo, recuperação de metadados e alterações de arquivo.

É possível adicionar domínios à Lista de Permissões após a criação do farm do Servidor do Office Web Apps. Para saber como adicionar domínios à Lista de Permissões, consulte [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps).

> [!IMPORTANT]
> Se você não adicionar domínios à Lista de Permissões, o Servidor do Office Web Apps permitirá solicitações de arquivo aos hosts em qualquer domínio. Não deixe essa lista em branco se seu farm do Servidor do Office Web Apps puder ser acessado da Internet. Caso contrário, qualquer pessoa poderá usar seu farm do Servidor do Office Web Apps para exibir e editar o conteúdo.


## Planejando os Visualizadores Online com o Servidor do Office Web Apps

Por padrão, a funcionalidade de Visualizadores Online é habilitada após a instalação do Servidor do Office Web Apps. Revise as seguintes diretrizes se estiver planejando usar os Visualizadores Online em sua organização. Em alguns casos, convém desabilitar alguns recursos dentro dos Visualizadores Online. Essas diretrizes se referem aos parâmetros definidos usando os cmdlets do Windows PowerShell, [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) e [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps).

## Considerações de segurança para os Visualizadores Online

Os arquivos que devem ser exibidos por meio de uma navegador da Web usando os Visualizadores Online não devem exigir autenticação. Em outras palavras, os arquivos precisam estar disponíveis publicamente, pois os Visualizadores Online não conseguem executar a autenticação quando estão recuperando arquivos. Recomendamos que o farm do Servidor do Office Web Apps usado para os Visualizadores Online possa acessar somente a Intranet ou a Internet, mas não ambas. Isso porque o Servidor do Office Web Apps não diferencia entre solicitações para URLs da Intranet e da Internet. Se uma solicitação vier da Internet para uma URL da Intranet, por exemplo, um vazamento de segurança poderá ocorrer se um documento interno for fornecido para alguém na Internet.

Pelo mesmo motivo, se você tiver configurado o Servidor do Office Web Apps para se conectar somente à Internet, recomendamos a desabilitação do suporte a UNC nos Visualizadores Online. Para desabilitar o suporte a UNC, defina o parâmetro OpenFromUncEnabled como False usando os cmdlets do Windows PowerShell, [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (para novos farms) ou [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (para farms existentes).

Como precaução de segurança adicional, os Visualizadores Online estão limitados à exibição de arquivos do Office com 10 MB ou menos.

## Opções de configuração para Visualizadores Online

É possível configurar os Visualizadores Online usando os seguintes parâmetros do Windows PowerShell em [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (para novos farms) ou [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (para farms existentes).

  - **OpenFromUrlEnabled**   Ativa ou desativa os Visualizadores Online. Esse parâmetros controla os Visualizadores Online para arquivos com URL e caminhos UNC. Por padrão, esse parâmetro é definido como False (desabilitado) quando você cria um novo farm do Servidor do Office Web Apps.

  - **OpenFromUncEnabled**   Quando os Visualizadores Online são ativados (definidos como True usando OpenFromUrlEnabled), esse parâmetro ativa ou desativa a capacidade dos Visualizadores Online de exibir arquivos em caminhos UNC. Por padrão, esse parâmetro é definido como True, mas saiba que o OpenFromUrlEnabled também é definido como True antes de você habilitar a abertura de arquivos a partir de caminhos UNC. Conforme descrito anteriormente, recomendamos a definição desse parâmetro como False se você tiver definido o Servidor do Office Web Apps para se conectar à Internet.

  - **OpenFromUrlThrottlingEnabled**   Limita o número de aberturas a partir de solicitações de URL a partir de qualquer servidor em um período. Os valores de limite padrão, que não são configuráveis, garantem que um farm do Servidor do Office Web Apps não sobrecarregue um único servidor enviando solicitações para exibição de conteúdo nos Visualizadores Online.

## Planejamento de atualizações para o Servidor do Office Web Apps

Antes de implantar o Servidor do Office Web Apps, você precisa decidir como sua organização gerenciará as atualizações de software para seu farm do Servidor do Office Web Apps. Embora as atualizações de software ajudem a aprimorar a segurança do servidor, o desempenho e a confiabilidade, a instalação incorreta das atualizações podem causar problemas com o Servidor do Office Web Apps.

A aplicação de atualizações do Servidor do Office Web Apps usando o processo de atualização automática da Microsoft não tem suporte no Servidor do Office Web Apps. Isso ocorre porque as atualizações para um Servidor do Office Web Apps precisam ser aplicadas de uma maneira específica, conforme descrito no [Aplicar atualizações de software ao Servidor do Office Web Apps](apply-software-updates-to-office-web-apps-server.md). Se as atualizações do Servidor do Office Web Apps forem aplicadas automaticamente, os usuários não poderão ver ou editar documentos no Office Web Apps. Se isso ocorrer, será necessário recriar sua farm do Servidor do Office Web Apps.

Recomendamos o gerenciamento das atualizações usando o Windows Server Update Services (WSUS) ou usando o System Center Configuration Manager, que usa o WSUS. O WSUS permite que você gerencie completamente a distribuição de atualizações lançadas pelo Microsoft Update para cada servidor no farm do Servidor do Office Web Apps. Ao usar o WSUS, você pode decidir quais atualizações serão automaticamente aplicadas ao farm do servidor e quais atualizações, como as atualizações do Servidor do Office Web Apps, precisam ser aplicadas manualmente. Para saber mais sobre o WSUS, confira [Windows Server Update Services](https://go.microsoft.com/fwlink/p/?linkid=294822).

Se você não usar o WSUS ou o System Center Configuration Manager, defina as atualizações automáticas da Microsoft em cada servidor no farm do Servidor do Office Web Apps como **Baixar automaticamente, mas notificar o usuário para instalação**. Quando receber uma notificação de uma atualização do Servidor do Office Web Apps, execute as etapas em [Aplicar atualizações de software ao Servidor do Office Web Apps](apply-software-updates-to-office-web-apps-server.md). Para que as atualizações do Windows sejam aplicadas e mantenham seus servidores seguros, aceite as atualizações do Windows quando receber uma notificação de que elas estão disponíveis.

## Consulte também


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Visão geral do Servidor do Office Web Apps](office-web-apps-server-overview.md)  
[Implantar o Servidor do Office Web Apps](deploy-office-web-apps-server.md)  
[Aplicar atualizações de software ao Servidor do Office Web Apps](apply-software-updates-to-office-web-apps-server.md)  


[Office.com (para obter ajuda com o Office Web Apps em seu desktop ou dispositivo móvel)](https://go.microsoft.com/fwlink/p/?linkid=266657)  
  

[https://technet.microsoft.com/pt-br/library/jj966220](apply-software-updates-to-office-web-apps-server.md)

