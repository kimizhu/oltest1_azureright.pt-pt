---
description: na
keywords: na
title: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
---
# Ajudar os utilizadores a proteger ficheiros utilizando o Azure Rights Management
Após ter implementado e configurado Azure Rights Management (RMS do Azure) para a sua organização, fornece ajuda e orientação para utilizadores, os administradores e o suporte técnico:

-   **Informações do utilizador final:**

    Permitir que os utilizadores saber como e quando proteger documentos e e-mails que contêm informações confidenciais. Sempre que possível, fornecem estas informações para os seus fluxos de trabalho existente para que estes podem incorporar os passos adicionais para um processo já familiar em vez de introdução ao completamente novos processos. Certifique-se de que diga-lhes os benefícios (e os riscos) que são específicas para a sua empresa, bem como fornecer orientações para quando deve proteger ficheiros e mensagens de correio eletrónico. Se tiver configurado [modelos personalizados](http://technet.microsoft.com/library/dn642472.aspx), fornecer instruções sobre a qual um-para-Selecione se o nome do modelo e a descrição não é suficiente para os mesmos escolher correto.

    > [!TIP]
    > Vídeos de exemplo para os utilizadores finais:
    > 
    > -   [Experiência de utilizador do Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Controlo de documento do Azure RMS e de revogação.](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informações de administrador:**

    Algumas aplicações aplicam automaticamente a proteção de informações, utilizando as políticas e definições que configurar os administradores. Para estas aplicações, poderá ter fornecer instruções aos outros administradores que gerem estas aplicações e serviços. Para obter mais informações, consulte o artigo [Como as aplicações suportam gestão de direitos do Azure](../Topic/How_Applications_Support_Azure_Rights_Management.md) e [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

-   **Informações de suporte técnico de ajuda:**

    Uma das ferramentas mais úteis para o suporte técnico está a [RMS analisador](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   Operadores de suporte técnico de ajuda podem executá-lo com a opção de administrador do Azure RMS e podem pedir aos utilizadores para executarem-lo com a opção de utilizador do Azure RMS. Esta ferramenta pode ajudar a identificar problemas não só, mas também corrigir problemas que encontra e, se ainda não corrigido, os registos de rastreio de registo.

    Se existirem pedidos legítimos para ter acesso completo direitos documentos protegidos, por exemplo um pedido efetuado pelo Departamento jurídico ou um gestor depois de um empregado saiu da organização, certifique-se do suporte técnico tem processos para este pedido utilizando o Azure RMS [funcionalidade de utilizador super](https://technet.microsoft.com/en-us/library/mt147272.aspx).

    Além disso, estes são alguns dos problemas típicos que os utilizadores poderão relatório:

    -   **Ajuda de início de sessão:**

        Os utilizadores poderão ser pedidos de credenciais quando o Azure RMS tem de autenticar um utilizador e não podem utilizar credenciais em cache. Este será o utilizador trabalho ou escola da conta e palavra-passe que está associado ao seu inquilino do Office 365 ou o inquilino do Azure Active Directory. Este não é uma conta Microsoft (anteriormente Microsoft Live ID) ou a respetiva conta de e-mail pessoal, porque estes não são atualmente suportadas pelo Azure RMS. Fornece aos utilizadores e o suporte técnico com instruções sobre a conta a utilizar quando os utilizadores recebem o pedido de credenciais quando estiverem a utilizar estas aplicações com o Azure RMS.

    -   **Problemas de proteção ou consumir conteúdos:**

        Certifique-se de que os utilizadores têm as instruções adequadas para as aplicações que utilizar e, está a utilizar aplicações e dispositivos que são suportados pelo Azure RMS. Para mais informações sobre dispositivos e aplicações suportadas, consulte o artigo [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

        Se os utilizadores veem um erro ao tentar proteger ou consumir conteúdos, peça-lhes para executar o [RMS analisador](https://www.microsoft.com/en-us/download/details.aspx?id=46437) como um utilizador do Azure RMS.

        Se os utilizadores de relatórios que pode abrir o conteúdo protegido, mas não tem os direitos que necessitam, peça-lhes para executar o [RMS analisador](https://www.microsoft.com/en-us/download/details.aspx?id=46437) como um utilizador do Azure RMS e transferir e visualizar os modelos. Isto confirma que estes têm transferidos com êxito os modelos e que direitos os modelos fornecem. O problema poderá ser que o utilizador não está no grupo de correto que esteja configurado para o modelo ou que o modelo tem de reconfigurar para o utilizador.

Utilize as secções seguintes para obter informações específicas de aplicações para ajudar os utilizadores proteger documentos confidenciais e mensagens de correio eletrónico.

## Utilizar a proteção de informações com a aplicação de partilha Rights Management
A gestão de direitos (RMS) aplicação de partilha é necessário para utilizadores que pretende proteger e consumir conteúdo protegido se utilizarem o Office 2010, mas também recomendado para todos os computadores e dispositivos móveis que suportam o Azure RMS.

Para além de tornar mais fácil para os utilizadores proteger documentos importantes, a aplicação de partilha RMS permite aos utilizadores controlar os documentos que estão protegidos e, se necessário, revogar o acesso aos mesmos.

Para obter instruções utilizar esta aplicação para computadores Windows, consulte o [Guia de utilizador de aplicação partilha Rights Management](http://technet.microsoft.com/library/dn339006.aspx).

Para dispositivos móveis, consulte o [FAQ para o aplicação de partilha do Microsoft Rights Management para plataformas móveis](http://technet.microsoft.com/dn451248).

> [!TIP]
> Para um cenário de exemplo de alto nível com capturas de ecrã, consulte o [Os utilizadores partilham de forma segura anexos com utilizadores móveis](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_SharingApp) secção a [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tópico.

## Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013
Se estiver a utilizar o Azure RMS e não instalou a aplicação de partilha Rights Management, os utilizadores não verão o **partilhar protegido** botão no Friso ou **proteger no local** do Explorador de ficheiros que torna mais fácil para os mesmos proteger ficheiros. Para estes utilizadores, tem de seguir as instruções semelhantes às funções.

> [!TIP]
> Para encontrar ajuda específicas de aplicações e instruções para utilizar a proteção de informações com estas aplicações, procure **IRM** e o nome da aplicação e a versão.

#### Para proteger um documento no Word 2013

1.  No Microsoft Word, crie um novo documento.

2.  A partir do **ficheiro** menu, clique em **informações**, clique em **Proteger documento**, clique em **restringir acesso**, e, em seguida, selecione um modelo para aplicar os direitos de utilização adequada, ou rapidamente selecione **restringir acesso** e selecione os direitos de utilização-la sozinho.

    > [!NOTE]
    > Se esta for a primeira vez que utiliza o Rights Management, irá contactar o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] de serviço e será serão pedidas credenciais configurar o cliente de IRM do Office.

3.  Guarde o documento.

Quando outras pessoas abrir o documento, primeiro são autenticados. Se não estão autorizados para abrir o documento, o documento não for aberto. Se estes estão autorizados a abrir o documento, abre-se com os direitos de utilização restrito que foram especificados para esse utilizador. Por exemplo, uma utilização para a direita da ver apenas não permitir que o utilizador editar ou guardar o documento, mesmo que o primeiro é copiado para outra localização. Os direitos de utilização são apresentados na parte superior do documento, utilizando uma faixa de restrição. A faixa pode mostrar as permissões que são aplicadas ao documento, ou pode disponibilizar uma ligação para mostrá-las.

#### Para proteger uma mensagem de correio eletrónico através do Outlook 2013 e no Exchange Online

1.  No Outlook, crie uma nova mensagem de correio eletrónico endereçada ao destinatário dentro da sua organização.

2.  A partir de **opções** separador, clique em **permissão**, e, em seguida, selecione uma opção. Por exemplo: **Não reencaminhar**, **&lt; nome da empresa &gt; - confidencial** ou **&lt; nome da empresa &gt; - apenas visualização confidencial**.

3.  Envie a mensagem.

Da mesma forma para visualizar um documento protegido, quando os destinatários recebem a mensagem de correio eletrónico, se são primeiro autenticados. Se o estão autorizados a ver a mensagem de correio eletrónico, abre-se com os direitos de utilização restrito que foram especificados para esse utilizador. Por exemplo, se tiver selecionado **não reencaminhar**, o botão no Friso reencaminhar não está disponível.

#### Para proteger uma mensagem de correio eletrónico utilizando o Outlook Web App

1.  No Outlook Web App, crie uma nova mensagem de correio eletrónico endereçada ao destinatário dentro da sua organização.

2.  Clique em  **…**,  clique em **definir permissões**, e, em seguida, selecione uma opção. Por exemplo: **Não reencaminhar**, **não responder a todos**, **&lt; nome da empresa &gt; - confidencial** ou **&lt; nome da empresa &gt; - apenas visualização confidencial**.

3.  Envie a mensagem.

Da mesma forma para visualizar um documento protegido, quando os destinatários recebem a mensagem de correio eletrónico, se são primeiro autenticados. Se o estão autorizados a ver a mensagem de correio eletrónico, abre-se com os direitos de utilização restrito que foram especificados para esse utilizador. Por exemplo, se tiver selecionado **fazer não responder a todos**, a **RESPONDER a todos** opção na janela da mensagem não está disponível.

## Consultar Também
[Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

