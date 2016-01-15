---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# RMS para indiv&#237;duos e Azure Rights Management
RMS para indivíduos é uma subscrição gratuita self-service para utilizadores numa organização ter sido enviado ficheiros confidenciais que foram protegidos pelo Microsoft Azure Rights Management (RMS) do Azure, mas não pode ser autenticadas porque o respetivo departamento de TI não gerir uma conta para os mesmos no Azure. Por exemplo, o departamento de TI não ter o Office 365 ou utilizar os serviços do Azure.

Estes utilizadores podem inscrever-se um livre conta escolar ou profissional para utilizar com o Azure RMS e transferir e instalar a aplicação de partilha Rights Management. Como resultado, estes utilizadores agora podem autenticar para provar que estão a pessoa que os ficheiros protegidos foram enviados para a e, em seguida, ler os ficheiros protegidos em computadores ou dispositivos móveis.

Utilizar a aplicação em computadores Windows de partilha Rights Management, estes utilizadores podem também proteger ficheiros no local ou enviar ficheiros protegidos por correio eletrónico para as pessoas dentro ou fora da sua organização. Se os destinatários da mensagem de correio eletrónico enviarem são numa organização que também não gerir contas de utilizador no Azure, eles também podem inscrever-se um RMS para a conta de indivíduos para ler o anexo de e-mail protegido.

> [!IMPORTANT]
> Esta subscrição gratuita assegura que as pessoas autorizadas podem sempre ler ficheiros que foram protegidos. Atualmente, também pode utilizar esta subscrição gratuita para proteger os documentos e criar novas mensagens de e-mail protegido, mas a capacidade de criar o novo conteúdo protegido destina-se a versão de avaliação apenas para utilização e poderá ser removida no futuro. Para obter mais informações e as alterações efetuadas ao utilizar RMS para utilizadores para proteger conteúdo, consulte o [direitos termos de serviço de gestão Microsoft](https://portal.aadrm.com/Legal/Service).

Para mais informações sobre como pode proteger ficheiros utilizando a aplicação de partilha Rights Management livre, consulte o [Guia aplicação de partilha do Rights Management para utilizadores](http://technet.microsoft.com/library/dn339006.aspx).

RMS para indivíduos é um exemplo de uma inscrição self-service que é suportado pelo Azure Active Directory. Para mais informações sobre como isto funciona, consulte o artigo [What ' s inscrição Self-Service para o Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) na documentação do Microsoft Azure. Utilize as secções seguintes para obter mais informações que é específicas de RMS para indivíduos:

-   [Como os utilizadores inscrever-se no RMS para indivíduos](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [Descrição geral técnica](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [Como saber se os seus utilizadores tenham inscreveu no RMS para indivíduos](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>Como os utilizadores inscrever-se no RMS para indivíduos
Para se inscrever para esta conta livre, solicitá-la, visitando o [página Microsoft Rights Management](https://portal.aadrm.com/), e forneça o seu trabalho profissional ou escolar do endereço de correio eletrónico. A forma mais habituais que será direcionado para esta página de inscrição é se recebeu uma mensagem de correio eletrónico com um anexo protegido, que contém instruções de como a inscrição. Irá receber uma mensagem de e-mail em resposta da Microsoft e, em seguida, pode concluir o processo de inscrição introduzindo detalhes para criar a sua conta. Quando receber uma confirmação de correio eletrónico da Microsoft, esta mensagem de correio eletrónico finais envia-lhe a uma página onde pode transferir a aplicação de partilha para diferentes dispositivos e uma ligação para o Guia do utilizador.

#### Para inscrever-se no RMS para indivíduos

1.  Utilizar um computador Windows ou Mac, vá para o [página Microsoft Rights Management](https://portal.aadrm.com).

2.  Escreva o endereço de e-mail que utiliza para a sua organização, tal como **janetm@contoso.com** ou **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Contas de e-mail pessoais não são suportadas, por isso, não introduza uma conta Microsoft (anteriormente conhecido como uma conta Microsoft Live ID) ou outra conta pessoal que poderá utilizar em casa através do seu fornecedor de Internet.

3.  Clique em **começar**.

    A Microsoft utiliza o seu endereço de e-mail para verificar se a sua organização já tiver um [pago a subscrição que inclui o Azure RMS](https://technet.microsoft.com/library/dn655136.aspx). Se for esse o caso, não precisa de RMS para indivíduos, de modo a irá ter a sessão iniciada imediatamente e a self-service de inscrição para o RMS para indivíduos é cancelada. Se não for encontrada uma subscrição paga do Azure RMS, irá continuar para o passo seguinte.

4.  Aguarde que uma mensagem de correio eletrónico de confirmação para serem enviados para o endereço que especificou. Esta irá ser da Microsoft (DoNotReply@microsoft.com) e com o assunto **Microsoft RMS**.

5.  Quando recebe o e-mail, clique na ligação nas instruções para concluir a processo de inscrição.

6.  A ligação direcionado um novo **Microsoft Rights Management** página para lhe fornecer os detalhes da sua conta. Escreva o nome do seu próprio, o último nome, introduza e confirme uma palavra-passe da sua escolha, selecione o seu país/região (ou o país/região mais próximo à sua se o seu país/região não estiver listado) a partir da lista pendente e, em seguida, clique em **criar**.

7.  Aguarde que de outra mensagem de correio eletrónico da Microsoft que agora confirma que a sua conta está pronta a ser utilizado.

8.  Quando recebe o e-mail, clique na ligação para iniciar sessão e leia as instruções para transferir e instalar a aplicação de partilha ou clique na ligação de ajuda para ler o guia de utilizador da aplicação de partilha.

Agora a sua conta estiver criada, está pronto para começar a proteger ficheiros e ler ficheiros que outras pessoas protegidos. Quando lhe for pedido para iniciar sessão proteger ou ler ficheiros protegidos, introduza o seu endereço de correio eletrónico e palavra-passe que utilizou para criar a conta para RMS para indivíduos.

### <a name="BKMK_TechnicalOverview"></a>Descrição geral técnica
RMS para indivíduos utiliza uma inscrição processo também é utilizado por outros serviços que utilizam a tecnologia de baseado na nuvem da Microsoft para autenticar os utilizadores self-service.

Este é o que acontece em segundo plano quando um utilizador se inscreve para RMS para indivíduos e respetiva organização não tiver uma subscrição do Office 365 ou subscrição do Azure e, por conseguinte, nenhum diretório no Azure para autenticar os utilizadores:

1.  Quando o primeiro utilizador a partir de uma organização solicita uma subscrição para o RMS para indivíduos, o nome de domínio fornecido no respetivo endereço de e-mail é verificado para ver se já estiver associado um inquilino do Azure. Se não existir nenhum inquilino existente, um novo inquilino e o diretório do Azure é criado automaticamente na organização, que contém uma conta para este utilizador primeiro. Ao contrário com uma subscrição paga do Azure, esta conta primeiro não é um administrador global, mas o utilizador normal. A nova conta utiliza o endereço de correio eletrónico e palavra-passe que o fornecido pelo utilizador.

    > [!NOTE]
    > Alguns nomes de domínio não podem ser utilizados para criar o diretório e, por conseguinte, não podem ser utilizados para o RMS para indivíduos. A lista de nomes de domínios bloqueados, pode ser visualizada a partir deste ficheiro JavaScript Object Notation: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Se for encontrado um inquilino existente, este é verificado para ver se já tem uma subscrição para o Azure RMS. Quando não é encontrada nenhuma subscrição, o RMS gratuita para a subscrição de indivíduos podem ser adicionados.

2.  A organização é concedida o RMS para a subscrição de indivíduos. Agora, este utilizador possa ser autenticado pelo Azure e pode, em seguida, proteja os ficheiros e ler ficheiros que outras pessoas protegidos utilizando o Azure Rights Management. Para proteger e ler ficheiros protegidos, o utilizador tem de ter uma aplicação suportadas por RMS, como gratuita [aplicação de partilha Rights Management](https://technet.microsoft.com/library/dn919648.aspx).

3.  Quando o segundo utilizador a partir da mesma empresa solicita a um RMS para a subscrição de indivíduos, uma nova conta de utilizador é adicionada ao diretório Azure criado anteriormente, utilizando o RMS da sua organização para a subscrição de indivíduos. Este segundo utilizador pode fazer tudo o que pode efetuar o primeiro utilizador (proteger ficheiros e ler ficheiros protegidos), mas além disso, estes dois utilizadores agora podem mais facilmente colaborarem com segurança uma vez que podem aplicar rapidamente modelos predefinidos para ficheiros que restringir o acesso a contas no diretório do Azure da sua organização.

4.  Utilizadores subsequentes do mesmo organização siga o mesmo padrão, adicionar contas de utilizador (quando a novos utilizadores inscrever-se) para o diretório Azure da sua organização. Mais contas que são adicionadas para o diretório, os utilizadores mais segura podem colaborar com colegas e parceiros e mais facilmente impedem que pessoas não autorizadas ler os seus ficheiros quando que não devem ter acesso aos mesmos.

Durante este processo, não existe nenhum gratuitas para a organização e qualquer trabalho necessário a partir do departamento de TI. No entanto, o departamento de TI pode optar por efetue um dos seguintes procedimentos:

-   **Gerir as contas e o processo de inscrição**: Os administradores de TI podem obter a propriedade das contas e diretório criado automaticamente no Azure. Em seguida, que podem gerir as contas através da implementação de soluções de integração de diretório como o início de sessão único e sincronização de palavra-passe. Em alternativa, pode impedir os utilizadores a partir de criação de contas ou inscrever-se para o RMS para indivíduos.

    Para mais informações, consulte a secção seguinte, [Como os administradores podem controlar as contas criadas para o RMS para indivíduos](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts).

-   **Gerir o Rights Management**: Os administradores de TI podem converter o RMS para a subscrição de indivíduos da organização para uma subscrição paga que inclui o Azure Rights Management. Quando para tal, as contas e de diretório do Azure existente são preservadas para uma transição totalmente integrada para utilizadores existentes que estava a usar o RMS para indivíduos. Quaisquer ficheiros que os utilizadores protegidos anteriormente serão ainda protegidos com as mesmas políticas e as pessoas que são concedidas permissões para utilizar os ficheiros poderão continuar a utilizar os ficheiros da mesma forma.

    Quando realize este curso de ação, os benefícios da sua organização pelo facto de ser capaz de integrar o Rights Management dos seus fluxos de trabalho, serviços e os arquivos de dados. Além disso, já pode gerir Rights Management porque têm controlo sobre a chave de inquilino da sua organização para o Azure Rights Management. Pode efetuar o seguinte:

    -   Configure o Exchange e SharePoint para suportar a gestão de direitos do Azure, mesmo que estas estão em execução no local. Exchange e SharePoint nativamente são suportados para os serviços online, e são suportados por um conector para os servidores no local. Para mais informações, consulte o seguinte:

        -   As secções de Exchange Online e no SharePoint Online a partir de [Office 365: Configuração para os clientes e serviços online](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365) no [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) tópico

        -   [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   Efetue a deteção de i nos dados pertencentes à empresa, de modo a que o pode, se necessário, desencriptar ficheiros que foram protegidos utilizando a gestão de direitos. Para obter mais informações, consulte o artigo [Configurar utilizadores Super para o Azure Rights Management e os serviços de deteção ou recuperação de dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

    -   Inicie a toda a atividade para a gestão de direitos, como utilizadas na sua organização. Isto é muito poderoso porque não só pode monitorizar os ficheiros que estão a ser protegidos e o que está a aceder com sucesso esses ficheiros protegidos, mas também podem identificar comportamento suspeito potencialmente de pessoas não autorizadas que estão a tentar aceder a ficheiros protegidos. Para obter mais informações, consulte o artigo [Registo e analisar a utilização de gestão de direitos do Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

    -   Fornecer aos utilizadores a capacidade de monitorizar e revogar os seus documentos protegidos, se estas funcionalidades são suportadas pelo seu [subscrição do Azure RMS](https://technet.microsoft.com/dn858608). Para obter mais informações, consulte o artigo  [monitorizar e revogar os seus ficheiros](https://technet.microsoft.com/library/dn986611.aspx) a partir de [Guia de utilizador de aplicação partilha do RMS](https://technet.microsoft.com/library/dn339006.aspx).

    -   Implemente uma traga a sua própria solução chave (BYOK) para que a chave de inquilino do Azure Rights Management é gerado no local, de acordo com as políticas de TI e segura transferidas para a Microsoft através da utilização de um módulo de segurança de Hardware (HSM). Para obter mais informações, consulte o artigo [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## <a name="BKMK_TakeControlofAccounts"></a>Como os administradores podem controlar as contas criadas para o RMS para indivíduos
Se não pretender converter RMS da sua organização para a subscrição de indivíduos para uma subscrição paga, ainda pode controlar as contas de utilizador no diretório do Azure que tenha sido criada para a sua organização das seguintes formas:

-   Implementar soluções de integração de diretório do Azure Active Directory e a sua infraestrutura de serviços de domínio do Active Directory. Pode sincronizar as contas e palavras-passe para que os utilizadores não terá de criar novas contas para utilizar a gestão de direitos e as políticas de palavra-passe no local serão aplicadas as novas contas de utilizador do Azure. Também pode sincronizar as palavras-passe para que os utilizadores não têm de lembrar-se uma palavra-passe diferente para utilizar a gestão de direitos.

-   Pode impedir que os utilizadores inscrever-se utilizar o Azure Rights Management com o RMS para a subscrição de indivíduos. Na maioria dos casos, há pouca partido no fazê-lo uma vez que os utilizadores irão pode partilhar ficheiros sem proteção (que foi possível colocar a sua empresa em risco) ou utilizarão outro mecanismo de proteção de ficheiros que não fornece o departamento de TI com a opção para aceder aos dados. No entanto, se pretender impedir que os utilizadores inscrever-se utilizar RMS para indivíduos, efetue um dos seguintes a depois de tomar as propriedade de diretório da sua organização no Azure:

    -   Impedi que todos os utilizadores inscrever-se para subscrições de self-service, que inclui o RMS para indivíduos.  Atualmente, não é possível configurar esta opção pelo serviço; a definição aplica-se a todas as subscrições do Azure que utilizam o processo de self-service. Para tal, defina o **AllowAdHocSubscriptions** parâmetro como false com o [conjunto MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet do módulo do Windows PowerShell para o Azure Active Directory. Por exemplo: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Impedir que os utilizadores a criar uma nova conta no Azure, o que significa que apenas os utilizadores que já tem uma conta no Azure podem inscrever-se subscrições self-service, que inclui o RMS para indivíduos.  Para tal, defina o **AllowEmailVerifiedUsers** parâmetro como false com o [conjunto MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet do módulo do Windows PowerShell para o Azure Active Directory. Por exemplo: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Sincronize a sua infraestrutura de serviços de domínio do Active Directory com o Azure Active Directory. Esta ação impede que novas contas de que está a ser criada quando os utilizadores inscrever-se para subscrições de self-service, tais como RMS para indivíduos e pode eliminar ou desativar a contas que foram anteriormente criadas no diretório do Azure.

Para controlar as contas de utilizador no diretório do Azure, ou para impedir que os utilizadores inscrever-se para o RMS para indivíduos, tem de ter uma subscrição do Azure e o diretório o proprietário. Se ainda não tiver uma subscrição do Azure, pode obter um aspeto sem gratuitas. Se um diretório foi criado automaticamente durante o processo de self-service, obter propriedade do domínio que tenha sido utilizado para criá-la. Se já possui um diretório no Azure, mas os utilizadores especificados um novo domínio que utiliza na sua organização, intercale nesse domínio seu diretório existente. Para mais informações, consulte as instruções em [What ' s inscrição Self-Service para o Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)

## <a name="BKMK_Detect"></a>Como saber se os seus utilizadores tenham inscreveu no RMS para indivíduos
Como administrador, como saber se os seus utilizadores tenham inscreveu no RMS para indivíduos? Pode utilizar quaisquer ou uma combinação dos seguintes métodos:

-   Peça aos utilizadores como protegem ficheiros altamente confidenciais, especialmente quando colaborar com outras pessoas fora da organização.

-   Quando tiver uma subscrição do Azure para a sua organização, utilize o [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) cmdlet para ver se **RIGHTSMANAGEMENT_ADHOC** é devolvido como uma das subscrições. Se estiver, este é o RMS para a subscrição de indivíduos que foi concedido para a organização, com um conjunto de Active Directory unidades disponíveis para utilizar o processo de inscrição de self-service pelos utilizadores.

-   Utilize uma sistema solução de gestão, como o System Center Configuration Manager, para o software de inventário instalado e de software em utilização. A aplicação de partilha Rights Management é executada através de **ipviewer.exe** programa e pode [Transferir e instalar a aplicação](http://go.microsoft.com/fwlink/?LinkId=303970) gratuitamente para identificar outras características sobre esta aplicação que utiliza, em seguida, inventário de software.

-   Ter o atento extensões de nome de ficheiro que são criados pela aplicação de partilha Rights Management. As extensões de nome de ficheiro. pfile e. ppdf são os exemplos mais óbvias, mas existem outros ficheiros que alterar as respetivas extensão de nome de ficheiro quando estes estão protegidos nativamente pela Rights Management. Para obter mais informações, consulte o [tipos de ficheiros e extensões de nome de ficheiro suportados](http://technet.microsoft.com/library/dn339003.aspx) secção a [Guia do administrador aplicação partilha Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

## Consultar Também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

