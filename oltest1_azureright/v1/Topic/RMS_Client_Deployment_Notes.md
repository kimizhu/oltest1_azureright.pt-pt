---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# Notas de implementa&#231;&#227;o do cliente do RMS
A versão do cliente (cliente RMS) do serviço de gestão de direitos 2 também é conhecido como o cliente MSIPC. Este é o software para computadores com Windows que comunica com o Microsoft Rights Management services no local ou na nuvem para o ajudar a proteger o acesso e utilização de informações como flua através de aplicações e dispositivos, dentro dos limites da sua organização ou fora dos geridos limites. Para além de envio com o [aplicações para Windows de partilha Rights Management](https://technet.microsoft.com/library/dn919648.aspx), o cliente RMS está disponível [como uma transferência opcional](http://www.microsoft.com/download/details.aspx?id=38396) que pode, com o reconhecimento e a aceitação do respetivo acordo de licença, ser distribuído gratuitamente com o software de terceiros para que os clientes possam proteger e consumir conteúdo que foi protegido por serviços de gestão de direitos.

Este tópico inclui as secções seguintes:

-   [Redistribuição do RMS](#BKMK_RedistributeInstaller)

-   [Instalar o cliente RMS](#BKMK_InstallClient)

-   [Perguntas e respostas sobre o cliente RMS](#BKMK_QA)

-   [Definições de cliente do RMS](#BKMK_Settings)

-   [Apenas AD RMS: O cliente RMS para utilizar a limitação fidedigna servidores do AD RMS](#BKMK_UsingTrustedServers)

-   [Deteção do serviço de RMS](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Redistribuição do RMS
O cliente RMS pode ser livremente redistribuído e incluído com outras aplicações e soluções de TI. Se for um programador da aplicação ou o fornecedor de soluções e pretende redistribuir o cliente RMS, tem duas opções:

-   Recomendada: Incorporar o instalador do cliente de RMS na instalação da aplicação e executá-lo em modo silencioso (o **/quiet** comutador, detalhada na secção seguinte).

-   Se o cliente RMS um pré-requisito para a sua aplicação. Com esta opção, poderá ter de fornecer aos utilizadores com instruções adicionais que lhes obter, instalar e atualizar os respetivos computadores com o cliente para que possam utilizar a aplicação.

## <a name="BKMK_InstallClient"></a>Instalar o cliente RMS
O cliente RMS está contido num ficheiro executável instalador denominado **setup_msipc_***&lt; arch &gt;***.exe**, onde *&lt; arch &gt;* está **x86** (para computadores de cliente de 32 bits) ou **x64** (para computadores de cliente de 64 bits). O pacote de instalador de 64 bits (x64) instala tanto um runtime de 32 bits executável para compatibilidade com aplicações de 32 bits que são executadas numa instalação de sistema operativo de 64 bits, bem como um runtime de 64 bits executável para suportar aplicações de 64 bits nativas. O instalador de 32 bits (x86) não serão executados numa instalação de Windows de 64 bits.

> [!NOTE]
> Precisa de privilégios elevados para instalar o cliente de RMS, como um membro do grupo Administradores no computador local.

Pode instalar o cliente RMS, utilizando qualquer um dos seguintes métodos de instalação:

-   **Modo silencioso.** Utilizando o **/quiet** mudar como parte das opções da linha de comandos, silenciosamente pode instalar o cliente RMS em computadores. O exemplo seguinte mostra uma instalação em modo silencioso, para o cliente RMS num computador cliente de 64 bits:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Modo interativo.** Em alternativa, pode instalar o cliente RMS utilizando o programa de configuração baseada em GUI fornecida pelo Assistente de instalação de cliente RMS. Para tal, faça duplo clique no pacote de instalador do cliente RMS (**setup_msipc_***&lt; arch &gt;***.exe**) na pasta para o qual foi copiado ou transferido no seu computador local.

## <a name="BKMK_QA"></a>Perguntas e respostas sobre o cliente RMS
A secção seguinte contém as perguntas mais frequentes sobre o cliente RMS e as respostas às mesmas.

### Que sistemas operativos suportam o cliente RMS?
O cliente RMS é suportado com os seguintes sistemas operativos:

|Sistema operativo Windows Server|Sistema operativo cliente Windows|
|------------------------------------|-------------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 com o mínimo de SP1|
|Windows Server 2008 (apenas para o AD RMS)|Windows Vista com mínima do SP2 (apenas para o AD RMS)|

### Que processadores ou plataformas suportam o cliente RMS?
O cliente RMS é suportado em x86 e x64 plataformas de computação.

### Onde está instalado o cliente RMS?
Por predefinição, o cliente RMS está instalado em %ProgramFiles%\Active Directory Rights Management serviços cliente 2. &lt; número da versão secundárias &gt;.

### Os ficheiros estão associados com o software de cliente RMS?
Os ficheiros seguintes estão instalados como parte do software de cliente do RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Para além destes ficheiros, o cliente RMS também instala ficheiros de suporte do utilizador multilingue interface (MUI) em 44 idiomas. Para verificar os idiomas suportados, execute a instalação de cliente RMS e quando a instalação estiver concluída, reveja os conteúdos das pastas de suporte multilingue no caminho predefinido.

### É o cliente RMS incluído por predefinição quando instalo um sistema operativo suportado?
Não. Esta versão do cliente RMS é fornecido como uma transferência opcional que pode ser instalada separadamente nos computadores que executem versões suportadas do sistema operativo Microsoft Windows.

### O cliente RMS é automaticamente atualizado através do Microsoft Update?
Se tiver instalado o cliente RMS utilizando a opção de instalação automática, o cliente RMS herda as definições atuais do Microsoft Update. Se tiver instalado o cliente RMS utilizando o programa de configuração baseada em GUI, o Assistente de instalação de cliente RMS pede-lhe para ativar o Microsoft Update.

## <a name="BKMK_Settings"></a>Definições de cliente do RMS
A secção seguinte contém informações sobre as definições sobre o cliente RMS. Esta informação pode ser útil se tiver problemas com aplicações ou serviços que utilizam o cliente RMS.

> [!NOTE]
> Algumas definições só estão disponíveis se aplicações suportadas por RMS é executado como uma aplicação de modo de cliente (tal como o Microsoft Word e Outlook ou aplicação de partilha RMS) ou a aplicação de modo de servidor (tal como o SharePoint e do Exchange).  Nas seguintes tabelas, estas definições são identificadas como **modo cliente** e **modo servidor**, respetivamente.

### Onde os arquivos de cliente RMS licenças em computadores cliente
O cliente RMS armazena licenças no disco local e também coloca em cache algumas informações no registo do Windows.

|Descrição|Caminhos do modo cliente|Caminhos do modo servidor|
|-------------|----------------------------|-----------------------------|
|Localização do arquivo de licenças|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\*&lt; SID &gt;*\|
|Localização do arquivo de modelo|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\Templates\*&lt; SID &gt;*\|
|Localização do registo|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local definições<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*&lt; SID &gt;*|
> [!NOTE]
> *&lt; SID &gt;* é o identificador de segurança (SID) para a conta sob a qual a aplicação de servidor está em execução. Por exemplo, se a aplicação estiver em execução sob a conta de serviço de rede incorporada, substitua *&lt; SID &gt;* com o valor do SID mais conhecido dessa conta (S-1-5-20).

### Definições de registo do Windows para o cliente RMS
Pode utilizar as chaves de registo do Windows para definir ou modificar algumas configurações de cliente do RMS. Por exemplo, enquanto administrador para aplicações suportadas por RMS que comunicam com servidores AD RMS, pode querer atualizar a localização de serviço de empresa (ignorar o AD RMS server que está selecionado atualmente para publicação) consoante a localização atual do computador cliente na sua topologia do Active Directory. Em alternativa, pode querer ativar o rastreio de RMS do computador cliente, para ajudar a resolver um problema com uma aplicação suportadas por RMS. Utilize a tabela seguinte para identificar as definições de registo que podem ser alteradas para o cliente RMS.

|Tarefa|Definições|
|----------|--------------|
|Apenas AD RMS: Para atualizar a localização de serviço da empresa para um computador cliente|Atualize as seguintes chaves de registo:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: predefinido<br />    **Valor:**&lt; http ou https &gt; :// *RMS_Cluster_Name*/_wmcs/certificação<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: predefinido<br />    **Valor:** &lt; http ou https &gt; :// *RMS_Cluster_Name*/_wmcs/Licensing|
|Para ativar e desativar o rastreio|Atualize a chave de registo seguinte:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Rastreio<br />    **Valor:** 1 para ativar o rastreio, 0 para desativar o rastreio (predefinição)|
|Para alterar a frequência em dias para atualizar os modelos|Os seguintes valores de registo especifique a frequência modelos serão atualizados no computador do utilizador se o valor de TemplateUpdateFrequencyInSeconds não está definido.  Se nenhum destes valores são definido, o intervalo de atualização predefinido para aplicações utilizando o cliente RMS (versão 1.0.1784.0) para transferir modelos é de 1 dia. As versões em versões anteriores de ter um valor predefinido de todos os 7 dias.<br /><br />**Modo cliente:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Valor:** Um valor inteiro que especifica o número de dias (mínimo de 1) entre transferências.<br /><br />**Modo servidor:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Valor:** Um valor inteiro que especifica o número de dias (mínimo de 1) entre transferências.|
|Para alterar a frequência em segundos para atualizar os modelos **Important:** Se este for especificado, o valor para atualizar os modelos em dias é ignorado. Especifique um ou outro, não ambos.|Os seguintes valores de registo especifique a frequência modelos serão atualizados no computador do utilizador. Se este valor ou o valor para alterar a frequência nos dias (TemplateUpdateFrequency) não estiver definido, o intervalo de atualização predefinido para aplicações utilizando o cliente RMS (versão 1.0.1784.0) para transferir modelos é de 1 dia. As versões em versões anteriores de ter um valor predefinido de todos os 7 dias.<br /><br />**Modo cliente:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Valor:** Um valor inteiro que especifica o número de segundos (mínimo de 1), entre as transferências.<br /><br />**Modo servidor:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Valor:** Um valor inteiro que especifica o número de segundos (mínimo de 1), entre as transferências.|
|Apenas AD RMS: Para transferir modelos imediatamente no pedido de publicação seguinte|Durante o teste e avaliações, poderá pretender que o cliente RMS para transferir modelos com a brevidade possível. Para tal, remova a seguinte chave de registo e o cliente RMS irá transferir modelos imediatamente no pedido de publicação seguinte, em vez de aguardar na hora especificada pela definição de registo TemplateUpdateFrequency:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; nome do servidor &gt; \Template **Note:** &lt; nome do servidor &gt; pode ter externos (corprights.contoso.com) e URLs de internos (corprights) e, por conseguinte, duas entradas diferentes.|
|Apenas AD RMS: Para ativar o suporte para autenticação federada|Se o computador de cliente RMS estiver ligado a um cluster do AD RMS, utilizando uma confiança federada, tem de configurar o realm inicial da Federação.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: FederationHomeRealm<br />    **Valor:** O valor desta entrada de registo é o uniform resource identifier (URI) para o serviço de Federação (por exemplo, "https://fs-01.contoso.com").|
|Apenas AD RMS: Para suportar servidores de Federação parceiros que exigem autenticação baseada em formulários para intervenção do utilizador|Por predefinição, o cliente RMS funciona em modo silencioso e não é necessária a intervenção do utilizador. Servidores de Federação parceiros, no entanto, poderão ser configurados para exigir a intervenção do utilizador, por exemplo, através da autenticação baseada em formulários. Neste caso, tem de configurar o cliente RMS ignorar modo silencioso, para que o formulário de autenticação federada, é apresentado numa janela do browser e o utilizador seja promovido para autenticação.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Se o servidor de Federação estiver configurado para utilizar a autenticação baseada em formulários, esta chave é necessária. Se o servidor de Federação estiver configurado para utilizar a autenticação integrada do Windows, esta chave não é necessária.|
|Apenas AD RMS: Para bloquear o consumo de serviço ILS|Por predefinição, o cliente RMS ativa consumo conteúdo protegido pelo serviço ILS mas também pode configurar o cliente para bloquear este serviço definindo a seguinte chave de registo. Se esta chave de registo é definida para bloquear o serviço ILS, todas as tentativas para abrir e consumir conteúdo protegido pelo serviço ILS irão devolver o seguinte erro:<br />hresult_from_win32 (error_access_disabled_by_policy)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Valor:** 1 para bloquear o consumo de ILS, 0 para permitir o consumo de ILS (predefinição)|

### Gerir a distribuição de modelos para o cliente RMS
Modelos tornam mais fácil para os utilizadores e administradores para aplicar rapidamente a proteção de gestão de direitos e o cliente RMS transfere automaticamente modelos do respetivo servidores RMS ou o serviço se colocar os modelos na seguinte localização de pasta, o cliente RMS não transferirá qualquer modelo a partir da localização predefinida e transferir em vez disso, os modelos que tem de colocar nesta pasta. O cliente RMS poderá continuar a transferir modelos a partir de outros servidores de RMS disponíveis.

**Modo cliente:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Modo servidor:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; SID &gt;*

Quando utiliza esta pasta, não existe nenhuma convenção de nomenclatura especial necessária, exceto que os modelos devem ser emitidos pelo servidor RMS ou o serviço e tem de ter a extensão de nome de ficheiro. XML. Por exemplo, Contoso-CONFIDENTIAL. XML ou Contoso-ReadOnly são os nomes válidos.

## <a name="BKMK_UsingTrustedServers"></a>Apenas AD RMS: O cliente RMS para utilizar a limitação fidedigna servidores do AD RMS
O cliente RMS pode ser limitado à utilização apenas específicos servidores AD RMS fidedignos efetuando as seguintes alterações para o registo do Windows nos computadores locais.

**Para ativar a limitação de RMS cliente para utilizar apenas servidores AD RMS de fidedignos**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Valor:** Se não for especificado um valor diferente de zero, o cliente RMS confiará apenas nos servidores especificados que estejam configurados na lista de TrustedServers e o serviço Azure Rights Management.

**Para adicionar membros à lista de servidores AD RMS fidedignos**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt; URL_or_HostName &gt;*

    **Valor:** Os valores de cadeias adicionados nesta localização da chave de registo podem ter um formato de nome de domínio DNS (por exemplo, **adrms.contoso.com**) ou completas URLs para servidores AD RMS fidedignos (por exemplo, **https://adrms.contoso.com**). Se um URL especificado for iniciado com **https://**,  o cliente RMS irá utilizar SSL ou TLS para contactar o servidor AD RMS especificado.

## <a name="BKMK_ServiceDiscovery"></a>Deteção do serviço de RMS
Deteção do serviço de RMS permite que o cliente RMS verificar qual servidor RMS ou o serviço para comunicar com antes de proteger conteúdo. Deteção do serviço também poderá acontecer se o cliente RMS consumir conteúdo protegido, mas é menos provável acontecer porque a política anexada ao conteúdo contém o serviço ou o servidor preferencial do RMS e apenas se que não for bem-sucedida o cliente, em seguida, executa a deteção do serviço.

Deteção do serviço de procura pela primeira vez uma versão no local do Rights Management (AD RMS). Se não for bem-sucedida, deteção de serviço de procura automaticamente a versão de nuvem do Rights Management (RMS do Azure).

Para efetuar a deteção de serviço para uma implementação no local, o cliente RMS verifica o seguinte:

1.  O registo do Windows no computador local: Se as definições de deteção de serviço estiverem configuradas no registo, estas definições são experimentadas em primeiro lugar.  Por predefinição, estas definições não estão configuradas no registo.

2.  Serviços de domínio do Active Directory: Um computador associado a um domínio consulta o Active Directory para um ponto de ligação de serviço (SCP). Se está registado um SCP, é devolvido o URL do servidor do RMS para o cliente RMS para utilizar.

### Apenas AD RMS: Ativar a deteção de serviços do lado do servidor através da utilização do Active Directory
Se a sua conta tem privilégios suficientes (Admins de empresa e um administrador local para o servidor AD RMS), pode registar automaticamente um um ponto de ligação de serviço (SCP) quando instala o servidor de cluster de raiz AD RMS. Se já existir um SCP na floresta, primeiro deve eliminar o SCP existente antes de pode registar um novo.

Pode registar e eliminar um SCP depois de AD RMS estiver instalado utilizando o procedimento seguinte. Antes de começar, certifique-se de que a conta tem os privilégios necessários (Admins de empresa e um administrador local para o servidor AD RMS).

##### Para ativar a deteção de serviço do AD RMS ao registar um SCP no Active Directory

1.  Abra a consola de serviços de gestão do Active Directory no servidor do AD RMS:

    -   Se estiver a utilizar o Windows Server 2008 R2 ou Windows Server 2008, clique em **Iniciar**, clique em **Ferramentas administrativas**, e, em seguida, clique em **Serviços de gestão de direitos do Active Directory**.

    -   Se estiver a utilizar Windows Server 2012 R2 ou Windows Server 2012, no Gestor de servidor, clique em **ferramentas**, e, em seguida, clique em **Serviços de gestão de direitos do Active Directory**.

2.  Na consola do AD RMS com o botão direito do cluster do AD RMS e, em seguida, clique em **Propriedades**.

3.  Clique na **SCP** separador.

4.  Selecione o **Alterar SCP** caixa de verificação.

5.  Selecione o **Definir SCP para o cluster de certificação atual** opção e, em seguida, clique em **OK**.

### Ativar a deteção de serviços do lado do cliente, utilizando o registo do Windows
Como alternativa à utilização de um SCP ou onde não existe um SCP, pode configurar o registo no computador cliente para que o cliente RMS possa localizar o servidor AD RMS.

##### Para ativar a deteção de serviço de AD RMS do lado do cliente, utilizando o registo do Windows

1.  Abra o editor de registo do Windows, Regedit.exe:

    -   No computador cliente, na janela executar, escreva **regedit**, e, em seguida, prima ENTER para abrir o Editor de registo.

2.  No Editor de registo, navegue para **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Se estiver a executar uma aplicação de 32 bits num computador de 64 bits, o caminho será da seguinte forma: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Para criar a subchave ServiceLocation, com o botão direito **MSIPC**, aponte para **novo**, clique em **chave**, e, em seguida, escreva **ServiceLocation**.

4.  Para criar a subchave EnterpriseCertification, com o botão direito **ServiceLocation**, aponte para **novo**, clique em **chave**, e, em seguida, escreva **EnterpriseCertification**.

5.  Para definir o URL de certificação da empresa, faça duplo clique a **(predefinição)** valor no **EnterpriseCertification** subchave e quando o **Editar cadeia** aparece a caixa de diálogo, para **dados do valor**, tipo &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification, e, em seguida, clique em **OK**.

6.  Para criar a subchave EnterprisePublishing, com o botão direito **ServiceLocation**, aponte para **novo**, clique em **chave**, e, em seguida, escreva EnterprisePublishing.

7.  Para definir a empresa URL de publicação, faça duplo clique em **(predefinição)** , no **EnterprisePublishing** subchave e quando o **Editar cadeia** aparece a caixa de diálogo, escreva para **dados do valor** seguintes &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing, e, em seguida, clique em **OK**.

8.  Feche o Editor de registo.

Se o cliente RMS não é possível localizar um SCP através da consulta do Active Directory e não está especificado no registo, chamadas de deteção de serviço para o AD RMS irão falhar.

### Redirecionar o tráfego do servidor de licenciamento
Em alguns casos, poderá ser necessário redirecionar o tráfego durante a deteção de serviço, por exemplo, quando duas organizações são fundidas e o servidor de licenciamento antigo na uma organização estiver retirado e os clientes que devem ser redirecionado para um novo servidor de licenciamento. Em alternativa, migrar do AD RMS para o Azure RMS. Para ativar o redirecionamento do licenciamento, utilize o procedimento seguinte.

##### Para ativar RMS licenciamento redirecionamento utilizando o registo do Windows

1.  Abra o editor de registo do Windows, Regedit.exe:

    -   No computador cliente, na janela executar, escreva **regedit**, e, em seguida, prima ENTER para abrir o Editor de registo.

2.  No Editor de registo, navegue até um dos seguintes procedimentos:

    -   Para a versão de 64 bits do Office em x64 plataforma: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Para a versão de 32 bits do Office em x64 plataforma: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Criar uma subchave LicensingRedirection, clicando com o **Servicelocation**, aponte para **novo**, clique em **chave**, e, em seguida, escreva **LicensingRedirection**.

4.  Para configurar o redirecionamento do licenciamento, com o botão direito do **LicensingRedirection** subchave, selecione **novo**, e, em seguida, selecione **valor de cadeia**.  Para **nome**, especifique o URL de licenciamento do servidor anterior e para **valor** especificar o URL de licenciamento do servidor novo.

    Por exemplo, para redirecionar licenciamento a partir de um servidor de Contoso.com, para uma de cada Fabrikam.com, poderá introduzir os seguintes valores:

    **Nome:** `https://contoso.com/_wmcs/licensing`

    **Valor:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Se tiver o antigo servidor de licenciamento de intranet e extranet URLs especificado, em seguida, um novo nome e mapeamento de valor tem de ser definido para os dois URL sob a chave LicensingRedirection.

5.  Repita o passo anterior para todos os servidores que necessitam de ser redirecionados.

6.  Feche o Editor de registo.

