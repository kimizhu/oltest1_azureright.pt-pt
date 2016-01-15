---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# Op&#231;&#245;es da caixa de di&#225;logo para a aplica&#231;&#227;o de partilha Rights Management
Utilize estas informações para ajudar a especificar as opções na aplicação de partilha RMS **Adicionar proteção** caixa de diálogo ou **partilha protegida** caixa de diálogo. Irá ver esta caixa de diálogo caixa quando [proteger um ficheiro para partilhar](http://technet.microsoft.com/library/dn574735.aspx) ou [proteger um ficheiro num local](http://technet.microsoft.com/library/dn574733.aspx) e escolhe permissões personalizadas.

> [!IMPORTANT]
> Se as opções que visualizar forem diferentes das documentadas aqui, provavelmente não tem a versão mais recente da aplicação de partilha instalada. Pode transferir a versão mais recente a partir de [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) página.
> 
> Como saber se tem a versão mais recente? Procure **aplicação de partilha Microsoft Rights Management** listada em programas e funcionalidades e verifique o número da versão correspondente. Ver e utilizar as opções da tabela, a versão deve ser, pelo menos, **1.0.1770.0**. Pode verificar o número da versão mais recente a partir da página de transferência.

Além das opções que pode escolher, poderá também ser perguntar-se:

-   [O que é o ficheiro. ppdf criado automaticamente?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [O que é a diferença entre proteção genérica e proteção incorporada (nativa)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|Opção|Descrição|
|---------|-------------|
|**UTILIZADORES**|Se já não tiver especificado um endereço de e-mail a partir do Outlook, escreva os endereços de e-mail das pessoas que pretende conseguir abrir o ficheiro.<br /><br />Se a sua organização utiliza a versão no local do Rights Management (AD RMS), pode especificar os endereços de e-mail estão limitados às pessoas da sua organização. Quando isto aplica-se e tentar especifique endereços de e-mail externo, verá uma mensagem a informá-lo que a configuração da empresa permite a partilha de conteúdo protegido apenas dentro da empresa. No entanto, se a sua organização utiliza o Azure RMS, estes endereços de e-mail podem ser para as pessoas da sua organização ou para as pessoas na organização outra.<br /><br />Por exemplo: janetm@contoso.com; p.dover@Fabrikam.com|
|**Proteção genérica**|Se esta opção estiver selecionada, significa que o ficheiro que selecionou não pode ser protegido nativamente. Para obter mais informações, consulte o artigo. [O que é a diferença entre proteção genérica e proteção incorporada (nativa)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) neste tópico.|
|**Visualizador-ver apenas**<br /><br />**Revisor-ver e editar**<br /><br />**Coautor-ver, editar, copiar e imprimir**<br /><br />**Coproprietário-todas as permissões** **Note:** Todas estas opções têm um ícone redondo antes do nome, que representam um globo do mundo. Este ícone é utilizado porque normalmente, pode selecionar uma das seguintes opções quando enviar o anexo para alguém numa organização diferentes.|Selecione uma das seguintes opções se pretender definir os direitos para o seu documento protegido. Clique em cada uma das opções para ver uma descrição.<br /><br />Ao escolher uma das seguintes opções, apenas as pessoas especifica na **utilizadores** tem os direitos que especificar para abrir e utilizar o documento. Por exemplo, se reencaminhar para outra pessoa, não seria abrir o documento.|
|Modelos de política que configura o seu administrador.<br /><br />Por exemplo, se o nome da sua empresa for Contoso, Lda.: **Contoso, Lda. - apenas visualização confidencial** **Note:** Todas estas opções têm um ícone quadrado antes do nome, que representam um modulares do office. Este ícone é utilizado porque normalmente, pode selecionar uma das seguintes opções quando enviar o anexo para alguém na sua organização.|Quando partilhar um documento com pessoas que trabalham na sua organização, verá os modelos de políticas disponíveis que configura o seu administrador. Escolha um dos seguintes quando o documento não deve ser partilhado fora da sua organização.<br /><br />Ao escolher uma das seguintes opções, o administrador define os direitos para o documento e quem pode abri-lo.|
|**Expirar estes documentos em**|Selecione esta opção apenas para ficheiros sensíveis ao tempo que os utilizadores que selecionou devem não poderão abrir após uma data que especificar. Ainda poderá abrir o ficheiro original, mas após a meia-noite (o fuso horário atual), no dia em que especificou, outras pessoas não conseguirá abrir o ficheiro.<br /><br />Esta opção não está disponível se selecionar um modelo de política que configura o seu administrador.|
|**Enviar-me e-mail quando alguém tentar abrir estes documentos**|**Note:** Esta opção está atualmente em pré-visualização.<br />Selecione esta opção se pretender receber notificações por e-mail sempre que alguém tentar abrir o documento que está a proteger. A mensagem de correio eletrónico indicará quem tentou abri-lo e se o fizeram com êxito.<br /><br />Esta opção está disponível apenas se a sua organização utiliza o Azure RMS. Se a sua organização utiliza a versão no local do Rights Management (AD RMS), não verá esta opção.|
|**Permitir revogar instantaneamente o acesso a estes documentos**|Escolha esta opção se necessitar de revogar o acesso aos documentos mais tarde, utilizando o site de monotorização de documentos, e a revogação tiver entre em vigor imediatamente. No entanto, se definir esta opção, significa que enquanto o documento não for revogado, os utilizadores necessitarão sempre uma ligação à Internet para ler o documento, sempre que aceder aos mesmos. Poderão existir alguns cenários onde os utilizadores não é possível ligar o seu dispositivo à Internet, e os utilizadores não é possível ler o documento conforme pretendido.<br /><br />Se não selecionar esta opção, pode revogar os documentos mais tarde, utilizando o site de controlo do documento. No entanto, uma vez que os utilizadores não necessitam sempre de uma ligação à Internet para ler o documento, não sabem de imediato que o documento está revogado e pode continuar a lê-lo até efetuarem novamente a autenticação com o Azure RMS. Por predefinição, o número máximo de dias que alguém pode continuar a ler documentos protegidos que revogar é 30 dias, mas um administrador pode alterar este valor para ser maior do que 30 dias ou menos.<br /><br />Esta opção está disponível apenas se a sua organização utiliza o Azure RMS. Se a sua organização utiliza a versão no local do Rights Management (AD RMS), não verá esta opção.|

## <a name="BKMK_GenericNative"></a>O que é a diferença entre proteção genérica e proteção incorporada (nativa)?

-   Quando lhe **protege genericamente um ficheiro**, pessoas não autorizadas não é possível abrir o ficheiro. Mas, depois de pessoas autorizadas abrirem o ficheiro, foi, em seguida, reencaminhe-desprotegidos a outras pessoas ou guardá-lo numa localização que podem aceder a outros utilizadores. Que, no entanto, consulte uma mensagem que indica as permissões que tenham para o ficheiro, e são-lhe pedidos que as cumpram, mas esta proteção não pode ser imposta. Além disso, quando protege genericamente um ficheiro, não é possível restringir as permissões mais autorização. Por exemplo, não é possível restringir o conteúdo para ver apenas, ou não são impressas.:

    > [!NOTE]
    > Um ficheiro protegido genericamente tem sempre uma extensão de nome de ficheiro de **. pfile**.

-   Em comparação, quando utiliza o **proteção incorporada (nativa)** do Rights Management com aplicações que a suportam (por exemplo, ficheiros do Office), a proteção é aplicada ao ficheiro mesmo se o ficheiro é enviado a outra pessoa ou guardado noutra localização. E, quando protege estes ficheiros, pode utilizar permissões restritivas como só de leitura, ou a permissão para editar, mas não para imprimir ou copiar. Por exemplo, pode selecionar **Visualizador-ver apenas**, para que não é possível editar o conteúdo, impresso ou copiadas.

Para obter informações técnicas adicionais, consulte o [Níveis de proteção – nativa e genérica](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) secção a [Guia partilha Rights Management aplicação administrador](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>O que é o ficheiro. ppdf criado automaticamente?

-   Quando partilha um ficheiro protegido por e-mail (partilha protegida), automaticamente a aplicação de partilha RMS cria um **. ppdf** versão do ficheiro para Word, Excel, PowerPoint ou PDF. Esta é uma versão protegida só de leitura do ficheiro que apenas as pessoas autorizadas podem abrir e assegura que os destinatários podem sempre ler o anexo, mesmo se estiverem a utilizar um dispositivo móvel que não tem uma aplicação que suporta nativamente o Rights Management. Fornecimento destas pessoas têm instalada de aplicação de partilha RMS, poderão ler o anexo.

    Neste cenário, ao contrário de um ficheiro protegido genericamente, é imposta a restrição de utilização. O destinatário não conseguirá guardar esta versão do ficheiro e, se reencaminhar o anexo para outra pessoa, as restrições originais permanecem no documento. Apenas as pessoas autorizadas para o documento protegido será possível abri-lo.

    > [!NOTE]
    > Um ficheiro. ppdf é criado automaticamente quando partilhar protegida (partilha por correio eletrónico), mas não é criado quando proteger no local.

## Exemplos e outras instruções
Para obter exemplos de como pode utilizar a aplicação e instruções sobre como proceder de partilha Rights Management, consulte as secções seguintes a partir do Guia do utilizador aplicação partilha Rights Management:

-   [Exemplos para utilizar a aplicação de partilha RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [O que pretende fazer?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Consultar Também
[Guia de utilizador de aplicação partilha do Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

