---
title: New-OfficeWebAppsFarm
TOCTitle: New-OfficeWebAppsFarm
ms:assetid: 3616a668-f76f-45c6-914c-3103cbded5d2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ219436(v=office.15)
ms:contentKeyID: 49647100
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsFarm

 

_**Aplica-se a:**Office Web Apps Server_

_**Tópico modificado em:**2015-03-26_

Cria um novo farm do Servidor do Office Web Apps no computador local.

## Sintaxe

    New-OfficeWebAppsFarm [-AllowCEIP <SwitchParameter>] [-AllowHttp <SwitchParameter>] [-AllowHttpSecureStoreConnections <SwitchParameter>] [-CacheLocation <String>] [-CacheSizeInGB <Nullable>] [-CertificateName <String>] [-ClipartEnabled <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DocumentInfoCacheSize <Nullable>] [-EditingEnabled <SwitchParameter>] [-ExcelAllowExternalData <SwitchParameter>] [-ExcelConnectionLifetime <Nullable>] [-ExcelExternalDataCacheLifetime <Nullable>] [-ExcelPrivateBytesMax <Nullable>] [-ExcelRequestDurationMax <Nullable>] [-ExcelSessionTimeout <Nullable>] [-ExcelWarnOnDataRefresh <SwitchParameter>] [-ExcelWorkbookSizeMax <Nullable>] [-ExternalURL <String>] [-FarmOU <String>] [-Force <SwitchParameter>] [-InternalURL <String>] [-LogLocation <String>] [-LogRetentionInDays <Nullable>] [-LogVerbosity <String>] [-MaxMemoryCacheSizeInMB <Nullable>] [-MaxTranslationCharacterCount <Nullable>] [-OpenFromUncEnabled <SwitchParameter>] [-OpenFromUrlEnabled <SwitchParameter>] [-OpenFromUrlThrottlingEnabled <SwitchParameter>] [-PicturePasteDisabled <SwitchParameter>] [-Proxy <String>] [-RecycleActiveProcessCount <Nullable>] [-RemovePersonalInformationFromLogs <SwitchParameter>] [-RenderingLocalCacheLocation <String>] [-SSLOffloaded <SwitchParameter>] [-TranslationEnabled <SwitchParameter>] [-TranslationServiceAddress <String>] [-TranslationServiceAppId <String>] [-WhatIf [<SwitchParameter>]]

## Descrição detalhada

O cmdlet **New-OfficeWebAppsFarm** cria um novo farm do Servidor do Office Web Apps no computador local. Você executa este cmdlet no primeiro servidor no farm do Servidor do Office Web Apps e adiciona mais servidores ao farm usando o cmdlet **New-OfficeWebAppsMachine**.

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parâmetro</strong></th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AllowCEIP</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita o relatório do Programa de Aperfeiçoamento da Experiência do Usuário (CEIP) em todos os servidores no farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><strong>AllowHttp</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica que os sites IIS devem ser provisionados na porta 80 para acesso HTTP. Use o <strong>AllowHTTP</strong> apenas em ambientes onde todos os computadores exigem IPSEC (criptografia completa) ou em ambientes de teste que não contêm arquivos sensíveis.</p>
<p>Habilitado automaticamente quando o <strong>SSLOffloaded</strong> é habilitado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHttpSecureStoreConnections</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica que as conexões de repositório seguro podem ser estabelecidas usando conexões não SSL (como HTTP). O padrão é <strong>False</strong>.</p>
<p>Use <strong>AllowHTTPSecureStoreConnections</strong> somente em ambientes onde todos os computadores exigem IPSEC (criptografia total) ou em ambientes de teste que não contêm arquivos sigilosos.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o local do cache de disco global usado para armazenar arquivos de imagem renderizados. O local padrão é <strong>%programdata%\Microsoft\OfficeWebApps\Working\d\</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheSizeInGB</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o tamanho máximo do cache de disco global em gigabytes.</p>
<p>O tipo deve ser um valor inteiro no intervalo de <strong>0</strong> a qualquer inteiro positivo. O valor padrão é <strong>15</strong> MB.</p></td>
</tr>
<tr class="even">
<td><p><strong>CertificateName</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome amigável do certificado que o Servidor do Office Web Apps usa para criar associações HTTPS.</p>
<p>Se o certificado especificado não é encontrado ou expirar ou se o valor especificado é associado com mais de um certificado, um erro é registrado e o farm não é criado.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Este valor é usado em cada servidor que se associa ao farm do Servidor do Office Web Apps. Portanto, cada servidor no farm deve ter um certificado que possui este nome amigável.</td>
</tr>
</tbody>
</table>

</div>
<p>Você não precisa especificar o parâmetro <strong>CertificateName</strong> se estiver usando o parâmetro <strong>AllowHttp</strong> ou <strong>SSLOffloaded</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClipartEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Permite que haja suporte para inserir imagens do Bing em documentos do Office. Este recurso exige comunicações do servidor para Web, configurado diretamente ou usando um proxy especificado usando o parâmetro <strong>Proxy</strong>.</p>
<p>O parâmetro <strong>OpenFromUrlEnabled</strong> deve ser definido como <strong>True</strong> para que as imagens do Bing funcionem.. O padrão é <strong>False</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita sua confirmação antes de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>DocumentInfoCacheSize</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o número máximo de registros de conversão do documento armazenados em um cache de memória.</p>
<p>O valor padrão é <strong>True</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>EditingEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita o suporte para edição no navegador. O padrão é <strong>False</strong>. Definido como <strong>True</strong> somente se você tiver o licenciamento apropriado para usar a funcionalidade de edição.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelAllowExternalData</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita a atualização de dados externos com suporte em pastas de trabalho do Excel Web App, em que as pastas de trabalho contêm conexões com dados externos. O padrão é <strong>True</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelConnectionLifetime</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica a duração, em segundos, de conexões de dados externos para o Excel Web App. O padrão é <strong>1.800</strong> segundos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelExternalDataCacheLifetime</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica a duração, em segundos, do tempo de vida útil do cache de dados externos no Excel Web App. O padrão é <strong>300</strong> segundos.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelPrivateBytesMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o máximo de bytes privados, em megabytes, usado pelo Excel Web App. Quando definido como <strong>-1</strong>, o máximo de bytes privados usa 50 por cento da memória física no computador.</p>
<p>O tipo deve ser <strong>-1</strong> ou qualquer positivo inteiro. O valor padrão é <strong>-1.</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelRequestDurationMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica a duração máxima, em segundos, para uma única solicitação em uma sessão. Após este tempo decorrer, a solicitação expira.</p>
<p>O tipo deve ser <strong>-1</strong> (sem limite) ou um inteiro no intervalo de <strong>1</strong> a <strong>2.073.600</strong>. O valor padrão é <strong>300</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelSessionTimeout</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o tempo, em segundos, que uma sessão permanece ativa no Excel Web App quando não há atividade do usuário. Os valores válidos incluem:</p>
<p><strong>-1</strong>   A sessão nunca expira.</p>
<p><strong>0</strong> A sessão expira no final de uma única solicitação.</p>
<p><strong>1</strong> a <strong>2073600</strong> A sessão permanece ativa por 1 segundo a 24 dias. O valor padrão é <strong>450</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelWarnOnDataRefresh</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Desativa ou ativa a caixa de diálogo de aviso exibida quando os dados são atualizados no Excel Web App.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelWorkbookSizeMax</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o tamanho máximo, em megabytes, de uma pasta de trabalho que pode ser carregada.</p>
<p>O tipo deve ser um valor inteiro no intervalo de <strong>1</strong> a <strong>2000</strong>. O valor padrão é <strong>10</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalURL</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a raiz URL que o cliente usa para acessar o farm do Servidor do Office Web Apps pela Internet. Em caso de uma carga balanceada, o farm do Servidor do Office Web Apps multiservidor, o URL externo é vinculado ao endereço IP do balanceador de carga externo.</p>
<p>Um farm do Servidor do Office Web Apps exige pelo menos um URL, definido usando o <strong>ExternalURL</strong> ou <strong>InternalURL</strong>. Também é possível definir URLs internos e externos.</p></td>
</tr>
<tr class="even">
<td><p><strong>FarmOU</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o nome da unidade organizacional (OU) do Active Directory que os servidores devem ser membros para se associar ao farm do Servidor do Office Web Apps. Use este parâmetro para evitar que servidores não autorizados (isto é, servidores que não estão no OU) se associem a um farm do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer prompt do usuário respondendo Sim.</p></td>
</tr>
<tr class="even">
<td><p><strong>InternalURL</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a raiz do URL que o cliente usa para acessar o farm do Servidor do Office Web Apps pela intranet.</p>
<p>Um farm do Servidor do Office Web Apps exige pelo menos um URL, definido usando o <strong>ExternalURL</strong> ou <strong>InternalURL</strong>. Também é possível definir URLs internos e externos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o local no computador local onde os logs de atividade são armazenados.</p>
<p>O local é aplicado a cada servidor no farm e não pode ser personalizado de acordo com o servidor. O local padrão é <strong>%programdata%\Microsoft\OfficeWebApps\Data\Logs\ULS\.</strong></p>
<p>Certifique-se de permitir espaço em disco suficiente no drive onde os logs são armazenados.</p></td>
</tr>
<tr class="even">
<td><p><strong>LogRetentionInDays</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o número de dias que as entradas de log são armazenadas. As entradas de logs anteriores à data configurada são cortadas.</p>
<p>O tipo deve ser um valor inteiro no intervalo de <strong>0</strong> a <strong>365</strong>. O valor padrão é <strong>7</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogVerbosity</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica quanta informação é armazenada nos arquivos de log de rastreamento. Os valores são os seguintes:</p>
<p><strong>VerboseEX</strong> grava detalhes de nível baixo no arquivo de log de rastreamento. Útil para rastreamentos que provavelmente terão alto volume.</p>
<p><strong>Verbose</strong> grava detalhes de nível baixo no arquivo de log de rastreamento.</p>
<p><strong>Medium</strong> grava detalhes de nível médio no arquivo de log de rastreamento.</p>
<p><strong>High</strong> grava detalhes de nível alto no arquivo de log de rastreamento.</p>
<p><strong>Monitorable</strong> grava rastreamentos que representam um caminho de código incomum e ações que devem ser monitoradas.</p>
<p><strong>Unexpected</strong> grava rastreamentos que representam um caminho de código inesperado e ações que devem ser monitoradas.</p>
<p><strong>Nenhum</strong> não grava nenhuma informação no arquivo de log de rastreamento.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Deixar o <strong>LogVerbosity</strong> em nível baixo por um longo período de tempo impactará negativamente o desempenho.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>MaxMemoryCacheSizeInMB</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica, em megabytes, a quantidade máxima de memória que o cache de renderização pode usar.</p>
<p>O tipo deve ser um valor inteiro no intervalo entre <strong>0</strong> e qualquer inteiro positivo. O tamanho padrão é <strong>75</strong> MB.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxTranslationCharacterCount</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica a quantidade máxima de caracteres que um documento pode ter para ser traduzido.</p>
<p>O tipo deve ser um valor inteiro. O valor pode ser definido como <strong>0</strong> para indicar sem limite ou um valor de <strong>2.000</strong> a <strong>2.000.000</strong>. O valor padrão é <strong>125.000</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUncEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Ativa ou desativa o recurso para usar Visualizadores Online para exibir arquivos do Office de um caminho UNC.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219439.note(Office.15).gif" title="Observação" alt="Observação" />Observação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Primeiro, você precisa definir <strong>OpenFromUrlEnabled</strong> como <strong>True</strong> para permitir que os Visualizadores Online exibam os arquivos em caminhos UNC.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>OpenFromUrlEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Ativa ou desativa a habilidade de usar os Visualizadores Online para exibir os arquivos do Office a partir de uma URL ou caminho UNC. O padrão é <strong>False</strong>.</p>
<p>Você deve definir esse parâmetro como verdadeiro ao usar o <strong>ClipartEnabled</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUrlThrottlingEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Acelera o número de solicitações de URL Abrir De a partir de qualquer servidor determinado em um período de tempo. Os valores de aceleração padrão, que não podem ser configurados, garantem que um farm do Servidor do Office Web Apps não sobrecarregará um único servidor com solicitações de conteúdo para visualização nos Visualizadores Online.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PicturePasteDisabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Desativa a capacidade dos usuários de colar imagens de uma página da Web no Office Web Apps. O padrão é <strong>False</strong>. Se <strong>OpenFromURLEnabled</strong> estiver definido como <strong>True</strong> e <strong>PicturePasteDisabled</strong> não estiver definido como <strong>False</strong>, os usuários poderão colar imagens no Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><strong>Proxy</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o URL do servidor de proxy que é configurado para permitir solicitações HTTP para sites externos. Geralmente configurado em conjunto com os parâmetros <strong>ClipartEnabled</strong> e <strong>TranslationEnabled</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecycleActiveProcessCount</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Especifica o número de arquivos que um único processo do Word ou PowerPoint pode renderizar antes do processo ser reciclado.</p>
<p>O tipo deve ser um valor inteiro no intervalo de <strong>1</strong> a <strong>1.000</strong>. O valor padrão é <strong>5</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>RemovePersonalInformationFromLogs</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Limpa informações pessoais dos registros do Servidor do Office Web Apps e substitui os valores pelo código SHA256. As informações que podem ser limpas podem ser:</p>
<ul>
<li><p>Nome de documentos e URLs</p></li>
<li><p>Endereços IP</p></li>
<li><p>Endereços de email</p></li>
<li><p>Nomes de usuário</p></li>
</ul>
<p>O padrão é <strong>False</strong>. Observe que a habilitação deste parâmetro não garante que as informações pessoais não ficarão registradas nos registros do Servidor do Office Web Apps.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RenderingLocalCacheLocation</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica o local do cache temporário para uso pelos Serviços de Exibição do Word e PowerPoint.</p>
<p>O local padrão é <strong>%programdata%\Microsoft\OfficeWebApps\Working\waccache\</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SSLOffloaded</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indica aos servidores no farm do Servidor do Office Web Apps que o SSL é descarregado para o balanceador de carga. Quando o <strong>SSLOffloaded</strong> é habilitado, os aplicativos Web são associados a porta 80 (HTTP) no servidor local. No entanto, o HTML que faz referências a outros recursos, como CSS ou imagens, usa URLs HTTPS para aquelas referências.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationEnabled</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Habilita o suporte para tradução de documento automática usando o Microsoft Translator, um serviço online que traduz texto entre idiomas. O arquivo traduzido é exibido no Word Web App. Como o Microsoft Translator é um serviço online, você deve habilitar a comunicação servidor para Web diretamente ou usando um proxy especificado usando o parâmetro <strong>Proxy</strong>.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219437.important(Office.15).gif" title="Importante" alt="Importante" />Importante</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>O Microsoft Translator pode coletar dados para melhorar a qualidade das traduções.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>TranslationServiceAddress</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a URL do servidor de tradução para o qual as solicitações de tradução são enviadas. O padrão é o serviço online do Microsoft Translator. Geralmente, você não usará esse parâmetro, a menos que precise alterar os serviços de tradução.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationServiceAppId</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Especifica a ID do aplicativo para o serviço de tradução. O padrão é a ID de aplicativo público para o Office Web Apps. Geralmente, você não usará esse parâmetro, a menos que tenha negociado serviços adicionais com o Microsoft Translator e que eles tenham fornecido uma ID de aplicativo particular a você.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Exibe uma mensagem que descreve o efeito do comando em vez de executar o comando. Para saber mais, digite o seguinte comando: <strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

## Tipos de retorno

## Exemplo

\------------------EXEMPLO 1---------------------

    New-OfficeWebAppsFarm -InternalUrl "https://server.corp.contoso.com" -ExternalUrl "https://server.external.contoso.com" -EditingEnabled:$true -SSLOffloaded

Este exemplo cria um farm do Servidor do Office Web Apps no servidor local que tem a edição habilitada para o Office Web Apps. O farm é configurado por balanceamento de carga habilitando o **SSLOffloaded**, que habilita automaticamente o **AllowHttp**. Se você não está usando um balanceador de carga, certifique-se de definir o **CertificateName**.

## Consulte também


[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  


[Mapa de conteúdo para o Servidor do Office Web Apps](content-roadmap-for-office-web-apps-server.md)  
[Implantar a infraestrutura: Servidor do Office Web Apps](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

