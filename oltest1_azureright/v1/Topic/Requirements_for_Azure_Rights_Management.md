---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Requisitos para o Azure Rights Management
Para implementar o Microsoft Azure Rights Management (RMS do Azure) na sua organização, certifique-se de que tem os seguintes pré-requisitos. Em seguida, pode utilizar o [Plano de implementação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para implementar a gestão de direitos para a sua organização.

|Requisito|Obter mais informações|
|-------------|--------------------------|
|Uma subscrição de nuvem para RMS|A sua organização tem de ter uma subscrição de nuvem que suporte RMS.<br /><br />Para informações de licenciamento, consulte o [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) deste tópico.|
|Diretório do Azure AD|A sua organização tem de ter um diretório do Azure AD para suportar a autenticação de utilizador para RMS. Além disso, se pretender utilizar as contas de utilizador a partir do directory no local (AD DS), tem também de configurar integração de diretórios.<br /><br />A autenticação multifator (MFA) é suportada com o Azure RMS quando tiver o software de cliente necessários e a infraestrutura de suporte de MFA corretamente configurada.<br /><br />Para obter mais informações, consulte o [Diretório do Azure AD](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) deste tópico.|
|Dispositivos cliente|Os utilizadores têm de ter um dispositivos de cliente (computador ou dispositivo móvel) que executam um sistema operativo que suporte RMS.<br /><br />Para obter mais informações, consulte o [Dispositivos de cliente que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) deste tópico.|
|Aplicações|Os utilizadores tem de executar as aplicações que suportam RMS.<br /><br />Para obter mais informações, consulte o [Aplicações que suportem o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) deste tópico.|
|Infraestrutura de que suporta a conectividade à Internet e serviços em nuvem dependentes|Se tiver uma firewall ou intervenientes semelhantes dispositivos que devem ser configurados para permitir ligações específicas, consulte o artigo de rede [intervalos de endereços IP e URLs de 356 Office](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />A lista de IP e URLs endereços no **identidade e o portal do Office 356** secção aplicam-se para o portal do Office 365, de recursos do Azure Active Directory e Azure Rights Management. Utilize as instruções neste artigo para manter atualizado com as alterações a estas informações ao subscrever um feed RSS.<br /><br />Além das informações no artigo Office, específico para o Azure RMS:<br /><br />-   Não termine a ligação de serviço de cliente TLS (por exemplo, para fazer inspeção de nível de pacotes). Se o fizer, as quebras do certificado afixação de que os clientes de RMS utilizar com CAs gerido por Microsoft para ajudar a proteger as comunicações com o Azure RMS.<br />-   Não utilize uma configuração de proxy web que irá autenticar em nome de um utilizador.|

Se pretender utilizar o Azure RMS com servidores no local, são suportados os seguintes produtos:

-   Exchange Server

-   Servidor do SharePoint

-   Servidores de ficheiros do Windows Server que suportam a infraestrutura de classificação de ficheiros

Para obter informações sobre os requisitos do Azure RMS adicionais para este cenário, consulte o [Servidores no local que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) deste tópico.

> [!IMPORTANT]
> Não é suportado o cenário de implementação seguintes:
> 
> -   Executar o AD RMS e o Azure RMS lado a lado na mesma organização, exceto durante a migração, conforme descrito em [Migrar do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> Existe um caminho de migração suportados [a partir do AD RMS para o Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx), e [Azure RMS para AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Se implementar o Azure RMS e, em seguida, decida que já não pretende utilizar este serviço em nuvem, consulte o artigo [Desativação e a desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Utilize as secções seguintes para obter mais informações sobre os requisitos do Azure RMS.

## <a name="BKMK_SupportedSubscriptions"></a>Subscrições de nuvem que suportam o Azure RMS
Para utilizar o Azure RMS, a sua organização tem de ter pelo menos uma das seguintes subscrições com um número suficiente de licenças de utilizadores e serviços que irão proteger ficheiros e mensagens de correio eletrónico. Se tiver um serviço que será aplicada a proteção para os utilizadores (proprietários dos ficheiros ou mensagens de correio eletrónico), esses utilizadores necessitam de uma destas licenças. Os utilizadores só irão consumir (por exemplo, ler e editar) estas dados protegidos não precisa de uma licença.

-   Office 365

-   Azure Premium de gestão de direitos (anteriormente o Azure RMS autónomo)

-   Enterprise Mobility Suite

-   RMS para utilizadores

Utilize as secções seguintes para obter mais informações e inscrever-se opções.

Para uma comparação das capacidades de Azure RMS para as subscrições pagas licenciamento, consulte o artigo [ofertas de comparação do Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

### Subscrição do Office 365
[Avaliação gratuita de 30 dias: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Esta subscrição foi concebida para organizações que pretendem utilizar os serviços online do Office e utilizar a funcionalidade de gestão de direitos de informação, o que utiliza o Azure RMS. No entanto, nem todas as subscrições do Office 365 incluem o Azure RMS.

|Opção de licenciamento|Office 365 empresas-versão Essentials|Office 365 empresas-versão Premium|Office 365 Enterprise E1<br /><br />Office 365 educação A1|Office 365 Enterprise E3<br /><br />Office 365 educação A3<br /><br />Office 365 administração pública G3|Office 365 Enterprise E4<br /><br />Office 365 educação A4<br /><br />Office 365 administração pública G4|Office 365 Enterprise K1|SharePoint plano 1<br />SharePoint plano 2|Exchange Online plano 1<br />Exchange Online plano 2|
|--------------------------|-----------------------------------------|--------------------------------------|------------------------------------------------------|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Proteção de direitos de informação (IRM)|Não|Não|Não|Sim|Sim|Não|Não|Não|

### Subscrição do Azure Rights Management Premium
[Avaliação gratuita de 30 dias](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Esta subscrição era anteriormente conhecida como autónomo do Azure RMS e foi concebido para organizações que pretendem utilizar o Azure RMS, mas não tem uma subscrição que inclui o Azure RMS. Por exemplo, se tiver uma subscrição para o Office 365 empresas-versão Essentials ou o Office 365 Enterprise E1, estas subscrições não incluem Azure RMS (consulte a tabela na secção anterior). Para utilizar o Azure RMS, que foi possível adquirir uma subscrição do Azure Rights Management-versão Premium (ou comprar outra subscrição, como o Office 365 Enterprise E4, que inclui o Azure RMS).

Para obter mais informações, consulte o artigo [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Esta subscrição também oferece um período de avaliação para a experimentar o Azure RMS para 25 utilizadores, livre de encargos. Se a subscrição expirar antes de comprar uma subscrição de substituição, consulte a secção seguinte, "o que acontece quando a subscrição de avaliação expira?"

|Opção de licenciamento|Office 365 empresas-versão Essentials|Office 365 empresas-versão Premium|Office 365 Enterprise E1<br /><br />Office 365 educação A1|Office 365 Enterprise E3<br /><br />Office 365 educação A3<br /><br />Office 365 administração pública G3|Office 365 Enterprise E4<br /><br />Office 365 educação A4<br /><br />Office 365 administração pública G4|Office 365 Enterprise K1|SharePoint plano 1<br />SharePoint plano 2|Exchange Online plano 1<br />Exchange Online plano 2|
|--------------------------|-----------------------------------------|--------------------------------------|------------------------------------------------------|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Proteção de direitos de informação (IRM)|Sim|Yes <sup>1</sup>|Sim|Sim|Sim|Sim|Sim|Sim|
<sup>1</sup> para empresas-versão Premium, existem algumas restrições de cliente: Pode proteger conteúdo e consumir conteúdo protegido com RMS utilizando o Outlook Web App e aplicação de partilha RMS. Pode consumir conteúdo protegido através da utilização de todas as outras aplicações do Office, que inclui o Office Online e as aplicações de cliente para o Office 365 empresas-versão Premium.

#### <a name="BKMK_TrialExpiryBehavior"></a>O que acontece quando a subscrição de avaliação expira?
Se a sua subscrição de avaliação expirar, perderá o acesso a conteúdo que foi protegido utilizando a sua subscrição de avaliação para o Azure RMS. No entanto, se, em seguida, comprar uma subscrição que suporta o Azure RMS, acesso automaticamente é restaurado.

Uma exceção a perda de acesso após a expiração é se a organização utilizados Azure RMS com o RMS indivíduos subscrição antes de tiver adquirido a subscrição de avaliação. Em seguida, acesso a anteriormente protegido conteúdo permanecerá, mesmo depois da subscrição de avaliação expira.

### Subscrição do Enterprise Mobility Suite
[Avaliação gratuita de 30 dias](http://go.microsoft.com/fwlink/?LinkId=615385)

Esta subscrição foi concebida para organizações que pretendem utilizar uma combinação do Azure Active Directory Premium, do Windows Intune e Azure Rights Management. Para obter mais informações, consulte o [Descrição geral do Microsoft Enterprise Mobility](http://go.microsoft.com/fwlink/?LinkId=615386).

|Opção de licenciamento|Office 365 empresas-versão Essentials|Office 365 empresas-versão Premium|Office 365 Enterprise E1<br /><br />Office 365 educação A1|Office 365 Enterprise E3<br /><br />Office 365 educação A3<br /><br />Office 365 administração pública G3|Office 365 Enterprise E4<br /><br />Office 365 educação A4<br /><br />Office 365 administração pública G4|Office 365 Enterprise K1|SharePoint plano 1<br />SharePoint plano 2|Exchange Online plano 1<br />Exchange Online plano 2|
|--------------------------|-----------------------------------------|--------------------------------------|------------------------------------------------------|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Proteção de direitos de informação (IRM)|Sim|Yes <sup>1</sup>|Sim|Sim|Sim|Sim|Sim|Sim|
<sup>1</sup> para empresas-versão Premium, existem algumas restrições de cliente: Pode proteger conteúdo e consumir conteúdo protegido com RMS utilizando o Outlook Web App e aplicação de partilha RMS. Pode consumir conteúdo protegido através da utilização de todas as outras aplicações do Office, que inclui o Office Online e as aplicações de cliente para o Office 365 empresas-versão Premium.

### RMS para a subscrição de indivíduos
Esta subscrição foi concebida para os indivíduos da organização que ainda não implementado Azure RMS ou o AD RMS. Permite-estas pessoas ler conteúdo que foi protegido por uma organização que está a utilizar o Azure RMS e também podem proteger os seus próprios conteúdo.

Para obter mais informações, consulte o artigo [RMS para indivíduos e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Diretório do Azure AD
Tem de ter um diretório do Azure AD para utilizar o Azure RMS. Utilizar a sua conta de organização para este diretório para iniciar sessão no Portal de gestão do Azure, onde, por exemplo, pode configurar e gerir modelos de gestão de direitos.

Se ainda não tiver uma subscrição do Azure para a sua organização, pode obter um ao inscrever-se numa avaliação gratuita.: Aceda ao [Azure obter iniciado](https://account.windowsazure.com/organization) página e siga as instruções.

Para obter mais informações, consulte os seguintes recursos na documentação do Azure Active Directory:

-   [O que é um diretório do Azure AD?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Como as subscrições do Azure estão associadas com o Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Se pretende integrar o diretório do Azure AD com o seu no local florestas do AD, consulte o artigo [integração de diretórios](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Se tiver de dispositivos móveis ou computadores Mac que autenticar no local utilizando o AD FS ou um fornecedor de autenticação equivalentes:
> 
> -   É necessário utilizar o AD FS na versão de servidor mínimo de **Windows Server 2012 R2**, ou um fornecedor de autenticação diferente que suporta o protocolo de OAuth 2.0.

### <a name="BKMK_MFA"></a>A autenticação multifator (MFA) e o Azure RMS
Para utilizar a multi-factor authentication (MFA) com o Azure RMS requer pelo menos um dos seguintes procedimentos:

-   Office 2013 (versão mínima):

    -   Se tiver o Office 2013, também tem de instalar o [9 de Junho de 2015, atualizar para o Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Para obter mais informações sobre esta atualização e como autenticação moderna traz baseada na biblioteca de autenticação do Active Directory ADAL início de sessão Office 2013, consulte [Office 2013 autenticação moderna pré-visualização pública comunicada](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)  no blogue do Office.

-   Aplicação partilha Rights Management para Windows:

    -   Tem de ter instalado a versão mínima do 1.0.1908.0, que pode ser confirmado utilizando o painel de controlo, programas e funcionalidades. Para mais informações sobre a aplicação de partilha, consulte o artigo  [Aplicações para Windows de partilha Rights Management](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Aplicação para dispositivos móveis e computadores Mac de partilha Rights Management:

    -   Certifique-se de que tem a versão mais recente instalada. Suporte MFA correu à versão de Setembro de 2015 da aplicação de partilha RMS.

Em seguida, configure a sua solução MFA:

-   Para inquilinos gerido por Microsoft (tiver do Azure Active Directory ou do Office 365):

    -   Configure a MFA do Azure para impor o MFA para os utilizadores. Para obter instruções, consulte o artigo [Introdução ao Azure multi-Factor Authentication na nuvem](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) da documentação do Azure.

        Para obter mais informações sobre a mfa no Azure, consulte o artigo [o que é o multi-Factor Authentication do Azure?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Para inquilinos federados (que operar Federação servidores no local):

    -   Configure os servidores de Federação para o Azure Active Directory ou do Office 365. Por exemplo, se estiver a utilizar o AD FS, consulte o artigo [configurar métodos de autenticação adicionais para o AD FS](https://technet.microsoft.com/library/dn758113.aspx) na TechNet.

        Para obter mais informações sobre este cenário, consulte o artigo  [o funciona com o Office 365 – o programa de identidade está agora mais simples](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) no blogue do Office.

## <a name="BKMK_SupportedDevices"></a>Dispositivos de cliente que suportam o Azure RMS
Utilize as secções seguintes para identificar quais os dispositivos suportam Azure Rights Management (RMS), e as funcionalidades de RMS suportam:

-   [Computadores](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Dispositivos móveis](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Capacidades do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Computadores
Os seguintes sistemas operativos de computador suportar a gestão de direitos do Azure:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Do Mac os X**: Versão mínima do Mac OS X 10.8 (montanha Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Dispositivos móveis
Os seguintes sistemas operativos de dispositivo móvel suportar Azure Rights Management:

-   **Windows Phone**: No Windows Phone 8.1

-   **Android telemóveis e tablets**: Versão mínima do Android 4.0.3

-   **iPhone e iPad**: Versão mínima do iOS 7.0

-   **Tablets Windows RT**: Windows 8 RT, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Capacidades do dispositivo cliente
Nem todos os dispositivos de cliente suportados atualmente suportam todas as capacidades de RMS. Utilize a tabela seguinte para identificar as aplicações que suportam as capacidades de RMS e as exceções.

A menos que indicado caso contrário, as capacidades suportadas aplicam-se para o Azure RMS e AD RMS. Além disso, necessita de suporte de AD RMS no iOS, Android, OS X e Windows Phone 8.1 [Active Directory diretório direitos de gestão de serviços móveis extensão do dispositivo](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informações sobre as colunas da tabela:

-   **Protegidos PDF**: Ficheiros que tenham uma extensão de nome de ficheiro. ppdf e que são criadas automaticamente quando utilizar a aplicação de partilha RMS para partilhar ficheiros do Office e ficheiros PDF por correio eletrónico. A aplicação de partilha RMS inclui um leitor para ficheiros PDF protegidos. Anteriormente, se tiver criado ficheiros PDF protegidos utilizando o Azure RMS ou o AD RMS, pode continuar a ler estes ficheiros em dispositivos Android, iOS e Windows utilizando o Foxit Reader e Nitro Pro.

-   **E-mail:** Os clientes de correio eletrónico listados podem proteger a mensagem de correio eletrónico próprio, que automaticamente irá proteger quaisquer ficheiros anexados. Neste cenário, funcionalidade de pré-visualização do cliente pode apresentar o conteúdo protegido (mensagens e anexos) para os destinatários autorizados. No entanto, se uma mensagem de correio eletrónico próprio não esteja protegida, mas o anexo é protegido, funcionalidade de pré-visualização do cliente não consegue apresentar o anexo protegido para os destinatários autorizados.

-   **Outros tipos de ficheiro**: Ficheiros de texto e imagem incluem ficheiros que tenham uma extensão de nome de ficheiro. txt,. XML,. jpg, e jpeg. Estes ficheiros alterados os respetivos extensão de nome de ficheiro depois de que estão protegidos nativamente pelo RMS e passará a ser só de leitura. Ficheiros que não podem ser protegidos nativamente a ter uma extensão de nome de ficheiro. pfile são protegidos genericamente pela RMS. Para obter mais informações, consulte o [níveis de proteção – nativa e genérica](https://technet.microsoft.com/library/dn339003.aspx) e [tipos de ficheiros e extensões de nome de ficheiro suportados](https://technet.microsoft.com/library/dn339003.aspx) secções a partir de [Guia do administrador aplicação partilha Rights Management](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Sistema operativo do dispositivo**|Word, Excel, PowerPoint|PDF protegido|Correio eletrónico|Outros tipos de ficheiro|
|----------------------------------------|---------------------------|-----------------|----------------------|----------------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Aplicações móveis do Office (apenas Azure RMS)<sup>1</sup><br /><br />Office Online<sup>2</sup>|Documento Gaaiho<br /><br />Ambiente de trabalho GigaTrust cliente PDF do Adobe<br /><br />Foxit Reader<br /><br />Leitor de nitro PDF<br /><br />Aplicação de partilha RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA)<br /><br />Windows Mail<sup>3</sup>|Aplicação para o Windows de partilha RMS: Texto, imagens, ficheiro<br /><br />Siemens JT2Go: Ficheiros JT (apenas no Windows 10)|
|**iOS**|Office para iPad e iPhone<sup>4</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS documentos|Foxit Reader<br /><br />Aplicação de partilha RMS<sup>1</sup><br /><br />TITUS documentos|NitroDesk<br /><br />Outlook para iPad e iPhone<sup>3</sup><br /><br />OWA para iOS<br /><br />Proteger Ilhas IQProtector<sup>1</sup><br /><br />TITUS correio|Aplicação de partilha RMS<sup>1</sup>: Texto, imagens, ficheiro<br /><br />TITUS documentos: Ficheiro|
|**Android**|GigaTrust aplicação para Android<br /><br />Office Online<sup>2</sup>|GigaTrust aplicação para Android<br /><br />Foxit Reader<br /><br />Aplicação de partilha RMS<sup>1</sup>|9Folders<br /><br />GigaTrust aplicação para Android<br /><br />NitroDesk<br /><br />OWA para Android<sup>5</sup><br /><br />E-Mail do Samsung (S3 e posterior)<br /><br />Proteger Ilhas IQProtector<sup>1</sup><br /><br />Classificação de TITUS Mobile|Aplicação de partilha RMS<sup>1</sup>: Texto, imagens, ficheiro|
|**OS X**|Office 2011 (apenas para o AD RMS)<br /><br />2016 do Office para Mac<br /><br />Office Online<sup>2</sup>|Foxit Reader<br /><br />Aplicação de partilha RMS<sup>1</sup>|Outlook 2011 (apenas para o AD RMS)<br /><br />2016 do Outlook para Mac<br /><br />Outlook para Mac|Aplicação de partilha RMS<sup>1</sup>: Texto, imagens, ficheiro|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|Não suportado|Outlook 2013 RT<br /><br />Aplicação correio para Windows<br /><br />Windows Mail<sup>3</sup>|Siemens JT2Go: Ficheiros JT|
|**No Windows Phone 8.1**|Office Mobile (apenas para o AD RMS)|Aplicação de partilha RMS<sup>1</sup>|O Outlook Mobile|Aplicação de partilha RMS<sup>1</sup>: Texto, imagens, ficheiro|
|**BlackBerry 10**|Não suportado|Não suportado|Correio eletrónico BlackBerry<sup>3</sup>|Não suportado|
<sup>1</sup> suporta a visualização de conteúdo protegido.

<sup>2</sup> suporta visualizar conteúdo protegido no SharePoint Online, o OneDrive para empresas e o Outlook Web Access.

<sup>3</sup> utiliza o Exchange ActiveSync IRM, que tem de ser ativada pelo administrador do Exchange. Os utilizadores podem ver, responder e responder a que todos para mensagens de e-mail protegido, mas os utilizadores não é possível proteger novas mensagens de e-mail por si próprios.

<sup>4</sup> suporta a visualização e edição protegidos documentos. Para obter mais informações, consulte a seguinte mensagem no blogue do Office: [Suporte do Azure Rights Management é encaminhado para o Office para iPad e iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>5</sup> para obter mais informações, consulte a seguinte mensagem no blogue do Office: [OWA para Android, agora disponível em determinados dispositivos](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Para obter mais informações sobre o suporte futura do RMS no Office para plataformas diferentes, consulte a seguinte mensagem de blogue do Office: [Office em qualquer lugar, encriptação em qualquer lugar](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Aplicações que suportem o Azure RMS
As seguintes aplicações suportam nativamente o Azure RMS, o que significa que RMS está totalmente integrada para estas aplicações utilizando os APIs de RMS para suportar a restrições de utilização. Estas aplicações também são conhecidas como suportadas por RMS:

-   **Aplicações do Microsoft Office** (Word, Excel, PowerPoint e Outlook) a partir de conjuntos de aplicações do seguinte pode proteger conteúdo através do Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Outras edições do Office (à exceção dos Office 2007) podem consumir conteúdo protegido.

    > [!NOTE]
    > Azure RMS com o Office Professional Plus 2010 ou o Office Professional 2010:
    > 
    > -   Requer a aplicação partilha Rights Management para Windows
    > -   Não é suportado no Windows 10

-   **A aplicação partilha Rights Management para Windows**

    Para mais informações sobre a aplicação de partilha Rights Management para Windows, consulte os seguintes recursos:

    -   [Guia partilha Rights Management aplicação administrador](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Guia de utilizador de aplicação partilha do Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

-   **A aplicação partilha Rights Management para plataformas móveis**

    Para mais informações sobre a aplicação de partilha Rights Management para plataformas móveis, consulte os seguintes recursos:

    -   Transferir a aplicação relevante utilizando as ligações a [página Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Se gerir dispositivos móveis através do Microsoft Intune, pode implementar e configurar a aplicação no [dispositivos iOS e Android como uma política de aplicação gerida por](https://technet.microsoft.com/library/dn878026.aspx).

    -   [FAQ da aplicação para plataformas móveis de partilha Microsoft Rights Management](http://technet.microsoft.com/dn451248)

-   **Outras aplicações que suportam as APIs de RMS**:

    -   Aplicações de linha de negócio que são escritas in-house utilizando o SDK RMS

    -   Aplicações a partir de fornecedores de software que são escritos utilizando o SDK RMS

    Para mais informações sobre o SDK, consulte o [SDK de gestão de direitos do Microsoft](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> As aplicações seguintes não são atualmente suportadas pelo Azure RMS:
> 
> -   Microsoft Office para Mac 2011
> -   Microsoft OneDrive para empresas para o SharePoint Server 2013
> -   Visualizador XPS
> 
> Além disso, a aplicação de partilha RMS tem as seguintes restrições:
> 
> -   Para computadores com Windows: Requer uma versão mínima do Windows 7 Service Pack 1

Para mais informações sobre como estas aplicações suportam o Azure RMS, consulte o artigo [Como as aplicações suportam gestão de direitos do Azure](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Para obter informações sobre como configurá-las, consulte o artigo [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Servidores no local que suportam o Azure RMS
Os seguintes produtos de servidor no local são suportados com o Azure RMS, quando utiliza o conector Azure RMS, que é funciona como uma interface de comunicações (um reencaminhamento) entre os servidores no local e o Azure RMS. Além disso, esta configuração requer que configure a sincronização de diretórios entre as florestas do Active Directory e o Azure Active Directory.

-   **Do exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Do office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Servidores que executam o Windows Server e utilizam a infraestrutura de classificação de ficheiros (FCI) de ficheiros**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Como os servidores de ficheiros que executem o Windows Server 2008 R2 não têm uma ação de tarefa de gestão de ficheiros incorporados para aplicar proteção RMS, não é possível utilizar o conector de RMS para este cenário. No entanto, pode utilizar infraestrutura de classificação de ficheiros e o Azure RMS nestes sistemas de operativos se configurar uma tarefa de gestão de ficheiros personalizadas para executar um executável ou script que pode proteger ficheiros utilizando o Azure RMS. Por exemplo, um script do Windows PowerShell que utiliza o [proteção RMS cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Também pode utilizar estes cmdlets com servidores a executar versões posteriores do Windows Server, com o benefício de que estes cmdlets pode proteger todos os tipos de ficheiro. O conector de RMS protege apenas ficheiros do Office. Para obter instruções sobre como utilizar, consulte o artigo [Proteção RMS com infraestrutura de classificação de ficheiros &#40;FCI&#41; do Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

O conector de RMS é suportado no Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2.

Para obter mais informações sobre como configurar o conector do RMS para estes servidores no local, consulte o artigo [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Consultar Também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

