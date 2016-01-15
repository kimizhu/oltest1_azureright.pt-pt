---
description: na
keywords: na
title: Microsoft Rights Management sharing application user guide - original publication
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: 350b6869-084d-4e8a-a4d3-df44a40fa13b
robots: noindex,nofollow
---
# Manual do utilizador da aplica&#231;&#227;o de partilha Microsoft Rights Management - publica&#231;&#227;o original
Este manual do utilizador da aplicação de partilha Microsoft Rights Management para Windows inclui as secções seguintes:

-   [Evaluating and Installing Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Eval)

-   [Using Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UsingMSRMSApp)

-   [Using User-Authored Permissions and Sharing Protected Content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Custom)

-   [Using the Office Toolbar Add-in](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_OfficeToolbar)

-   [Administrator’s guidance for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminGuide)

Para obter mais informações sobre as perguntas mais frequentes e a resolução de problemas, consulte [FAQ para a Aplicação de Partilha Microsoft Rights Management para Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="BKMK_Eval"></a>Avaliar e Instalar a aplicação de partilha Microsoft Rights Management
Esta secção explica o que é a aplicação de partilha Microsoft Rights Management e como instalá-la:

-   [What is the Microsoft Rights Management sharing application?](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_WhatIs)

-   [Requirements for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Reqs)

-   [Installing the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Install)

### <a name="BKMK_WhatIs"></a>O que é a aplicação de partilha Microsoft Rights Management?
A aplicação de partilha Microsoft Rights Management é uma aplicação transferível e opcional para o Microsoft Windows e que proporciona o seguinte:

-   Melhora o Explorador de Ficheiros (também conhecido como Explorador do Windows no Windows 7 e em versões anteriores) para permitir a proteção de um único ficheiro ou de uma grande quantidade de ficheiros, assim como de todos os ficheiros contidos numa pasta selecionada.

-   Adiciona suporte para a proteção de qualquer tipo de ficheiro e um visualizador incorporado para tipos de ficheiros de texto e de imagens normalmente utilizados.

-   Adiciona novos botões à barra de ferramentas do Microsoft Office para Word, PowerPoint e Excel.

### <a name="BKMK_Reqs"></a>Requisitos da aplicação de partilha Microsoft Rights Management
Para utilizar a aplicação de partilha Microsoft Rights Management, o seu computador tem de executar o Windows 8.1, o Windows 8 ou o Windows 7.

A aplicação de partilha Microsoft Rights Management requer o Cliente 2.1 de AD RMS, que é instalado como parte do pacote de instalação. A aplicação de partilha Microsoft Rights Management só funciona com esta versão do cliente de AD RMS.

### <a name="BKMK_Install"></a>Instalar a aplicação de partilha Microsoft Rights Management
Para instalar a aplicação de partilha Microsoft Rights Management, proceda da seguinte forma:

1.  Aceda à página [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.

2.  Na secção **Computadores**, clique no ícone da **aplicação RMS para Windows** e guarde o pacote de instalação da aplicação de partilha Microsoft Rights Management no computador.

3.  Faça duplo clique no ficheiro comprimido que foi transferido e, em seguida, faça duplo clique em **setup.exe**. Se lhe for perguntado se pretende continuar, clique em **Sim**.

4.  Na página **Configurar o Microsoft RMS**, clique em **Seguinte** e aguarde que a instalação seja concluída.

5.  Quando a instalação estiver concluída, clique em **Reiniciar**, para reiniciar o computador e concluir a instalação. Em alternativa, clique em **Fechar** e reinicie o computador mais tarde para concluir a instalação.

## <a name="BKMK_UsingMSRMSApp"></a>Utilizar a aplicação de partilha Microsoft Rights Management
Esta secção abrange formas diferentes de utilizar a aplicação de partilha Microsoft Rights Management:

-   [Creating a protected text (.ptxt) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePTXT)

-   [Viewing a protected text (.ptxt) or a protected image file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPTXT)

-   [Creating a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePFILE)

-   [Viewing a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPFILE)

-   [Removing protection from a file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Unprotect)

### <a name="BKMK_CreatePTXT"></a>Criar um ficheiro de texto protegido (.ptxt)
A aplicação de partilha Microsoft Rights Management pode ser utilizada para converter um ficheiro de texto normal (.txt) num ficheiro protegido (.ptxt).

##### Para criar um ficheiro de texto protegido (.ptxt)

1.  No Explorador de Ficheiros, clique com o botão direito do rato numa pasta, aponte para **Novo** e, em seguida, clique em **Documento de Texto**.

2.  Mude o nome do ficheiro (por exemplo, Amostra.txt).

3.  Faça duplo clique no ficheiro para o abrir no Bloco de notas.

4.  No Bloco de notas, adicione algumas linhas de texto ao ficheiro, como as seguintes, e depois guarde-o:

    ```
    This is a sample text file.
    This is a sample text file.
    This is a sample text file.
    This is a sample text file. 
    This is a sample text file.
    This is a sample text file.
    ```

5.  Clique com o botão direito do rato no ficheiro, aponte para **Proteger no local** e selecione um modelo na lista. (Tenha em atenção que, se for a primeira vez que utiliza a ferramenta, terá de selecionar **Empresa - Proteção** para começar a transferir os modelos para a sua empresa.)

6.  No ecrã da **aplicação de partilha Microsoft Rights Management**, confirme a política que pretende aplicar, clique em **Aplicar** e, depois de o ficheiro estar protegido, clique em **Fechar**.

### <a name="BKMK_ViewPTXT"></a>Ver um ficheiro de texto protegido (.ptxt) ou um ficheiro de imagem protegido
Para ver um ficheiro de texto protegido (.ptxt), no Explorador de Ficheiros, faça duplo clique no ficheiro (por exemplo, Amostra.ptxt). Pode ser-lhe pedido que autorize a aplicação a obter direitos. A política de proteção é apresentada na parte superior do ficheiro.

As imagens protegidas podem ser abertas e vistas de forma semelhante.

### <a name="BKMK_CreatePFILE"></a>Criar um ficheiro de proteção genérica (.pfile)
O formato de ficheiro de proteção genérica (.pfile) pode ser utilizado para fornecer um nível de proteção genérica a tipos de ficheiro que não são suportados diretamente pela aplicação de partilha Microsoft Rights Management ou por outras aplicações que forneçam proteção incorporada do tipo RMS.

Por exemplo, o formato de ficheiro de proteção genérica pode proteger ficheiros .vsd criados através do Microsoft Visio (que atualmente não suporta proteção incorporada).

> [!NOTE]
> Os ficheiros que utilizam a proteção geral só estão protegidos para autenticação. Um utilizador que esteja autorizado a utilizar o ficheiro protegido (.pfile) será autenticado e os respetivos direitos e permissões são apresentados, mas não podem ser forçados depois de o ficheiro ter sido aberto no formato original (por exemplo, depois de o ficheiro .vsd ter sido aberto no Visio). Um utilizador que não esteja autorizado ou que não possa ser autenticado não conseguirá abrir o ficheiro protegido.

##### Para criar um ficheiro de proteção genérica (.pfile) a partir de um ficheiro de desenho do Visio (.vsd)

1.  No Explorador de Ficheiros, clique com o botão direito do rato numa pasta, aponte para **Novo** e, em seguida, clique em **Novo Documento do Visio**.

2.  Mude o nome do ficheiro (por exemplo, Amostra.vsd).

3.  Faça duplo clique no ficheiro para o abrir no Visio.

4.  No Visio, adicione elementos ao desenho e, depois, guarde e feche o ficheiro.

5.  Clique com o botão direito do rato no ficheiro, aponte para **Proteger no local** e selecione um modelo de política na lista. (Tenha em atenção que, se for a primeira vez que utiliza a ferramenta, terá de selecionar **Empresa - Proteção** para começar a transferir os modelos para a sua empresa.)

6.  No ecrã da **aplicação de partilha Microsoft Rights Management**, selecione a política que pretende aplicar e, em seguida, clique em **Aplicar**.

7.  Uma mensagem informa-o de que o seu ficheiro protegido foi guardado como Sample.vsd.pfile (o ficheiro original é eliminado).

### <a name="BKMK_ViewPFILE"></a>Ver um ficheiro de proteção genérica (.pfile)
Para ver um ficheiro de proteção genérica (.pfile), no Explorador de Ficheiros, faça duplo clique no ficheiro de proteção genérica (.pfile) (por exemplo, Sample.vsd.pfile) e clique em **Abrir**.

### <a name="BKMK_Unprotect"></a>Remover a proteção de um ficheiro
A aplicação de partilha Microsoft Rights Management oferece-lhe a opção de remover a proteção de ficheiros que protegeu anteriormente.

Para remover a proteção (isto é, desproteger) de um ficheiro anteriormente protegido, tem de aplicar a opção **Remover Proteção**, da seguinte forma:

1.  Clique com o botão direito do rato em **Sample.ptxt**, aponte para **Proteger no local** e clique em **Remover Proteção**. Pode ser-lhe pedido que autorize a aplicação a obter direitos.

2.  O ficheiro Sample.ptxt será eliminado e substituído por Sample.txt.

## <a name="BKMK_Custom"></a>Utilizar as Permissões de Criação do Utilizador e Partilhar Conteúdo Protegido
Esta secção explica como proteger e consumir um ficheiro ao utilizar permissões de criação do utilizador, como partilhar conteúdo protegido e como proteger vários ficheiros:

-   [Protecting a file with user-authored permissions](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ProtectCustom)

-   [Consuming files that have user-authored protection](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UserDefined)

-   [Sharing protected content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ShareProtected)

-   [Using keyboard shortcuts](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AccessKeys)

-   [Applying protection to multiple files and folders](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Multiple)

### <a name="BKMK_ProtectCustom"></a>Proteger um ficheiro com permissões de criação do utilizador
A proteção da criação do utilizador pode ser utilizada para conseguir o seguinte:

-   Para limitar o acesso a ficheiros a apenas uma lista específica de utilizadores individuais identificados pelos respetivos endereços de e-mail.

-   Para limitar a utilização de um ficheiro a apenas direitos específicos, como direitos só de leitura de um documento.

Para proteger um ficheiro com permissões de criação do utilizador, clique com o botão direito do rato no ficheiro, clique em **Proteger no local** e em **Personalizar Permissões**. É apresentado o ecrã seguinte:

![](../Image/ADRMS_MSRMSApp_ProtectCustom.gif)

Escreva os endereços de e-mail da lista de utilizadores, utilize o controlo de deslize para selecionar as permissões para o ficheiro e clique em **Aplicar**.

### <a name="BKMK_UserDefined"></a>Consumir ficheiros que têm proteção de criação do utilizador
A maioria dos ficheiros protegidos que é processada pela aplicação de partilha Microsoft Rights Management foi protegida através da aplicação de níveis de proteção baseados em modelos. No entanto, é possível, que a aplicação de partilha Microsoft Rights Management suporte igualmente ficheiros aos quais foi conferido um nível de proteção de criação do utilizador.

A proteção de criação do utilizador pode ser utilizada para obter os tipos seguintes de proteção para um ficheiro:

-   Para limitar o acesso a ficheiros a apenas uma lista muito específica de utilizadores individuais identificados pelos respetivos endereços de e-mail.

-   Para limitar a utilização de um ficheiro a apenas um direito específico, como direitos só de impressão do documento.

Nos formatos de ficheiro de texto e de imagem, este nível de proteção requer que todas as aplicações que forem utilizadas para editar, guardar ou restringir ficheiros de texto ou de imagem tenham sido concebidos de modo a suportar proteção RMS e a implementar as API de proteção fornecidas no AD RMS SDK.

Quando visualiza um ficheiro de texto protegido ao qual tenha sido aplicada proteção de criação do utilizador, observa uma ligeira diferença nas permissões, uma vez que estas são apresentadas para o ficheiro, conforme apresentado no exemplo seguinte.

Nos ficheiros que são protegidos através do formato de ficheiro de proteção genérica (.pfile), os direitos ou permissões que tenham sido definidos pelo utilizador aparecem no ecrã de confirmação, em vez do nome do modelo que foi utilizado para proteger o ficheiro, conforme exemplificado na ilustração seguinte.

![](../Image/ADRMS_MSRMSApp_SP_ConsumePfile.gif)

### <a name="BKMK_ShareProtected"></a>Partilhar conteúdo protegido
Para proteger e partilhar conteúdo, clique com o botão direito do rato no ficheiro e clique em **Partilhar Protegido**. É apresentado o ecrã seguinte:

![](../Image/ADRMS_MSRMSAPP_SP_ShareProtected.gif)

Escreva os endereços de e-mail da lista de utilizadores, utilize o controlo de deslize para selecionar as permissões para o ficheiro e clique em **Enviar**. A aplicação abre o Outlook com um pré-e-mail, com o ficheiro protegido anexado. O ficheiro original não será protegido.

Para permitir que os utilizadores vejam ficheiros protegidos em dispositivos que não tenham o Windows instalado, clique em **Permitir consumo em todos os dispositivos**. Os utilizadores terão de [transferir a aplicação de partilha Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) para o respetivo dispositivo.

### <a name="BKMK_AccessKeys"></a>Utilizar atalhos de teclado
Prima a tecla **Alt** para ver as teclas de acesso disponíveis. Prima **Alt** + a tecla de acesso para selecionar uma opção. Por exemplo, na caixa de diálogo **Partilhar Protegido**, prima **Alt** para ver as teclas de acesso e prima **Alt + u** para selecionar **Os utilizadores têm de iniciar sessão sempre que abrem este ficheiro**.

![](../Image/ADRMS_MSRMSApp_AccessKeys.png)

### <a name="BKMK_Multiple"></a>Aplicar proteção a vários ficheiros e pastas
A aplicação de partilha Microsoft Rights Management também pode ser utilizada para aplicar proteção a mais do que um ficheiro, selecionando, por exemplo, vários ficheiros ou uma pasta que contenha ficheiros desprotegidos no Explorador de Ficheiros.

##### Para proteger vários ficheiros ou todos os ficheiros contidos numa pasta selecionada

1.  No Explorador de Ficheiros, selecione vários ficheiros ou uma pasta que contenha vários ficheiros a proteger.

2.  Clique com o botão direito do rato na pasta ou nos ficheiros selecionados, aponte para **Proteger no local** e selecione um modelo na lista. (Tenha em atenção que, se for a primeira vez que utiliza a ferramenta, terá de selecionar **Empresa - Proteção** para começar a transferir os modelos para a sua empresa.)

3.  No ecrã da **aplicação de partilha Microsoft Rights Management**, confirme que os ficheiros foram protegidos.

Se lhe tiverem sido apresentadas mensagens de erro, consulte [FAQ da Aplicação de Partilha Microsoft Rights Management para Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="BKMK_OfficeToolbar"></a>Utilizar o Suplemento da Barra de Ferramentas do Office
É possível proteger e partilhar ficheiros do Word, do PowerPoint e do Excel diretamente no Microsoft Office com o suplemento do friso do Office da aplicação de partilha Microsoft Rights Management. Clique em **Partilhar Protegido**, no friso, para iniciar a aplicação de partilha Microsoft Rights Management.

![](../Image/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

## <a name="BKMK_AdminGuide"></a>Documentação de orientação do administrador para a aplicação de partilha Microsoft Rights Management
Este Manual do Administrador da aplicação de partilha Microsoft Rights Management para Windows inclui as secções seguintes:

-   [Microsoft Rights Management sharing application Technical Overview](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminOverview)

-   [Supported File Types](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_SupportFileTypes)

-   [Automatic deployment for the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ScriptedInstall)

### <a name="BKMK_AdminOverview"></a>Descrição Geral Técnica da aplicação de partilha Microsoft Rights Management
A aplicação de partilha Microsoft Rights Management é uma aplicação transferível e opcional para o Microsoft Windows e outras plataformas e que proporciona o seguinte:

-   Proteção de um único ficheiro ou de uma grande quantidade de ficheiros, assim como de todos os ficheiros contidos numa pasta selecionada.

-   Suporte completo para a proteção de qualquer tipo de ficheiro e um visualizador incorporado para tipos de ficheiros de texto e de imagens normalmente utilizados.

-   Proteção genérica para ficheiros que não suportem proteção RMS.

-   Interoperabilidade completa com ficheiros protegidos através da Gestão de Direitos de Informação (IRM) do Office

-   Interoperabilidade completa com ficheiros PDF protegidos através de SharePoint, FCI e de ferramentas de criação de PDF suportadas

A aplicação de partilha Microsoft Rights Management utiliza o novo runtime [Cliente 2.1 de AD RMS](http://www.microsoft.com/download/details.aspx?id=38396). Fornece aos utilizadores a capacidade de proteger conteúdo através de modelos predefinidos ou definidos pelo utilizador, que pode personalizar e implementar na sua organização. Ao utilizar a funcionalidade do AD RMS 2.1, a aplicação de partilha Microsoft Rights Management fornece aos utilizadores finais proteção e uma experiência de consumo simples.

Com a versão de outubro de 2013 do Microsoft Azure AD RMS, é possível proteger documentos nativamente com o Office 2010 e enviá-los para pessoas de outra empresa, que, por sua vez, podem utilizar o Microsoft Azure AD RMS para os consumir. Além disso, com esta versão, se utilizar o AD RMS em Modo Criptográfico 2, pode utilizar RMS para indivíduos e consumir conteúdo de pessoas de outra empresa que utilize o Microsoft Azure AD RMS. Para obter mais informações sobre o Modo Criptográfico 2, consulte [Modos Criptográficos de AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

Para transferir a aplicação de partilha Microsoft Rights Management, proceda da seguinte forma:

1.  Inicie sessão no [Microsoft Connect](http://connect.microsoft.com/) com a sua Conta Microsoft (anteriormente denominada Live ID).

2.  Na página **Home**, procure **Serviços de Gestão de Direitos** e adira ao grupo.

3.  Clique em **Transferências** e, em seguida, em **aplicação de partilha Microsoft Rights Management**.

4.  Na página **Detalhes da Transferência**, selecione **Microsoft Rights Management sharing application.zip** e clique em **Transferir**.

5.  Se necessário, instale o Microsoft File Transfer Manager e conclua os passos para transferir a aplicação de partilha Microsoft Rights Management.

#### Níveis de Proteção Suportados pela aplicação de partilha Microsoft Rights Management
A aplicação de partilha Microsoft Rights Management suporta proteção em dois níveis diferentes, conforme descrito na tabela seguinte.

||||
|-|-|-|
|Tipo de proteção|Nativa|Genérica|
|Descrição|Nos ficheiros de texto, imagem, do Microsoft Office (Word, Excel e PowerPoint), .pdf e outros tipos de ficheiros de aplicação que suportem AD RMS, a proteção nativa fornece um elevado nível de proteção que inclui encriptação e imposição de direitos (permissões).|Em todas as outras aplicações e tipos de ficheiros, a proteção genérica fornece um nível de proteção que inclui encapsulamento de ficheiros através do tipo de ficheiro .pfile e autenticação, para verificar se um utilizador está autorizado a abrir o ficheiro.|
|Proteção|Os ficheiros são totalmente encriptados e a proteção é imposta das formas seguintes:<br /><br />-   Antes de o conteúdo protegido ser apresentado, tem de ocorrer a autenticação com êxito para aqueles que recebam o ficheiro por e-mail ou a quem for facultado o acesso através de um ficheiro ou de permissões de partilha.<br />-   Além disso, os direitos de utilização e a política definidos pelo proprietário do conteúdo, quando os ficheiros estão protegidos, são totalmente impostos quando o conteúdo é apresentado no Visualizador IP (para ficheiros de texto e de imagem protegidos) ou na aplicação associada (para todos os outros tipos de ficheiros suportados).|A proteção de ficheiros pode ser imposta das formas seguintes:<br /><br />-   Antes de o conteúdo protegido ser apresentado, tem de ocorrer a autenticação com êxito para aqueles que estão autorizados a abrir o ficheiro e a quem foi facultado o acesso ao mesmo. Se a autorização falhar, o ficheiro não abre.<br />-   Os direitos de utilização e a política definidos pelo proprietário do conteúdo são apresentados para informar os utilizadores autorizados da política de utilização pretendida.<br />-   O registo de auditoria dos utilizadores autorizados que abrem e acedem aos ficheiros é efetuado; no entanto, não são impostos quaisquer direitos de utilização por aplicações que não os suportem.|
|Predefinições dos tipos de ficheiros|Este é o nível de proteção predefinido para os tipos de ficheiros seguintes:<br /><br />-   Ficheiros de texto e de imagem<br />-   Ficheiros do Microsoft Office (Word, Excel e PowerPoint)<br />-   Portable document format (.pdf)<br /><br />Para obter mais informações, consulte Tipos de Ficheiros Suportados.|Esta é a proteção predefinida para todos os outros tipos de ficheiros (como .vsdx, .rtf e outros) que não são suportados através da proteção completa.|

### <a name="BKMK_SupportFileTypes"></a>Tipos de Ficheiros Suportados
A tabela seguinte lista os tipos de ficheiros que são suportados pela aplicação de partilha Microsoft Rights Management.

|Extensão de nome de ficheiro|Descrição|Extensão de nome de ficheiro original|
|--------------------------------|-------------|-----------------------------------------|
|.ptxt|Ficheiro de texto protegido|.txt|
|.pxml|Ficheiro XML protegido|.xml|
|.pjpg|Ficheiro de imagem JPG protegido|.jpg|
|.pjpeg|Ficheiro de imagem JPEG protegido|.jpeg|
|.ppng|Ficheiro de imagem PNG protegido|.png|
|.ptiff|Ficheiro de imagem TIFF protegido|.tiff|
|.pbmp|Ficheiro de mapa de bits do Windows protegido|.bmp|
|.pgif|Ficheiro de imagem GIF protegido|.gif|
|.pgiff|Ficheiro de imagem GIFF protegido|.giff|
|.pjpe|Ficheiro de imagem JPE protegido|.jpe|
|.pjfif|Ficheiro de imagem JFIF protegido|.jfif|
|.pjif|Ficheiro de imagem JIF protegido|.jif|
A tabela seguinte lista os tipos de ficheiros que são suportados pelo Microsoft Office 2013, o Office 2010 e o Office 2007. Existem dois tipos de protetores: O MsoIrmProtector e o OpcIrmProtector. Para obter mais informações sobre estes tipos de protetores, consulte [Protetores de Formatos de Ficheiros do Microsoft Office](http://archive.msdn.microsoft.com/OfficeProtectors).

|||
|-|-|
|O MsoIrmProtector suporta os tipos de ficheiros seguintes:<br /><br />-   doc<br />-   dot<br />-   xla<br />-   xls<br />-   xlt<br />-   pps<br />-   ppt|O OpcIrmProtector suporta os tipos de ficheiros seguintes:<br /><br />-   docm<br />-   docx<br />-   dotm<br />-   dotx<br />-   xlam<br />-   xlsb<br />-   xlsm<br />-   xlsx<br />-   xltm<br />-   xltx<br />-   xps<br />-   potm<br />-   potx<br />-   ppsx<br />-   ppsm<br />-   pptm<br />-   pptx<br />-   thmx|

### <a name="BKMK_ScriptedInstall"></a>Implementação automática da aplicação de partilha Microsoft Rights Management
A versão do Windows da aplicação de partilha RMS suporta uma instalação através de ficheiro script, o que a torna adequada para implementações em empresas.

##### Para transferir a aplicação de partilha RMS para implementação automática

1.  Vá para a página da [Aplicação de Partilha Microsoft Rights Management para Windows](http://www.microsoft.com/en-us/download/details.aspx?id=40857), no Centro de Transferências da Microsoft, e clique em **Transferir**.

2.  Selecione e transfira os ficheiros de que necessita. Existem dois pacotes de instalação do cliente: um para Windows de 64 bits (Microsoft Rights Management sharing application x64.zip) e outro para Windows de 32 bits (Microsoft Rights Management sharing application x86.zip).

3.  Extraia os ficheiros dos pacotes de instalação comprimidos, por exemplo, fazendo duplo clique neles. Em seguida, copie os ficheiros extraídos para uma localização na rede à qual os computadores clientes consigam aceder.

Os pacotes de configuração da aplicação de partilha RMS suportam diferentes cenários de implementação e incluem o seguinte:

|Descrição|Cenário de implementação|
|-------------|----------------------------|
|Assistente de Início de Sessão do Microsoft Online|Necessário para os seguintes:<br /><br />-   Office 2010 e Windows Azure RMS|
|Correção para Office (KB 2596501)|Necessária para os seguintes:<br /><br />-   Office 2010 e Windows Azure RMS|
|Correção para Modo Criptográfico 2 (KB 2627273)|Necessária para os seguintes:<br /><br />-   Office 2010 e Windows Azure RMS|
|Cliente de AD RMS e a aplicação de partilha RMS|Necessários para os seguintes:<br /><br />-   Office 2013 e Windows Azure RMS<br />-   Office 2010 e Windows Azure RMS<br />-   Office 2013 e Active Directory RMS<br />-   Office 2010 e Active Directory RMS<br />-   Atualização da aplicação de partilha RMS|
|Suplemento do Office para o friso|Necessário para os seguintes:<br /><br />-   Office 2013 e Windows Azure RMS<br />-   Office 2013 e Active Directory RMS<br />-   Office 2010 e Active Directory RMS<br />-   Atualização da aplicação de partilha RMS|
|Ferramenta de preparação da Gestão de Direitos do Active Directory do Microsoft Azure|Necessária para os seguintes:<br /><br />-   Office 2010 e Windows Azure RMS|
> [!NOTE]
> No cenário do **Office 2010 e do Windows Azure RMS**, pode estar a utilizar o Microsoft Azure RMS, ou o Active Directory RMS, mas pretender enviar documentos de forma segura a pessoas de outra empresa que utilizam o Microsoft Azure RMS.
> 
> Quando instala e executa a ferramenta de preparação da Gestão de Direitos do Active Directory do Microsoft Azure para suportar o Office 2010, esta efetua dois procedimentos:
> 
> -   Edita o registo para suportar a aplicação de partilha RMS.
> -   Faz “arrancar” o utilizador, o que significa que o computador contacta o servidor AD RMS ou o Microsoft Azure RMS e obtém os certificados de que o computador e o utilizador necessitam para utilizar RMS.

Utilize o procedimento seguinte para identificar os comandos necessários para implementar a aplicação de partilha RMS para estes cenários de implementação:

-   Office 2013 e Windows Azure RMS

-   Office 2010 e Windows Azure RMS

-   Office 2013 ou Office 2010 e Active Directory RMS

-   Atualização da aplicação de partilha RMS

Os exemplos contidos nos comandos partem do princípio de que copiou os ficheiros transferidos e extraídos para uma partilha de rede à qual os computadores clientes acedem através do **\\server5\apps\rms** e de que os computadores clientes já têm uma pasta denominada **C:\Log files**, na qual guarda os ficheiros de registo da instalação da aplicação. Para cada instalação, tem de escolher o nome do ficheiro de registo da instalação, mas tem de ter a extensão de nome de ficheiro .log.

> [!IMPORTANT]
> Antes de implementar a aplicação de partilha RMS, tem de empacotar os comandos necessários nestes procedimentos, para que os mesmos possam instalar no contexto do computador para todos os utilizadores, bem como instalar com privilégios de administrador local. Em seguida, pode implementar o pacote nos computadores, através do seu mecanismo de implementação de aplicações padrão, como a Política de Grupo ou o System Center Configuration Manager.
> 
> A exceção é a ferramenta de preparação da Gestão de Direitos do Active Directory do Microsoft Azure: Esta ferramenta tem de ser utilizada uma vez para cada utilizador do computador e de ser executada com privilégios elevados para editar o Registo com êxito. Existem formas diferentes de o fazer, incluindo pedir aos utilizadores para executarem o comando (por exemplo, uma ligação numa mensagem de e-mail ou uma ligação no portal do suporte técnico) ou pode adicioná-la ao respetivo script de início de sessão. Se não puder utilizar o comando runas porque os outros utilizadores não têm uma conta de administrador local, existem ferramentas de implementação que podem elevar automaticamente um comando, de acordo com as regras que especificar.

##### Para implementar a aplicação de partilha RMS para Office 2013 e Windows Azure RMS

1.  Instale o Cliente do AD RMS e a aplicação de partilha RMS com os comandos seguintes:

    -   Para Windows de 64 bits: x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "&lt;caminho e nome do ficheiro de registo&gt;"

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para Windows de 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Instale o suplemento do Office com os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Para concluir a instalação, o computador tem de ser reiniciado. Pode utilizar um comando como shutdown /i para iniciar um reinício automático.

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

##### Para implementar a aplicação de partilha RMS para Office 2010 e Windows Azure RMS

1.  Instale o Assistente de Início de Sessão no Microsoft Online com os comandos seguintes:

    -   Para Windows de 64 bits:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name >"
        ```

    -   Para Windows de 32 bits:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "C:\Log files\assistant.log"`

2.  Instale a correção do Office com os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"<log file path and name >"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        x86\office2010-kb2596501-fullfile-x86-glb.exe /norestart /quiet /log:"<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"C:\Log files\kb2596501install.log"`

3.  Instale a correção do Modo Criptográfico 2 com os comandos seguintes:

    -   Para Windows de 64 bits:

        ```
        wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"<log file path and name >"
        ```

    -   Para Windows de 32 bits:

        ```
        wusa.exe /norestart /quiet "x86\Windows6.1-KB2627273-v4-x86.msu" /log:"<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"C:\Log files\kb267273.log"`

4.  Instale o Cliente do AD RMS e a aplicação de partilha RMS com o comando seguinte:

    -   Para Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name >"
        ```

    -   Para Windows de 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

5.  Instale o suplemento do Office com os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Para concluir a instalação, o computador tem de ser reiniciado. Pode utilizar um comando como shutdown /i para iniciar um reinício automático.

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

6.  Instale a ferramenta de preparação da Gestão de Direitos do Active Directory do Microsoft Azure, adicionando o comando seguinte aos scripts de início de sessão:

    > [!IMPORTANT]
    > Para executar este comando com êxito, os utilizadores têm de ter privilégios de administrador local.

    -   Para Windows 8, de 64 bits:

        ```
        x64\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   Para Windows 8, de 32 bits:

        ```
        X86\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   Para Windows 7, de 64 bits:

        ```
        x64\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   Para Windows 7, de 32 bits:

        ```
        X86\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    > [!NOTE]
    > Este comando pode pedir ao utilizador para introduzir as respetivas credenciais do Windows Azure. Se o computador não for adicionado a um domínio, será pedido ao utilizador que o faça. Se o computador tiver sido adicionado a um domínio, a ferramenta pode conseguir utilizar as credenciais em cache.

    Por exemplo: `\\server5\apps\rms\x64\aadrmprep.exe /initiateMe /logfile "C:\Log files\aadrmprepinstall.log"`

##### Para implementar a aplicação de partilha RMS para Office 2013 ou Office 2010 e Active Directory RMS

1.  Instale o Cliente do AD RMS e a aplicação de partilha RMS através dos comandos seguintes:

    -   Para Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para Windows de 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Instale o suplemento do Office com os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Para concluir a instalação, o computador tem de ser reiniciado. Pode utilizar um comando como shutdown /i para iniciar um reinício automático.

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

##### Para atualizar a aplicação de partilha RMS

1.  Instale o Cliente do AD RMS e a aplicação de partilha RMS com o comando seguinte:

    -   Para Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para Windows de 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Instale o suplemento do Office com os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Para concluir a instalação, o computador tem de ser reiniciado. Pode utilizar um comando como shutdown /i para iniciar um reinício automático.

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

#### <a name="BKMK_verifyscripted"></a>Verificar se a instalação teve êxito
Pode utilizar os ficheiros de registo da instalação para verificar se esta foi realizada com êxito.

###### Para verificar o êxito da instalação do Assistente de Início de Sessão no Microsoft Online

-   Para confirmar se foi bem-sucedida, procure o texto seguinte no ficheiro de registo da instalação: **Êxito da instalação ou estado de erro: 0**

    Linhas de exemplo de uma instalação com êxito:

    **MSI (s) (9C:88) [18:49:04:007]: Produto: Suplementos do Office do Microsoft RMS -- A instalação foi concluída com êxito.**

    **MSI (s) (9C:88) [18:49:04:007]: O Windows Installer instalou o produto. Nome do Produto: Suplementos do Office do Microsoft RMS Versão do Produto: 1.0.7. Idioma do Produto: 1033. Fabricante: Microsoft. Êxito da instalação ou estado de erro: 0.**

###### Para verificar o êxito da instalação da correção do Office

-   Para verificar o êxito, procure uma das cadeias de texto seguintes no ficheiro de registo da instalação:

    -   Para a versão de 64 bits do Office:

        -   **office2010-kb2596501-fullfile-x64-glb.exe saiu com o estado SUCESSO**

        -   **office2010-kb2596501-fullfile-x64-glb.exe saiu com o estado NÃO APLICÁVEL**

    -   Para a versão de 32 bits do Office:

        -   **office2010-kb2596501-fullfile-x86-glb.exe saiu com o estado ÊXITO**

        -   **office2010-kb2596501-fullfile-x86-glb.exe saiu com o estado NÃO APLICÁVEL**

###### Para verificar o êxito da instalação da correção do Modo Criptográfico 2

-   Para verificar o êxito, procure uma das cadeias de texto seguintes no ficheiro de registo da instalação:

    -   Para Windows de 64 bits:

        -   **Windows6.1-KB2627273-v4-x64.msu saiu com o estado ÊXITO**

        -   **Windows6.1-KB2627273-v4-x64.msu saiu com o estado NÃO APLICÁVEL**

    -   Para Windows de 32 bits:

        -   **Windows6.1-KB2627273-v4-x86.msu saiu com o estado ÊXITO**

        -   **Windows6.1-KB2627273-v4-x86.msu saiu com o estado NÃO APLICÁVEL**

###### Para verificar o êxito da instalação do Cliente de AD RMS e da aplicação de partilha RMS

-   Para confirmar se foi bem-sucedida, procure o texto seguinte no ficheiro de registo da instalação: **Êxito da instalação ou estado de erro: 0**

    Linhas de exemplo de uma instalação com êxito:

    **MSI (s) (F0:B8) [14:19:57:854]: Produto: Cliente 2.1 dos Serviços de Gestão de Direitos do Active Directory -- A instalação foi concluída com êxito.**

    **MSI (s) (F0:B8) [14:19:57:854]: O Windows Installer instalou o produto. Nome do Produto: Cliente 2.1 dos Serviços de Gestão de Direitos do Active Directory. Versão do Produto: 1.0.1179.1. Idioma do Produto: 1033. Fabricante: Microsoft Corporation. Êxito da instalação ou estado de erro: 0.**

###### Para verificar o êxito da instalação do suplemento do Office

-   Para confirmar se foi bem-sucedida, procure o texto seguinte no ficheiro de registo da instalação: **Êxito da instalação ou estado de erro: 0**

    Linhas de exemplo de uma instalação com êxito:

    **MSI (s) (9C:88) [18:49:04:007]: Produto: Suplementos do Office do Microsoft RMS -- A instalação foi concluída com êxito.**

    **MSI (s) (9C:88) [18:49:04:007]: O Windows Installer instalou o produto. Nome do Produto: Suplementos do Office do Microsoft RMS Versão do Produto: 1.0.7. Idioma do Produto: 1033. Fabricante: Microsoft. Êxito da instalação ou estado de erro: 0.**

###### Para verificar o êxito da instalação da ferramenta de preparação da Gestão de Direitos do Active Directory do Microsoft Azure

-   Para confirmar se foi bem-sucedida, procure o texto seguinte no ficheiro de registo da instalação: **aadrmprep.exe saiu com o estado ÊXITO**

    > [!NOTE]
    > Por vezes, esta instalação pode ser executada duas vezes; a primeira ocorrência falha e a segunda é concluída com êxito.

Se pretender verificar manualmente as alterações ao registo introduzidas por esta ferramenta, são as seguintes:

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

    @="&lt;url de certificação&gt;"

-   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

    DefaultUser="&lt;default_user&gt;"

#### <a name="BKMK_uninstallscripted"></a>Comandos de desinstalação
Nem todos os comandos de instalação que são necessários para estas implementações suportam um comando de desinstalação. Pode desinstalar o cliente do AD RMS e a aplicação de partilha, bem como o suplemento do Office. Utilize os comandos seguintes para desinstalar estes elementos.

###### Para desinstalar o Cliente do AD RMS e a aplicação de partilha RMS

-   Utilize os comandos seguintes:

    -   Para Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Para Windows de 32 bits:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

###### Para desinstalar o suplemento do Office

-   Utilize os comandos seguintes:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Consultar Também
[Transferência da aplicação de partilha Microsoft Rights Management (http://go.microsoft.com/fwlink/?LinkId=303970)](http://go.microsoft.com/fwlink/?LinkId=303970)
 [FAQ da Aplicação de Partilha Microsoft Rights Management para Windows](http://go.microsoft.com/fwlink/?LinkId=303971)

