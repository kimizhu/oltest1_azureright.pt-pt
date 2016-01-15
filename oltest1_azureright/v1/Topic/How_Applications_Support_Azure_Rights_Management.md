---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Como as aplica&#231;&#245;es suportam gest&#227;o de direitos do Azure
Utilize as seguintes informações para ajudar a compreender como as suas aplicações de utilizador final (tal como o Office aplicações, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e SharePoint) podem utilizar o Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para ajudar a proteger dados da sua organização:

-   [Aplicação para o Windows e de plataformas móveis de partilha RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Aplicações do Office: Word, Excel, PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online e do Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online e no SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Servidores de ficheiros que executam o Windows Server e utilizam a infraestrutura de classificação de ficheiros (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Outras aplicações que suportam as APIs de RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Para verificar as aplicações e versões que [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS do Azure) suporta, consulte o artigo [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

Em alguns casos, a proteção de informações é aplicada automaticamente, de acordo com as políticas que configurar. Por exemplo, é este o caso com bibliotecas do SharePoint, ficheiros classificados e regras de transporte do Exchange. Noutros casos, os utilizadores tem de aplicar proteção de informações por si próprios das suas aplicações, selecionando um modelo ou ao selecionar opções específicas. Por exemplo, é este o caso quando os utilizadores partilhar um ficheiro por e-mail ou proteger um ficheiro no local por restringir o acesso ou utilização para utilizadores selecionados ou para os utilizadores fora da organização.

Modelos de tornam mais fácil para os utilizadores (e administradores que configurar políticas) para aplicar o nível correto de proteção e restringir o acesso a pessoas da sua organização. Embora [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] vem com dois modelos de predefinido, é provável que pretenda criar modelos personalizados para reduzir as horas quando têm de especificar as opções de individuais. Para obter mais informações, consulte o artigo [Configurar modelos personalizados para o Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Para os casos em que os utilizadores tem de aplicar proteção de informação, certifique-se de que dê-lhes com instruções e orientações sobre como e quando efetuar esta ação. As instruções devem ser específicas para a aplicação e das versões que utilizarem e como podem utilizar os mesmos e a orientação para quando e como informações de aplicar proteção deve ser adequada para a sua empresa. Para obter mais informações, consulte o artigo [Ajudar os utilizadores a proteger ficheiros utilizando o Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Para obter informações sobre como configurar estas aplicações para o Azure RMS, consulte o artigo [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Para exemplos e capturas de ecrã das aplicações a utilizar o Azure RMS, consulte o [Azure RMS em ação: O que os utilizadores e administradores visualizam](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) secção a partir de [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tópico.

## <a name="BKMK_SharingAppIntro"></a>Aplicação para o Windows e de plataformas móveis de partilha RMS
A aplicação de partilha RMS é uma aplicação gratuita de transferível que é necessário para suportar o Office 2010, mas também recomendada para os computadores com o Windows, computadores Mac e dispositivos móveis. Uma das respetivos benefícios é que pode a aplicar proteção genérica para aplicações e ficheiros que não suportam nativamente [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], o que significa que todos os ficheiros podem ser protegidos. Para mais informações sobre os níveis de proteção diferentes, consulte o [nível de proteção – nativa e genérica](http://technet.microsoft.com/library/dn339003.aspx) secção a partir de [Guia do administrador aplicação partilha Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

Quando os utilizadores protegem os seus ficheiros utilizando o RMS partilhar a aplicação, podem também controlar os documentos que estão protegidas e se for necessário, revogar o acesso aos mesmos. Para tal, utilizando o [documento controlo do site](http://go.microsoft.com/fwlink/?LinkId=529562).

Para computadores Windows, aplicação de partilha RMS unobtrusively integra-se com e melhora as aplicações que os utilizadores já a utilizar:

-   Um suplemento do Office para Word, Excel, PowerPoint e Outlook está instalado. Isto proporciona aos utilizadores com um **partilhar protegido** botão no Friso, o que invoca uma caixa de diálogo de fácil utilização de definições que são normalmente utilizados para proteger ficheiros para ser enviado por correio eletrónico. Este botão também fornece uma forma rápida de aceder ao site de monotorização de documentos.

-   Uma nova opção de clique o botão direito no Explorador de ficheiros. Isto proporciona aos utilizadores com um **proteger no local** opção, o que invoca uma caixa de diálogo de fácil utilização de definições que são normalmente utilizados para proteger ficheiros armazenados num disco.

-   Um visualizador para abrir ficheiros que foram protegidos por [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Este Visualizador será invocado o automaticamente quando não existe nenhuma outra aplicação instalada que foi possível abrir o ficheiro protegido.

-   Configuração de back-end para o Office 2010, que permite o Word, Excel, PowerPoint e Outlook a partir deste conjunto de aplicações trabalhar de forma totalmente integrada com [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Embora a aplicação para o Windows de partilha RMS pode ser transferida e instalada para um único computador utilizando o [página Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), também suporta uma implementação de empresa para instalação automática e de configuração personalizado. Para obter mais informações, consulte os seguintes recursos:

-   [Guia partilha Rights Management aplicação administrador](http://technet.microsoft.com/library/dn339003.aspx)

-   [Guia de utilizador de aplicação partilha do Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

A aplicação para dispositivos móveis de partilha RMS suporta os dispositivos móveis utilizados com maior frequência, tal como o iPad e iPhone, Android, Windows Phone e Windows RT. Os utilizadores podem transferir esta aplicação da loja relevante e não existirem ligações às funções a partir de [página Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Aplicações do Office: Word, Excel, PowerPoint, Outlook
Estas aplicações nativamente suportam a gestão de direitos, utilizando a gestão de direitos de informação (IRM) e permitem aos utilizadores aplicar proteção a um documento guardado ou a uma mensagem de correio eletrónico que será enviada. Os utilizadores podem aplicar modelos ou escolher definições muito personalizadas para as restrições de acesso, os direitos e utilização. Por exemplo, os utilizadores podem configurar um ficheiro para que possa ser acedido apenas por pessoas na sua organização ou controlo se o ficheiro pode ser editado, restrito a só de leitura ou impedi-lo de que está a ser impresso. Para ficheiros sensíveis ao tempo, um tempo de expiração pode ser configurado (diretamente por utilizadores ou ao aplicar um modelo) para quando o ficheiro já não pode ser acedido. Para o Outlook, os utilizadores também podem escolher a **não reencaminhar** opção para ajudar a evitar a fuga de dados.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online e do Exchange Server
Quando utiliza o Exchange Online ou o Exchange Server, pode utilizar a integração de gestão (IRM) direitos de informação, que fornece informações adicionais soluções de proteção:

-   **Exchange ActiveSync IRM** para que dispositivos móveis poderá proteger e consumir protegidas mensagens de correio eletrónico.

-   Suporte de RMS para o **Outlook Web App**, implementadas da mesma forma para o cliente do Outlook, para que os utilizadores podem proteger mensagens de correio eletrónico por modelos ou especificando opções individuais, e os utilizadores podem ler e utilizar protegidas mensagens de e-mail que são enviadas aos mesmos.

-   **Regras de proteção** para clientes do Outlook que o administrador configura para aplicar modelos de RMS para correio eletrónico automaticamente mensagens para destinatários especificados. Por exemplo, quando internas mensagens de correio eletrónico são enviadas para o seu departamento jurídico, estes só podem ser lidas por membros do Departamento jurídico e não podem ser reencaminhadas. Os utilizadores veem a aplicada à mensagem de e-mail antes de enviar a proteção e, por predefinição, podem removê-la se podem decidir não é necessário. Mensagens de correio eletrónico são encriptadas antes de serem enviados. Para obter mais informações, consulte o artigo [regras de proteção do Outlook](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [criar uma regra de proteção do Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Regras de transporte** que o administrador configura a aplicar automaticamente modelos do RMS para correio eletrónico mensagens com base nas propriedades, tais como remetente, destinatário, assunto da mensagem e conteúdo. Estes são semelhantes no conceito às regras de proteção, mas não permitir que os utilizadores remover a proteção, pode ser aplicada ao Outlook Web Access e mensagens de correio eletrónico enviadas por dispositivos móveis e não encripte mensagens de correio eletrónico antes de serem enviados do cliente. Para obter mais informações, consulte o artigo [criar uma regra de proteção de transporte](http://technet.microsoft.com/library/dd302432.aspx) na biblioteca do Exchange.

-   **Políticas de prevenção (DLP) de perda de dados** que contêm conjuntos de condições para filtrar mensagens de correio eletrónico e adotar medidas para ajudar a evitar perda de dados sensíveis ou confidenciais conteúdo (por exemplo, informações pessoais ou informações de cartão de crédito). Sugestões de políticas podem ser utilizados quando são detetados dados confidenciais, a utilizadores de alertas que que poderão ter de aplicar a proteção de informações, com base nas informações na mensagem de e-mail. Para obter mais informações, consulte o artigo [prevenção de perda de dados](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Encriptação de mensagens do office 365** que utiliza regras para enviar e-mails encriptados para pessoas fora da sua empresa de transporte e é ler o e-mail num browser com uma interface semelhante para o Outlook Web App. Pode personalizar o texto de exclusão de responsabilidade e o texto do cabeçalho e-mails encriptados da sua empresa e, até adicionar o logótipo da empresa. Para obter mais informações, consulte o artigo [encriptação de mensagens do Office 365](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) a partir do Web site do Office.

Se utiliza o Exchange Server, pode utilizar as funcionalidades de proteção de informações com [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] ao implementar o conector de RMS, que age como um reencaminhamento entre os servidores no local e o serviço de nuvem do RMS. Para obter mais informações, consulte o artigo [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online e no SharePoint Server
Quando utiliza o SharePoint Online ou no SharePoint Server, pode utilizar informações integração de gestão (IRM) de direitos, que permite aos administradores de proteger as listas ou bibliotecas para que quando um utilizador verifica-se um documento, o ficheiro está protegido, para que apenas autorizado as pessoas pode ver e utilizar o ficheiro de acordo com as políticas de proteção de informações que especificar. Por exemplo, o ficheiro poderá ser só de leitura, desativar a cópia de texto, impedir que guardar uma cópia local e evitar imprimir o ficheiro.

Para listas e bibliotecas, a proteção de informações é sempre aplicada por um administrador, nunca um utilizador final. E é aplicado ao nível de lista ou biblioteca para todos os documentos no contentor, em vez de em ficheiros individuais.  Se utilizar o SharePoint Online, os utilizadores também podem aplicar a IRM a respetiva biblioteca do OneDrive para empresas.

O serviço de IRM primeiro tem de estar ativado para o SharePoint. Em seguida, especificar Information Rights Management para uma biblioteca. No caso do SharePoint Online e OneDrive para empresas, os utilizadores também podem especificar Information Rights Management para a respetiva biblioteca do OneDrive para empresas. SharePoint não utiliza modelos de política de direitos, apesar de existirem definições de configuração de SharePoint, pode selecionar que estreitamente correspondem às definições que pode ser especificado nos modelos.

Se utilizar o SharePoint Server, pode utilizar as funcionalidades de proteção de informações com [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] ao implementar o conector de RMS, que age como um reencaminhamento entre os servidores no local e o serviço de nuvem do RMS. Para obter mais informações, consulte o artigo [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações ao utilizar IRM com o SharePoint:
> 
> -   Não é possível utilizar a predefinição ou modelos personalizados que gerir no portal do Azure.
> -   Ficheiros que tenham um. Extensão de nome de ficheiro PPDF para ficheiros PDF protegidos não são suportadas. Ficheiros que tenham. Extensão de nome de ficheiro PDF e que foi protegido nativamente pelo RMS são suportadas quando utiliza um leitor de PDF que suporta nativamente o RMS.
> -   Uma vez que o Office em dispositivos móveis ainda não suporte RMS, estes dispositivos têm de utilizar um browser para ver os ficheiros que foram protegidos com o RMS e os ficheiros são só de leitura.

Azure RMS aplica restrições de utilização e a encriptação de dados para os documentos quando serem transferidas a partir do SharePoint e não quando o documento é o primeiro criado no SharePoint ou carregado para a biblioteca. Para obter informações sobre como os documentos estão protegidos antes de serem transferidas, consulte o artigo [encriptação de dados no OneDrive para empresas e no SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) da documentação do SharePoint.

Para obter mais informações sobre como utilizar o Azure RMS com o SharePoint, consulte a seguinte mensagem de blogue do Office: [O que há de novo com gestão de direitos de informação no SharePoint e no SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Servidores de ficheiros que executam o Windows Server e utilizam a infraestrutura de classificação de ficheiros (FCI)
Quando configura o Windows Server para utilizar a infraestrutura de classificação de ficheiros, esta funcionalidade do Gestor de recursos do servidor de ficheiros pode analisar ficheiros locais e determinar se contiverem dados sensíveis. Para ficheiros que satisfaçam estes critérios, são etiquetados com propriedades de classificação que define um administrador. A infraestrutura de classificação de ficheiros, em seguida, pode demorar uma ação automática, de acordo com a classificação. Uma destas ações incluem aplicar proteção de informação utilizando [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] e a implementação do conector de gestão de direitos (também conhecido como o conector do RMS). Ficheiros do Office, em seguida, são automaticamente protegidos pelo Azure RMS.

Para proteger todos os tipos de ficheiro, que seria não utilizar o conector de RMS, mas em vez disso, executar um script do Windows PowerShell, utilizando os cmdlets do [ferramenta de proteção RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

As políticas de classificação são totalmente configurável e altamente extensível para que podem impedir potenciais fuga de dados dos utilizadores não autorizados e autorizados. Ainda pode ajudar a reduzir o risco de fuga de dados por administradores de rede porque pode configurar as políticas que não requerem estes administradores ter acesso aos ficheiros.

Para obter instruções para implementar e configurar o conector do RMS para ficheiros do Office, consulte o artigo [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Para obter instruções para utilizar o script do Windows PowerShell para todos os tipos de ficheiros, consulte o artigo [Proteção RMS com infraestrutura de classificação de ficheiros &#40;FCI&#41; do Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Outras aplicações que suportam as APIs de RMS
Ao utilizar o SDK RMS, os programadores internos podem escrever as aplicações de linha de negócio para suportar nativamente [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Como a proteção de informações é integrada com estas aplicações depende da forma como são escritos. Por exemplo, a integração poderá ser automaticamente aplicada interação do utilizador mínima necessária ou para uma experiência mais personalizada, os utilizadores poderão ser-lhe configurar definições para aplicar proteção de informações a ficheiros. Para mais informações sobre o SDK, consulte o [SDK de gestão de direitos do Microsoft](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Da mesma forma, muitos fornecedores de software fornecem aplicações para fornecer informações soluções de proteção, também conhecido como direitos (ERM) produtos de gestão empresarial. Um exemplo popular é um leitor de PDF que suporte [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para plataformas específicas. Pode utilizar a tabela a [Capacidades do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico para identificar as aplicações que suportam RMS (aplicações suportadas por RMS) e, em seguida, utilize uma pesquisa web para comprar ou transferir a aplicação.

> [!TIP]
> Para aplicações publicadas recentemente, verifique os canais de Comunidade de RMS, listados na [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Consultar Também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

