---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Perguntas mais frequentes do Azure Rights Management
Algumas perguntas mais frequentes do Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], também conhecido como o Azure RMS:

## O que é necessário implementar o Azure RMS e como posso começar a utilizar?
Primeiro, verifique o [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md), que tem informações sobre as opções de subscrição na nuvem, como pode utilizar os servidores no local com o Azure RMS, os cenários de implementação atualmente não são suportadas, quais os dispositivos e aplicações de suporte do Azure RMS e uma ligação se precisar de uma lista de endereços IP e nomes de domínio para firewalls ou servidores proxy. Pode também querer verificar os outros tópicos [Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) secção, para obter uma compreensão básica de como [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pode ajudar a proteger os dados da organização, como é funciona com aplicações, como se compara com a versão no local do Active Directory Rights Management e compreender os termos e as abreviaturas que são específicas para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Em seguida, quando estiver pronto para testar o Azure RMS sozinho ou implementá-lo para a sua organização, utilize o [Plano de implementação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para obter uma lista dos passos com ligações para obter mais instruções de informações e procedimentos.

Se precisar de informações adicionais, recursos e opções de suporte, consulte o artigo [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Pode integrar Azure RMS com a minha servidores no local?
Sim. Azure RMS pode ser integrado com os servidores no local, tais como servidores de ficheiros do Exchange Server, o SharePoint e o Windows. Para tal, utilize o [conector da gestão de direitos](https://technet.microsoft.com/library/dn375964.aspx). Ou, se estiver apenas interessado em utilizar a infraestrutura de classificação de ficheiros (FC) com o Windows Server, pode utilizar o [proteção RMS cmdlets](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Também pode sincronizar e federar controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais estável para utilizadores, por exemplo, utilizando [o Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS automaticamente gera e gere XrML certificados conforme necessário, pelo que não utiliza um PKI no local. Para obter mais informações sobre como o Azure RMS utiliza certificados, consulte o [Instruções de como funciona o Azure RMS: Utilizar pela primeira vez, a proteção, o consumo de conteúdo de conteúdo](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) secção a [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tópico.

## Tenho de ter uma implementação híbrida do Exchange com alguns utilizadores no Exchange Online e outros no servidor Exchange — é suportado pelo Azure RMS?
Tal for absolutamente e uma vantagem é, os utilizadores irão ser capazes de forma totalmente integrada proteger e consumir protegidas mensagens de correio eletrónico e anexos entre as duas implementações do Exchange. Para esta configuração, [Ativar o Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) e [ativarem a IRM para o Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), em seguida, [Implementar e configurar o conector de RMS](https://technet.microsoft.com/library/dn375964.aspx) para o Exchange Server.

## Se implementar o Azure RMS em produção, é a minha empresa, em seguida, bloqueada para o risco de perda de acesso a conteúdo que foi protegidos com o Azure RMS ou solução?
Não, pode sempre permanece no controlo dos seus dados e pode continuar a aceder ao mesmo, mesmo se optar por já não utilizam o Azure RMS. Para obter mais informações, consulte o artigo [Desativação e a desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

No entanto, antes de encerrar a implementação do Azure RMS, gostaríamos de ouvir do utilizador e a compreender por que motivo que efetuou esta decisão. Se o Azure RMS não cumprir os requisitos de negócio, verifique connosco no caso de novas funcionalidades for planeada para o próximo-futuro ou se existirem alternativas. Enviar uma mensagem de correio eletrónico para [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) e iremos estará Feliz discutir os requisitos técnicos e empresariais.

## Posso controlar qual dos meus utilizadores pode utilizar o Azure RMS para proteger conteúdo?
Sim, o Azure RMS tem controlos de integração do utilizador para este cenário. Para obter mais informações, consulte o [Configurar os controlos de integração para uma implementação faseada](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) secção a [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tópico.

## Pode impedir os utilizadores a partir de partilha de documentos protegidos com organizações específicas?
Uma das maiores vantagens do Azure RMS é que suporta a colaboração de negócio para empresas sem precisar de o ter de configurar confianças explícitas para a organização de cada parceiro, porque o Azure AD toma conta de autenticação por si.

Não existe nenhuma opção de administração para impedir os utilizadores de forma segura a partilhar documentos com organizações específicas. Por exemplo, pretende bloquear uma organização que não fidedignas ou que tenha uma empresa concorrente. Impedir que o Azure RMS enviar documentos protegidos aos utilizadores destes organizações não faz sentido porque os seus utilizadores, em seguida, iriam partilhar os seus documentos desprotegidos, que é provável que a última coisa que pretende que aconteça neste cenário! Por exemplo, não conseguirão identificar quem está a partilhar documentos confidencial da empresa com os utilizadores que estes organizações, o que pode fazer quando o documento (ou o correio eletrónico) está protegido pelo Azure RMS.

## Quando partilhar um documento protegido com alguém fora da minha empresa, como esse utilizador obter autenticado?
Azure RMS utiliza sempre uma conta do Azure Active Directory e um endereço de e-mail associado para autenticação de utilizador, que torna a colaboração de negócio para empresas totalmente integrada para administradores. Se a outra organização utiliza os serviços do Azure, os utilizadores terão contas já no Azure Active Directory, mesmo que estas contas são criadas e geridos no local e, em seguida, são sincronizados para o Azure.  Se a organização tiver o Office 365, sob o abrange, este serviço utiliza também do Azure Active Directory para as contas de utilizador.  Se a organização do utilizador não tiver contas geridas no Azure, os utilizadores podem inscrever-se no [RMS para indivíduos](https://technet.microsoft.com/library/dn592127.aspx), que cria um inquilino Azure não gerido e de diretório da organização com uma conta para o utilizador, para que este utilizador, em seguida, pode ser autenticado para o Azure RMS.

O método de autenticação para estas contas pode variar, consoante a forma como o administrador na outra organização tiver configurado as contas do Azure Active Directory. Por exemplo, eles podem utilizar palavras-passe que foram criadas para estas contas, a autenticação multifator (MFA), Federação ou palavras-passe que foram criadas nos serviços de domínio do Active Directory e, em seguida, sincronizadas com o Azure Active Directory.

## Posso adicionar utilizadores a partir de fora da minha empresa para modelos personalizados?
Sim.  Criar modelos personalizados que os utilizadores finais (e os administradores), podem selecionar a partir de aplicações torna a rápida e facilmente para os mesmos aplicar a proteção de informações, utilizando as políticas predefinidas que especificar. Uma das definições no modelo é quem é capaz de aceder ao conteúdo e pode especificar os utilizadores e grupos a partir da sua organização e utilizadores a partir de fora da sua organização.

Para especificar os utilizadores a partir de fora da sua organização, utilize o [módulo do Windows PowerShell para o Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx). Pode utilizar uma destas opções:

-   **Exportação, edite e importar o modelo atualizado**:  Este é o método mais simples se pretender adicionar estes utilizadores externos a um modelo existente que inclui a outros grupos. Utilize o [exportação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet para exportar o modelo a um. Ficheiro CSV que podem ser editados para adicionar os endereços de e-mail externo destes utilizadores e os respetivos direitos sobre os grupos existentes e direitos. Em seguida, utilize o [importação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) cmdlet para importar esta alteração de volta para o Azure RMS.

-   **Utilizar um objeto de definição de direitos para criar ou atualizar um modelo de**:    Especifica os endereços de e-mail externo e os respetivos direitos de um objeto de definição de direitos, o que, em seguida, utilizar para criar ou atualizar um modelo. Especificar o objeto de definição de direitos, utilizando o [AadrmRightsDefinition novo](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet para criar uma variável e, em seguida, fornecer esta variável para o parâmetro - RightsDefinition com o [AadrmTemplate adicionar](https://msdn.microsoft.com/library/azure/dn727075.aspx) cmdlet (para um novo modelo) ou [conjunto AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet (se estiver a modificar um modelo existente). No entanto, se estiver a adicionar estes utilizadores para um modelo existente, terá de definir os objetos de definição de direitos para os grupos existentes nos modelos e não apenas os utilizadores externos.

Para mais informações sobre modelos personalizados, consulte o artigo [Configurar modelos personalizados para o Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Que dispositivos e quais os tipos de ficheiro são suportados pelo Azure RMS?
Para obter uma lista de dispositivos suportados, consulte o [Dispositivos de cliente que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico. Uma vez, todos suportados dispositivos atualmente suportam todas as capacidades de RMS, certifique-se de que também verificar o [Capacidades do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) tabela no mesmo tópico.

Azure RMS pode suportar todos os tipos de ficheiro. Para texto, imagem, Microsoft Office (Word, Excel, PowerPoint) ficheiros, ficheiros. pdf e alguns outros tipos de ficheiro de aplicação, o Azure RMS fornece proteção nativa que inclui a encriptação e imposição de direitos (permissões). Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece encapsulamento de ficheiro e autenticação para verificar se um utilizador está autorizado a abrir o ficheiro.

Para obter uma lista de extensões de nome de ficheiro que são suportados nativamente pelo Azure RMS, consulte o [tipos de ficheiros e extensões de nome de ficheiro suportados](http://technet.microsoft.com/library/dn339003.aspx) secção a [Guia do administrador aplicação partilha Rights Management](http://technet.microsoft.com/library/dn339003.aspx). Extensões de nome de ficheiro listadas não são suportadas utilizando a aplicação que aplica automaticamente a proteção genérica a estes ficheiros de partilha RMS.

## Quando se tiver de suportar a migração a partir de AD RMS?
Inicialmente, o Azure RMS não suporta migração a partir de uma implementação no local da gestão de direitos, como o AD RMS. Mas é agora suportado.

Para obter mais informações, consulte o artigo [Migrar do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Enviámos realmente pretende utilizar BYOK com o Azure RMS, mas não aprendeu que isto não é compatível com o Exchange Online — o que é o seu conselhos?
Não lhe permitem esta limitação atual atrasar a implementação do Azure RMS. Se tiver o Exchange Online e pretende utilizar traga a sua própria chave (BYOK), recomendamos que implementa o Azure RMS no agora, o modo de gestão de chaves predefinido onde o Microsoft gera e gere a sua chave. Dessa forma, para obter todos os benefícios de proteger os ficheiros importantes e e-mails agora, com a opção para mover para BYOK mais tarde (por exemplo, quando o Exchange Online suporta BYOK).

No entanto, se as políticas da empresa exigem a utilização de um módulo de segurança de hardware (HSM) e, caso contrário, este seria bloquear a implementação do Azure RMS, outra opção é implementar o Azure RMS com BYOK agora, com a funcionalidade reduzida do RMS para o Exchange. Para obter mais informações, consulte o [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico.

## Uma funcionalidade que procuro não parecer para trabalhar com o SharePoint protegidos bibliotecas — é o suporte para o meu funcionalidade planeado?
Atualmente, documentos do SharePoint suporta RMS protegidos ao utilizar a IRM protegidos bibliotecas, que não suportam modelos personalizados, documentos, controlar e algumas funcionalidades de outras.  Para mais informações, expanda o   [SharePoint Online e OneDrive para empresas: Configuração de IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) secção a [Como as aplicações suportam gestão de direitos do Azure](../Topic/How_Applications_Support_Azure_Rights_Management.md) tópico.

Se estiver interessado numa capacidade específica que ainda não é suportada, certifique-se de que estar atento no anúncios a [blogue da equipa do RMS](http://blogs.technet.com/b/rms/).

## Como posso configurar uma unidade para empresas no SharePoint Online, para que os utilizadores podem partilhar de forma segura os seus ficheiros com pessoas dentro e fora da empresa?
Por predefinição, enquanto administrador do Office 365, não configura esta; fazer os utilizadores.

Tal como um administrador do site SharePoint ativa e configura a IRM para uma biblioteca do SharePoint que possuem, OneDrive para empresas foi concebido para utilizadores que pretende ativar e configurar a IRM para os seus próprios biblioteca do OneDrive para empresas.  No entanto, utilizando o PowerShell, pode fazê-para-los. Para obter instruções, expanda o [SharePoint Online e OneDrive para empresas: Configuração de IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)  secção a [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) artigo.

## Tem todos os sugestões e dicas para uma implementação bem sucedida do RMS?
Depois de overseeing muitas implementações e escuta dos nossos clientes, parceiros, consultores e engenheiros de suporte – das sugestões maiores que podem passar a partir da experiência do: **Design e implementar políticas de direitos simples**.

Como o Azure RMS suporta a partilha de forma segura com qualquer pessoa, pode perder ser ambitious com o seu alcance de proteção de informações. Mas estar e conservador com as políticas de direitos. Para muitas organizações, o impacto sobre o negócio maior vêm impedir fugas de dados ao aplicar o modelo de política de direitos de predefinido que restringe o acesso às pessoas na sua organização. Obviamente, pode obter muito mais granular de que se precisar de – impedir que as pessoas da impressão, etc edição. Mas manter as restrições mais granulares como a exceção para documentos que realmente precisa de segurança de alto nível e não implementar estas políticas mais restritivas em dia, mas o plano para uma abordagem mais fases.

## As funcionalidades que o podem ou não podem ser utilizado com as diferentes subscrições do Azure RMS?
Para subscrições pagas que suportam o Azure RMS (Office 365, o Azure RMS Premium e Enterprise Mobility Suite), existem algumas diferenças entre as funcionalidades de RMS que são suportadas. Para obter uma lista das mesmas, consulte o artigo [ofertas de comparação do Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

A subscrição gratuita que suporte o Azure RMS (RMS para indivíduos) suporta consumo conteúdo que foi protegido pelo Azure RMS. Para obter mais informações, consulte o artigo [RMS para indivíduos e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Onde posso obter informações técnicas sobre a subscrição do Azure RMS gratuita (RMS para indivíduos) — por exemplo, como realmente funciona, como assumir o controlo das contas e não não possível utilizar os domínios?
Encontrará as respostas a estas perguntas no [RMS para indivíduos e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) tópico.

## Como podemos recuperar o acesso aos ficheiros que foram protegidos por um empregado que ainda tem agora a organização?
Utilize a funcionalidade de utilizador super do Azure RMS, que lhe permite a utilizadores autorizados possam tem direitos de proprietário completo de todas as licenças de utilização que foram concedidas pelo inquilino de RMS da sua organização. Esta funcionalidade mesma que lhe permite índice de serviços autorizados e inspecionar os ficheiros, conforme necessário.

Para obter mais informações, consulte o artigo [Configurar utilizadores Super para o Azure Rights Management e os serviços de deteção ou recuperação de dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Gestão de direitos de impedir capturas de ecrã?
Gestão de direitos de bloquear capturas de ecrã a partir da maior parte das ferramentas de captura de ecrã frequentemente utilizadas, que podem ajudar a evitar a divulgação acidental ou negligent das informações sensíveis ou confidenciais. No entanto, existem várias formas que um utilizador pode partilhar os dados que são apresentados num ecrã e efetuar uma captura de ecrã é apenas um método. Por exemplo, um utilizador intenção partilha a informação apresentada pode tirar uma fotografia de-as utilizando os respetivos telefones de câmara, volte a escrever os dados ou simplesmente verbally reencaminham-lo a pessoa.

Conforme estes exemplos demonstram, tecnologia sozinho sempre não é possível impedir os utilizadores da partilha de dados que não deveriam. Enquanto o Rights Management pode ajudá-lo para salvaguardar os dados importantes através da utilização de autorização e políticas de utilização, esta solução de gestão de direitos de empresa deve ser utilizada com outros controlos. Por exemplo, implementar a segurança física, cuidadosamente de ecrã e monitorizar as pessoas que autorizou acesso aos dados da sua organização e investir na educação de utilizador para que os utilizadores a compreender os dados que não devem ser partilhados.

## Onde posso encontrar informações de suporte para o Azure RMS — por exemplo, legal, conformidade e SLAs?
Azure RMS suporta outros serviços e também depende de outros serviços. Se estiver à procura de informações relacionadas com o Azure RMS, mas não sobre como utilizar o serviço do Azure RMS, verifique os seguintes recursos:

**Legal e privacidade:**

-   Para obter informações de contrato do Microsoft Azure: [Contrato do Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Para obter informações de privacidade do Microsoft Azure: [Declaração de privacidade do Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Segurança, conformidade e auditoria:**

Consulte o [Os requisitos de regulamentação, conformidade e segurança](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) secção a [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tópico. Além disso:

-   Para obter certificações externas para o Azure RMS: [Centro de fidedignidade do Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   Para obter informações de certificação FIPS 140: [Tem certificação FIPS 140 validação](https://technet.microsoft.com/library/security/cc750357.aspx)

**Contratos de nível de serviço:**

-   Contrato de nível de serviço para o Azure RMS, por país/região selecionada: [Contrato de nível de serviço](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Contrato de nível de serviço do Azure Active Directory: [Contratos de nível de serviço](http://azure.microsoft.com/support/legal/sla/)

**Documentação:**

-   Site de documentação do Active Directory do Azure: [Do Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Biblioteca do Azure Active Directory: [Do Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Biblioteca do Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## O que fazer se a minha pergunta não estiver aqui?
Utilize as ligações e recursos listados na [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Além disso, existem perguntas mais frequentes concebidos para utilizadores finais:

-   [FAQ da aplicação para o Windows de partilha Rights Management](https://technet.microsoft.com/dn467883)

-   [FAQ da aplicação para plataformas móveis e Mac de partilha Rights Management](https://technet.microsoft.com/dn451248)

-   [FAQ para o controlo de documento](http://go.microsoft.com/fwlink/?LinkId=523977)

Esta página de perguntas mais frequentes será atualizada regularmente, com novas adições listadas os anúncios de atualização de documentação mensais no [equipa Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) blogue.

> [!TIP]
> Pode utilizar o [etiqueta documentos](http://blogs.technet.com/b/rms/archive/tags/docs/) no blogue, mais localizar facilmente estes anúncios de documentação.

## Consultar Também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

