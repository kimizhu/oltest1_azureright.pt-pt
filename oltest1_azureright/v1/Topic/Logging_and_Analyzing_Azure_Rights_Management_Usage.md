---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Registo e analisar a utiliza&#231;&#227;o de gest&#227;o de direitos do Azure
Utilize as informações deste tópico para o ajudar a compreender como pode utilizar o registo com o Azure Rights Management (RMS do Azure) de utilização. O serviço Azure Rights Management pode iniciar cada pedido que faz para a sua organização, incluindo pedidos de utilizadores, ações efetuadas por administradores de gestão de direitos na sua organização e ações efetuadas por operadores de Microsoft para suportar a implementação do Azure Rights Management.

Em seguida, pode utilizar estes registos Azure Rights Management para suportar os seguintes cenários de negócio:

-   Analise para informações empresariais.

    Azure Rights Management escreve registos num formato de registo expandido de W3C para uma conta de armazenamento do Azure que indicar. Em seguida, pode direcionar estes registos para um repositório à sua escolha (tal como uma base de dados, um sistema de processamento analítico online (OLAP), ou um reduzir mapa system) a analisar as informações e elaborar relatórios. Por exemplo, foi possível identificar quem está a aceder os dados protegidos pelo RMS. Pode determinar o que as pessoas de dados protegidos pelo RMS estão a aceder e que dispositivos e a partir da qual. Pode saber se as pessoas com êxito podem ler conteúdo protegido. Pode também identificar que pessoas leu um documento importante que estava protegido.

-   Monitor de abuso.

    Informações de registo de gestão de direitos do Azure estão disponíveis para si no tempo de perto real, para que possa continuamente monitorizar utilização da sua empresa de gestão de direitos. 99,9% de registos estão disponíveis em 15 minutos de uma ação iniciada por RMS.

    Por exemplo, poderá ser alertado se existir um aumento repentino das pessoas a leitura de dados protegida por RMS fora do horário de trabalho padrão, que pode indicar que um utilizador mal intencionado está a recolher informações sobre a vender concorrência. Em alternativa, se o mesmo utilizador acede gráfico dados a partir de dois endereços IP diferentes num período de hora abreviada, que pode indicar que uma conta de utilizador tiver sido comprometida.

-   Efetue análise forense.

    Se tiver uma fuga de informações, é provável que ser-lhe pedido que tenha acedido recentemente documentos específicos e as informações que uma pessoa potencialmente acesso recentemente. Pode atender destes tipos de perguntas quando utiliza o Azure Rights Management e registo porque as pessoas que utilizam protegido conteúdo sempre tem de obter uma licença de gestão de direitos para abrir documentos e imagens que são protegidas pelo Azure Rights Management, mesmo que estes ficheiros são movidos por correio eletrónico ou copiados para unidades USB ou outros dispositivos de armazenamento. Isto significa que pode utilizar os registos do Azure Rights Management como definitivo fonte de informações para análise forense quando proteger os seus dados, utilizando a gestão de direitos do Azure.

> [!NOTE]
> Se estiver interessado apenas o registo de tarefas administrativas para gestão de direitos do Azure e execute não as pretender controlar como os utilizadores estão a utilizar gestão de direitos, pode utilizar o [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) cmdlet do Windows PowerShell para o Azure Rights Management.
> 
> Também pode utilizar o portal do Azure para relatórios de utilização de alto nível que incluem **utilização RMS**, **utilizadores RMS mais ativos**, **utilização do dispositivo de RMS**, e **RMS ativou a utilização de aplicação**. Para aceder a estes relatórios a partir do portal do Azure, clique em **do Active Directory**, selecione e abra um diretório e, em seguida, clique em **relatórios**,

Utilize as secções seguintes para obter mais informações sobre o registo de utilização do Azure Rights Management.

-   [Como ativar o registo de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Como aceder e utilizar os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Como gerir o armazenamento de registo do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Como delegar acesso para os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Interpretar os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Referência do Windows PowerShell](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Como ativar o registo de utilização do Azure Rights Management
Registo de utilização do Azure Rights Management é opcional, por isso se pretender utilizá-lo, terá de efetuar passos específicos. Quando utiliza o registo de utilização do Azure Rights Management, não existe qualquer alteração de como funciona o Rights Management e o processo de registo propriamente dito está livre. No entanto, tem de fornecer uma conta de armazenamento do Azure para os registos e será cobrada por este armazenamento.

Antes de começar, certifique-se de que cumpre os seguintes pré-requisitos para utilizar o registo de utilização do Azure Rights Management:

|Requisito|Obter mais informações|
|-------------|--------------------------|
|Uma subscrição de gestão de TI que inclui o Azure Rights Management|Tem de ter uma subscrição do Microsoft Azure Rights Management é gerida pela sua organização. As organizações que utilizam o RMS para indivíduos não é possível utilizar o registo de utilização do Azure Rights Management.<br /><br />Se a sua organização tiver utilizadores que utilizam o RMS para indivíduos, o registo de utilização do Azure Rights Management fornece uma razão comercial muito apelativa para converter o RMS para indivíduos para uma subscrição do Microsoft Azure Rights Management.<br /><br />Para mais informações sobre as subscrições que incluem o Azure RMS, consulte o [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico.<br /><br />Para mais informações sobre RMS para indivíduos, consulte [RMS para indivíduos e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Subscrição do Azure|Tem de ter uma subscrição do Azure e suficiente armazenamento no Azure para os seus registos do Azure Rights Management.|
|Windows PowerShell para o Azure Rights Management|Se ainda não o fez, transfira e instale o módulo Windows PowerShell para o Azure Rights Management. Irá utilizar cmdlets do Windows PowerShell para configurar e gerir os seus registos de utilização do Azure Rights Management.<br /><br />Para obter mais informações, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Utilize o procedimento seguinte para ativar o registo de utilização do Azure Rights Management, que inclui passos para criar uma conta de armazenamento do Azure e, em seguida, configurar o Azure para utilizar esta conta de armazenamento para os seus registos do Rights Management.

> [!NOTE]
> Este procedimento assume que tem uma conta do Azure. Registo de utilização do Azure Rights Management suporta contas individuais, mas como uma melhor prática, utilizar escolar ou profissional contas. Além disso, recomendamos que crie uma conta de armazenamento dedicado para os seus registos do Rights Management. Tem de partilhar as chaves de acesso de armazenamento com o Azure Rights Management e, potencialmente com outras pessoas se também utilizarão os ficheiros de registo.
> 
> Para mais informações sobre armazenamento do Azure, consulte o [documentação do Azure para armazenamento](http://azure.microsoft.com/documentation/services/storage/).

#### Como criar a sua conta de armazenamento e ativar o registo de utilização do Azure Rights Management

1.  Início de sessão para o [portal do Azure](https://manage.windowsazure.com/).

2.  Selecione **armazenamento**.

    > [!TIP]
    > Se não vir esta opção, verifique se tem uma subscrição do Azure, além da sua subscrição para o Rights Management.

3.  Clique em **criar conta de armazenamento de um** e para o **URL**, introduza um nome exclusivo para a conta de armazenamento e, se necessário, altere o **grupo de AFINIDADES/localização** para que corresponde a sua região.

4.  Clique em **OK**, e aguarde até ver o nome do seu armazenamento mostram um Estado de **Online**.

5.  Clique em **Gerir as chaves de acesso**.

6.  A partir de **Gerir as chaves de acesso** caixa de diálogo que mostra as chaves de acesso primária e secundária, copie a chave de acesso primária para a área de transferência e, em seguida, feche a caixa de diálogo.

7.  Inicie o Windows PowerShell com o **Executar como administrador** opção. Executar o [Ligar AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) comando para ligar ao serviço de gestão de direitos do Azure:

    ```
    Connect-AadrmService
    ```

8.  Utilize o [conjunto AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) comandos para especificar para onde pretende manter os seus registos de utilização do Azure Rights Management, substituindo *&lt; Access_Key &gt;* com a chave de acesso primária que copiou no passo 6 e *&lt; StorageAccount &gt;* com o nome da conta de armazenamento que criou no passo 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Utilize o [Ativar AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) comando para ativar o registo de utilização do Azure Rights Management:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Deverá ver a mensagem: **A funcionalidade de registo de utilização é ativada para o serviço de gestão de direitos.**

Agora que o registo de utilização é ativado, o Azure Rights Management começa a registar todas as ações para a sua organização e guarda estas informações para a sua conta de armazenamento. As informações de registo não estão disponíveis antes deste ponto.

## <a name="BKMK_AccesAndUseLogs"></a>Como aceder e utilizar os seus registos de utilização do Azure Rights Management
Azure Rights Management escreve registos à sua conta de armazenamento do Azure como uma série de blobs. Cada blob contém um ou mais registos de registo, num formato de registo expandido de W3C. Os nomes de blob são números, pela ordem em que foram criados. O [Interpretar os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) secção mais à frente neste documento contém mais informações sobre os conteúdos de registo e a respetiva criação.

Pode demorar algum tempo para os registos a aparecer na sua conta de armazenamento após uma ação de Azure Rights Management. A maioria dos registos são apresentados em 15 minutos.

A conta de armazenamento que criou para os seus registos de utilização do Azure Rights Management é como uma caixa de correio e suporta leitura diretamente a partir da conta de armazenamento, mas não está otimizada para serem utilizados desta forma. Em vez disso, para um melhor desempenho e para ajudar a reduzir os custos, recomendamos que transfira os registos para o armazenamento local, tal como uma pasta local, uma base de dados, ou um repositório de reduzir mapa.

Pode transferir os seus registos de utilização de duas formas:

-   Utilize o cmdlet do Windows PowerShell [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Esta é a forma mais simples para aceder aos seus registos de utilização. Este cmdlet transfere registos para o seu computador, transferir cada blob como um ficheiro para uma localização que especificou.

-   Utilize o [SDK de armazenamento do Azure](http://www.windowsazure.com/en-us/develop/net/) ao escrever a sua própria aplicação personalizada para transferir os registos.

    Uma aplicação personalizada pode fornecer mais flexibilidade do que o cmdlet Get-AadrmUsageLogs. Por exemplo, poderá querer delegar a transferência de registos a pessoa ou um processo que não tem de utilizar as credenciais administrativas do Azure Rights Management. Em alternativa, pode querer são consultados os registos em tempo real, uma vez que pretende monitorizar utilização indevida.

#### Para transferir os seus registos de utilização utilizando o PowerShell

-   Inicie o Windows PowerShell com o **Executar como administrador** opção e execute **Get-AadrmUsageLog –Path &lt;location&gt;**. Por exemplo, depois de criar uma pasta denominada **logs** no disco I:

    -   Para transferir todos os registos disponíveis para a pasta E:\logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Para transferir um intervalo específico de blobs: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Quando execute estes cmdlets, o Windows PowerShell apresenta o nome do último blob que foi transferido. Pode atribuir este nome a uma variável, o que lhe permite executar Get-AadrmUsageLog uma tarefa de agenda ou um ciclo, transferir apenas os registos incrementais cada vez.

Por exemplo:

**PS C:\ &gt; $LastBlobName = Get-AadrmUsageLog – o caminho "e:\logs"**

**1527**

**PS C:\ &gt; $LastBlobName**

**1527**

> [!TIP]
> Pode agregar todos os ficheiros de registo do transferido para um formato CSV, utilizando [Parser de registo da Microsoft](http://www.microsoft.com/download/details.aspx?id=24659), que é uma ferramenta para converter entre vários formatos de registo bem conhecidas. Também pode utilizar esta ferramenta para converter os dados para formato SYSLOG ou importá-lo para uma base de dados. Depois de instalar a ferramenta, executar **LogParser.exe /?** para obter ajuda e informações para utilizar esta ferramenta. Por exemplo, poderá executar o seguinte comando para importar todas as informações para um formato de ficheiro. log: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

Pode suspender e retomar o registo de utilização. Quando suspende o registo, o Azure Rights Management mantém as informações da conta de armazenamento, para que possa a retomar facilmente o registo novamente.

#### Suspender e retomar o registo de utilização

-   Para suspender o registo, utilize o seguinte cmdlet: [Desativar AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Para retomar o registo, utilize o seguinte cmdlet: [Ativar AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Para verificar se o registo está ativado ou desativado, utilize o seguinte cmdlet: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Um valor de **Verdadeiro** significa que o registo de utilização é ativado para gestão de direitos do Azure e um valor de **Falso** significa que o registo de utilização é desativado.

## <a name="BKMK_ManageStorage"></a>Como gerir o armazenamento de registo do Azure Rights Management
São cobradas para o espaço de armazenamento que é utilizado para manter os seus registos do Azure Rights Management.

Azure Rights Management não sem gestão automática dos seus ficheiros de registo de utilização. Se não tomar medidas, irão permanecer na sua conta de armazenamento. No entanto, para poupar espaço e reduzir os custos de armazenamento, poderá eliminá-las depois de ter transferido-los. Ou pode escolher quais os ficheiros para eliminar. Com uma exceção, Azure Rights Management não utiliza estes ficheiros de registo, por isso, não sem restrições sobre quando pode eliminá-las.

Chama-se o ficheiro que não tem eliminar (ou modificar) **metadados** que está a **rms metadados** contentor. Azure Rights Management utiliza esta blob para controlar o último número de blob utilizado. Se este ficheiro é eliminado, Azure Rights Management começa um novo contentor para os registos, com um número de blob que começa a 1 e todas as transferências futuras que utilizam o cmdlet Get-AadrmUsageLog utilizam este novo contentor para transferir ficheiros de registo. Como resultado, nenhum registo no contentor original é mantido, mas órfãos. É a única forma de transferir estes registos órfãos utilizar o SDK de armazenamento Azure.

> [!TIP]
> Em vez de gerir o armazenamento de registo do Azure Rights Management-la sozinho, pode delegar esta função de gestão a outra empresa ao partilhar a sua chave de acesso e o nome da conta de armazenamento. Para obter mais informações, consulte o [Como delegar acesso para os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) secção mais à frente neste tópico.

Em algumas circunstâncias, pode querer voltar a gerar as chaves de acesso de armazenamento. Por exemplo:

-   Alterar a empresa que gere os seus registos de utilização do Azure Rights Management.

-   Se suspeita que a sua chave de acesso de armazenamento estiver comprometido.

Se isto acontecer, esta é quando utiliza a chave de acesso secundária (-se no pressuposto que anteriormente estava a usar a chave de acesso primária) para assegurar a continuidade do serviço. Quando voltar a gerar a chave de acesso que ainda não foram anteriormente utilizar, em seguida, configure Azure Rights Management para utilizar a nova chave. Utilize o procedimento seguinte para gerar a chave de acesso secundária e configurar o Azure Rights Management para utilizá-lo:

#### A gerar a chave de acesso secundária

1.  Início de sessão para o [portal do Azure](https://manage.windowsazure.com/).

2.  Selecione **armazenamento**.

3.  Clique em **Gerir as chaves de acesso**.

4.  No **Gerir as chaves de acesso** caixa de diálogo, clique em **regenerar** junto a chave de acesso secundária e copie-a nova chave de acesso secundária para a área de transferência.

5.  Inicie o Windows PowerShell com o **Executar como administrador** opção e utilizar o [conjunto AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) cmdlet para configurar o Azure Rights Management para utilizar esta nova chave de acesso, substituindo *&lt; StorageAccount &gt;* com o nome da sua conta de armazenamento e *&lt; Access_Key &gt;* com a chave de acesso secundária regenerada que acabou de copiar:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > Apesar de, pode mudar para outra conta de armazenamento ao executar este comando, esta ação orphans os seus registos do anterior e estes deixarão de estar acessíveis para o cmdlet Set-AadrmUsageLogStorageAccount ou semelhante comandos de gestão e funções.

6.  Voltar a **Gerir as chaves de acesso** diálogo caixa, regenerar a chave de acesso primária.

## <a name="BKMK_Delegate"></a>Como delegar acesso para os seus registos de utilização do Azure Rights Management
Pode delegar acesso para os seus registos do RMS através da partilha a sua chave de acesso e o nome da conta de armazenamento. Pode querer delegar acesso a outro utilizador administrativo para um programador na sua própria organização ou para um fabricante independente de software (ISV). Porque não terão as credenciais de administrador de RMS, estes não podem utilizar o cmdlet Get-AardrmUsageLog para transferir os registos do RMS. Em vez disso, terão de utilizar o SDK de armazenamento do Windows para transferir os registos. Em alternativa, estes podem escrever uma aplicação para ler os registos diretamente a partir do armazenamento do Azure.

É seguro partilhar a sua chave de acesso e o nome de conta de armazenamento desta forma, quando a conta de armazenamento dedicada para os seus registos do RMS. Mesmo que outras pessoas tenham a chave de acesso, não é possível utilizar esta para aceder a qualquer outra conta de armazenamento ou utilizar a sua conta de inquilino do RMS.

## <a name="BKMK_Interpret"></a>Interpretar os seus registos de utilização do Azure Rights Management
Utilize as seguintes informações para ajudar a interpretá os registos de utilização do Azure Rights Management.

### O esquema de conta de armazenamento
Na primeira vez que o Azure Rights Management escreve registos à sua conta de armazenamento, cria os seguintes duas contentores:

-   **Rms metadados**: Este contentor de está reservado para o Azure Rights Management. Não modificar ou eliminar neste contentor.

-   **Rms - registos - &lt; guid &gt;**: Este contentor é onde o Azure Rights Management cria e guarda os registos. Pode eliminar em segurança todos os ficheiros neste contentor se já não pretender que as informações de registo que contêm.

Ao longo do tempo, o Azure Rights Management pode criar adicional **Rms - registos - &lt; guid &gt;** contentores. Por exemplo, se o **Rms metadados** contentor fica danificado ou é eliminada acidentalmente, Azure Rights Management repõe o respetivo conteúdo e cria uma nova **Rms - registos - &lt; guid &gt;** contentor para todos os registos futuros. Os registos antigos no contentor antigo não são eliminados mas ficarão órfãos.

### A sequência de registo
Azure Rights Management escreve os registos de como uma série de blobs. Cada blob contém um ou mais registos de registo, num formato de registo W3C expandido.

O nome de cada blob é um número. Dentro do contentor cada registo o blob primeiro é denominado 000000001. Cada blob é denominado sequencialmente pela ordem em que foi criada. Cada blob contém um ou mais registos de registo. Cada registo tem um carimbo de hora UTC que indica quando o pedido correspondente servido pelo Azure Rights Management.

> [!IMPORTANT]
> O sistema de registo do Azure Rights Management está otimizado para lhe fornecer registos rapidamente, em vez de por ordem sequencial estrita. A ordem dos blobs, bem como a ordem dos registos dentro de um blob, poderá ter ficado sem sequência cronológica. A razão apenas que BLOBs são denominados sequencialmente é permitem-lhe de forma eficiente transferi-los de forma incremental.
> 
> Dois exemplos de potenciais resultados de sequência de registo:
> 
> -   Os registos no blob 000000004 poderão sobrepor-se cronologicamente com os registos no blob 000000003. Num cenário extremos, todos os registos no blob 000000004 poderão ter sido gerados antes de todos os registos no blob 000000003.
> -   O segundo registo de registo num blob poderá ter sido gerado antes do primeiro registo de registo, mas tenha sido escrito para armazenamento na ordem inversa.

Antes de analisar os seus registos de utilização do Azure Rights Management, recomendamos que transfira e importe-o registo para um repositório de onde pode ordenar os registos com base no respetivo timestamp. Para obter mais informações sobre como transferir os registos, consulte o [Como aceder e utilizar os seus registos de utilização do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) deste tópico.

Uma vez que os registos não são necessariamente cronológicos mas a maioria dos mesmos são escritos em 15 minutos do pedido, quando identifica os registos que pretende, utilizando os respetivos timestamp, adicione 15 minutos até ao momento em que está interessado. Em seguida, transferir estes registos. Esta estratégia deve garantir que obtém quase todos os registos.

Outra coisa a memorizar os é que o timestamp em cada registo é a hora local do serviço Azure Rights Management que processar o pedido. Porque Azure Rights Management é executada em vários servidores em vários centros de dados, por vezes, os registos podem parecer ter fora da sequência, mesmo quando estes são ordenados pelo respetivo timestamp. No entanto, os diferentes situação pequeno e normalmente dentro de um minuto. Na maioria dos casos, isto não é um problema de é um problema para análise do registo.

### O formato de blob
Cada blob está num formato de registo expandido de W3C. Comece com as seguintes duas linhas:

**#Software: RMS**

**#Version: 1.1**

A primeira linha identifica que estes são os registos do Azure Rights Management. A segunda linha identifica que o resto do blob segue a especificação de versão 1.1. Recomendamos que todas as aplicações que analisar estes registos verificar estas duas linhas antes de continuar a analisar o resto do blob.

A terceira linha enumera uma lista de nomes de campos que são separados por separadores:

**#Fields: data tempo id de linha tipo de pedido id de utilizador resultado id de correlação id de conteúdo. o proprietário-e-mail emissor id do modelo-nome do ficheiro publicados data c informações c-ip**

Cada uma das linhas subsequentes é um registo de registo. Os valores dos campos estão na mesma ordem que a linha anterior e são separados por separadores. Utilize a tabela seguinte para interpretar os campos.

|Nome do campo|Tipo de dados de W3C|Descrição|Valor de exemplo|
|-----------------|------------------------|-------------|--------------------|
|data|Data|Data UTC quando o pedido foi servido.<br /><br />A origem é o relógio local no servidor que servida o pedido.|2013-06-25|
|tempo|Tempo|Hora UTC no formato de 24 horas, quando o pedido foi servido.<br /><br />A origem é o relógio local no servidor que servida o pedido.|21:59:28|
|id de linha|Texto|GUID exclusivo para este registo.<br /><br />Este valor é útil quando agregar registos ou registos de cópia noutro formato.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|tipo de pedido|Nome|Nome da API do RMS que foi pedido.|AcquireLicense|
|id de utilizador|Cadeia|O utilizador que efetuou o pedido.<br /><br />O valor está escrito entre plicas. Alguns tipos de pedido são anónimos, caso em que é o valor ".|'joe@contoso.com'|
|resultado|Cadeia|"Êxito" se o pedido foi servido com êxito.<br /><br />O tipo de erro plicas se o pedido falhou.|"Êxito"|
|id de correlação|Texto|GUID que é comum entre o registo de cliente do RMS e o registo de servidor para um pedido específico.<br /><br />Este valor pode ser útil para ajudar a resolução de problemas do cliente.|cab52088-8925-4371-be34-4b71a3112356|
|id de conteúdo|Texto|GUID, entre chavetas que identifica o conteúdo protegido (por exemplo, um documento).<br /><br />Este campo tem um valor apenas se o tipo de pedido é AcquireLicense e está em branco para todos os outros tipos de pedido.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|proprietário do e-mail|Cadeia|Endereço de e-mail do proprietário do documento.|Alice@contoso.com|
|emissor|Cadeia|Endereço de e-mail do emissor do documento.|Alice@contoso.com (ou) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|Id do modelo|Cadeia|ID do modelo utilizado para proteger o documento.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Nome de ficheiro|Cadeia|Nome de ficheiro do documento que estava protegido.|TopSecretDocument.docx|
|Publicado por data|Data|Data quando o documento foi protegido.|2015-10-15T21:37:00|
|informações de c|Cadeia|Informações sobre a plataforma de cliente que está a fazer o pedido.<br /><br />A cadeia específica varia, dependendo da aplicação (por exemplo, o sistema operativo ou o browser).|' MSIPC;) versão = 1.0.623.47; AppName = WINWORD. EXE; AppVersion = 15.0.4753.1000; AppArch = x86; OSName = Windows; OSVersion = 6.1.7601; OSArch = amd64'|
|c-ip|Endereço|Endereço IP do cliente que faz com que o pedido.|64.51.202.144|

#### Exceções para o campo de id de utilizador
Apesar do campo de id de utilizador indica normalmente o utilizador que efetuou o pedido, existem duas exceções onde o valor não é mapeado para um utilizador real:

-   O valor **' microsoftrmsonline @&lt; YourTenantID &gt;. &lt; Região &gt; do RMS. aadrm.com'**.

    Isto indica que um serviço do Office 365, como o Exchange Online ou Sharepoint Online, está a fazer o pedido. Na cadeia de *&lt; YourTenantID &gt;* é o GUID para o seu inquilino e *&lt; Região &gt;* é a região onde está registado o seu inquilino. Por exemplo, **ND** representa América do Norte – **UE** representa Europa, e **ap** representa da Ásia.

-   Se estiver a utilizar o conector do RMS.

    Pedidos deste conector são registados com o nome principal de serviço que RMS gera automaticamente ao instalar o conector do RMS.

#### Tipos de pedido típica
Existem vários tipos de pedido para o Azure Rights Management, mas a tabela seguinte identifica alguns dos tipos de pedido normalmente utilizados.

|Tipo de pedido|Descrição|
|------------------|-------------|
|AcquireLicense|um cliente a partir de um computador baseado no Windows está a solicitar uma licença para o conteúdo protegido por RMS.|
|AcquirePreLicense|um cliente, em nome do utilizador, está a solicitar por uma licença para o conteúdo protegido por RMS.|
|AcquireTemplates|foi feita uma chamada para adquire modelos com base no modelo IDs|
|AcquireTemplateInformation|foi feita uma chamada para obter os IDs do modelo de serviço.|
|AddTemplate|é feita uma chamada a partir do portal do Azure para adicionar um modelo.|
|BECreateEndUserLicenseV1|é feita uma chamada a partir de um dispositivo móvel para criar uma licença do utilizador final.|
|BEGetAllTemplatesV1|é feita uma chamada a partir de um dispositivo móvel (back-end) para obter todos os modelos.|
|Certify|o cliente é certifying o conteúdo para proteção.|
|Desencriptar|o cliente está a tentar desencriptar o conteúdo protegido por RMS.|
|DeleteTemplateById|é feita uma chamada a partir do portal do Azure, para eliminar um ID de modelo pelo modelo.|
|ExportTemplateById|é feita uma chamada a partir do portal do Azure para exportar um modelo baseado num modelo ID|
|FECreateEndUserLicenseV1|é semelhante ao pedido de AcquireLicense mas a partir de dispositivos móveis.|
|FECreatePublishingLicenseV1|igual Certify e GetClientLicensorCert combinados, a partir de clientes móveis.|
|FEGetAllTemplates|é feita uma chamada, a partir de um dispositivo móvel (front-end) para obter os modelos.|
|GetAllTemplates|é feita uma chamada a partir do portal do Azure, para obter todos os modelos.|
|GetClientLicensorCert|o cliente está a solicitar um certificado de publicação (que é posteriormente utilizado para proteger conteúdo) a partir de um computador baseado em Windows.|
|GetConfiguration|cmdlet do PowerShell do Azure um chama-se para obter a configuração do inquilino do Azure RMS.|
|GetConnectorAuthorizations|é feita uma chamada a partir de conectores do RMS para obter a configuração a partir da nuvem.|
|GetTenantFunctionalState|portal do Azure está a verificar se o Azure RMS é ativado.|
|GetTemplateById|é feita uma chamada a partir do portal do Azure para obter um modelo, especificando um ID de modelo|
|ExportTemplateById|está a ser feita uma chamada a partir do portal do Azure para exportar um modelo, especificando um ID de modelo|
|FindServiceLocationsForUser|é feita uma chamada para consultar os URLs, que é utilizada para telefonar Certify ou AcquireLicense.|
|ImportTemplate|é feita uma chamada a partir do portal do Azure para importar um modelo.|
|ServerCertify|é feita uma chamada a partir de um cliente preparados para RMS (por exemplo, o SharePoint) para o servidor de certificar.|
|SetUsageLogFeatureState|é feita uma chamada para ativar o registo de utilização.|
|SetUsageLogStorageAccount|é feita uma chamada para especificar a localização dos registos do Azure RMS.|
|SignDigest|é feita uma chamada quando é utilizada uma chave para fins de assinatura. Esta opção é denominada normalmente uma vez por AcquireLicence (ou FECreateEndUserLicenseV1), Certify e GetClientLicensorCert (ou FECreatePublishingLicenseV1).|
|UpdateTemplate|é feita uma chamada a partir do portal do Azure para atualizar um modelo existente.|

## <a name="BKMK_PowerShell"></a>Referência do Windows PowerShell
Utilize os seguintes cmdlets do Windows PowerShell para o ajudar a configurar e utilizar o registo de utilização do Azure Rights Management:

-   [Desativar AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Ativar AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Conjunto AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Para obter mais informações sobre como utilizar o Windows PowerShell para o Azure Rights Management, consulte o artigo [Administrar o Azure Rights Management utilizando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Consultar Também
[Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

