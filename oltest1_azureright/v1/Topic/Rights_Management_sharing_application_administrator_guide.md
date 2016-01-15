---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Guia partilha Rights Management aplica&#231;&#227;o administrador
Utilize as seguintes informações se for responsável pela partilha de aplicações numa rede empresarial do Microsoft Rights Management, ou se pretender mais informações técnicas que está a ser o [Guia de utilizador de aplicação partilha do Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md) ou [FAQ do Microsoft Rights Management partilha de aplicações para Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Implementação automática para a aplicação de partilha do Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Verificar o êxito da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Comandos de desinstalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Suprimir atualizações automáticas](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Azure RMS: Configurar o controlo de documento](#BKMK_DocumentTracking)

    -   [Apenas AD RMS: Suporte para múltiplos domínios de e-mail da sua organização](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Descrição geral técnica para a aplicação de partilha do Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Níveis de proteção – nativa e genérica](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Tipos de ficheiro suportados e extensões de nome de ficheiro](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Alterar o nível de proteção predefinida dos ficheiros](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Se estiver familiarizado com a aplicação de partilha RMS, ou ao procurar para obter mais informações, consulte o artigo [forma o RMS protege todos os tipos de ficheiro-ao utilizar a aplicação de partilha RMS](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

A aplicação de partilha RMS é mais adequada para o seu trabalho com o Azure RMS, porque esta configuração de implementação suporta anexos protegidos envio para os utilizadores na outra organização e as opções, como notificações por correio eletrónico e documentos com a revogação de controlo.  No entanto, com algumas limitações, também funciona com a versão no local, o AD RMS. Para uma comparação completa das funcionalidades que são suportadas pelo Azure RMS e AD RMS, consulte o artigo [Comparar Azure Rights Management e o AD RMS](https://technet.microsoft.com/library/jj739831.aspx). Se tiver o AD RMS e pretende migrar para o Azure RMS, consulte o artigo [Migrar do AD RMS para o Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Implementação automática para a aplicação de partilha do Microsoft Rights Management
A versão do Windows da aplicação de partilha RMS suporta uma instalação encriptada, o que torna adequado para implementações empresariais.

Os únicos pré-requisitos para instalações são os computadores executarem a versão mínima do Windows 7 Service Pack 1 e que o Microsoft Framework, versão mínima 4.0 está instalado. Se precisar de instalar o Microsoft .NET Framework 4.0, pode [transferi-lo para instalação a partir de Center Download Microsoft](http://www.microsoft.com/download/details.aspx?id=17718).

#### Para transferir a aplicação para implementação automática de partilha RMS

1.  Aceda ao [aplicações para Windows de partilha Microsoft Rights Management](http://www.microsoft.com/download/details.aspx?id=40857) página no Center Download Microsoft e clique em **Transferir**.

2.  Selecione e transferir os ficheiros de que precisa. Existem dois pacotes de instalação de cliente: um para Windows de 64 bits (Microsoft Rights Management partilha aplicação x64.zip) e outro para Windows de 32 bits (Microsoft Rights Management x86.zip de aplicação de partilha).

3.  Extraia os ficheiros a partir de pacotes de instalação comprimidos, por exemplo, fazendo duplo clique neles. Em seguida, copie os ficheiros extraídos para uma localização de rede que podem aceder a computadores cliente.

Os pacotes de configuração para a aplicação de partilha RMS suporta diferentes cenários de implementação e incluem o seguinte:

|Descrição|Cenário de implementação|
|-------------|----------------------------|
|Assistente de início de sessão Online do Microsoft|Necessário para o seguinte:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2013 e Azure RMS se não tiver instalado o [9 de Junho de 2015, atualizar para o Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Correção para Office (KB 2596501)|Necessário para o seguinte:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e do Active Directory RMS|
|Correção para ativar o AD RMS Client 1.0 funcionar com o Azure RMS (KB 2843630)|Necessário para o seguinte:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e do Active Directory RMS|
|Cliente de AD RMS e aplicação de partilha RMS|Necessário para o seguinte:<br /><br />-   Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e do Active Directory RMS<br />-   Suplemento Office só e aplicação de partilha RMS|
|Suplemento do Office para o Friso|Necessário para o seguinte:<br /><br />-   Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e do Active Directory RMS<br />-   Suplemento Office só e aplicação de partilha RMS|
|Ferramenta de preparação do Azure Active Directory Rights Management|Necessário para o seguinte:<br /><br />-   Office 2010 e Azure RMS|
Utilize os procedimentos seguintes para identificar os comandos necessários para implementar a aplicação para estes cenários de implementação de partilha RMS:

-   **Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS**

    Os utilizadores estão a executar Office 2016 ou o Office 2013, a organização utiliza o Azure RMS ou Active Directory RMS e os utilizadores colaboram com outras organizações que utilizam o Azure RMS ou Active Directory RMS.

-   **Office 2010 e Azure RMS**

    Os utilizadores estão a executar o Office 2010, a organização utiliza o Azure RMS e os utilizadores colaboram com outras organizações que utilizam o Azure RMS ou Active Directory RMS.

-   **Office 2010 e do Active Directory RMS**

    Os utilizadores estão a executar o Office 2010, a organização utiliza o AD RMS e os utilizadores colaboram com outras organizações que utilizam o Azure RMS.

-   **Suplemento Office só e aplicação de partilha RMS**

    Os utilizadores estão a executar 2016 do Office, Office 2013 ou Office 2010, a organização utiliza o AD RMS e os utilizadores não precisam de colaborar com outras organizações que utilizam o Azure RMS. Esta instalação permite instalar apenas a partilha de aplicações e suplemento do Office.

> [!NOTE]
> Nestes cenários, se a sua organização estiver a executar o AD RMS, os utilizadores podem receber conteúdo protegido de outras organizações que utilizam o Azure RMS, mas os seus utilizadores não é possível enviar protegidos conteúdo para utilizadores numa organização que utiliza o Azure RMS. No entanto, se a sua organização estiver a executar o Azure RMS, os utilizadores podem enviar e receber conteúdo protegido de outras organizações.

Para concluir a instalação para cada procedimento, tem de reiniciar o computador. Pode iniciar um reinício automático utilizando um comando como shutdown /i.

#### Para implementar a aplicação para o Office 2016 ou o Office 2013 e o Azure RMS ou o Active Directory RMS de partilha RMS

-   Em cada computador no qual pretende instalar a aplicação e componentes relacionados de partilha RMS, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s
    ```

Para verificar o êxito, consulte o [Verificar o êxito da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) deste tópico.

#### Para implementar a aplicação do Office 2010 e Azure RMS de partilha RMS

1.  Tem de ser o administrador global do seu inquilino do Office 365 ou do Azure Active Directory, de modo a que pode obter o URL do serviço de certificação da sua organização ao executar a ferramenta de preparação do Azure Active Directory Rights Management. Tem de executar esta ferramenta apenas uma vez, num único computador. Irá utilizar o URL do serviço de certificação ao instalar aplicação em cada computador de partilha RMS:

    1.  Inicie sessão computador utilizando uma conta de administrador local.

    2.  Nesse computador, [Transferir e instalar o início de sessão no Assistente do Microsoft Online](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Execute o seguinte comando para ver apresentado no ecrã o URL de serviço de certificação que pode, em seguida, copiar e guardar para o passo seguinte:

        -   Para o Windows 8.1 e Windows 8, 64 bits:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para o Windows 8.1 e Windows 8, 32 bits:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para o Windows 7, 64 bits:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Este comando pode pedir-lhe para introduzir as suas credenciais para o Azure. Se o computador não estiver associado a um domínio, será solicitado. Se o computador estiver associado a um domínio, a ferramenta poderá ser possível utilizar credenciais em cache.

2.  Em cada computador no qual irá instalar a aplicação de partilha RMS, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Em cada computador no qual irá instalar a aplicação de partilha RMS, os utilizadores tem de executar o seguinte comando (não necessita de privilégios elevados). Existem várias formas de efetuar este procedimento, incluindo pedir aos utilizadores para executarem o comando (por exemplo, numa ligação na mensagem de correio eletrónico ou uma ligação no portal de suporte técnico) ou pode adicioná-la ao respetivo script de início de sessão:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Para verificar o êxito, consulte o [Verificar o êxito da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) deste tópico.

#### Para implementar a aplicação do Office 2010 e Active Directory RMS de partilha RMS

1.  Em cada computador no qual irá instalar a aplicação de partilha RMS, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Em cada computador no qual irá instalar a aplicação de partilha RMS, os utilizadores tem de executar o seguinte comando (não necessita de privilégios elevados). Existem várias formas de efetuar este procedimento, incluindo pedir aos utilizadores para executarem o comando (por exemplo, numa ligação na mensagem de correio eletrónico ou uma ligação no portal de suporte técnico) ou pode adicioná-la ao respetivo script de início de sessão:

    -   Para o Windows 10, Windows 8.1 e Windows 8, 64 bits:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Para o Windows 10, Windows 8.1 e Windows 8, 32 bits:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Para o Windows 7, 64 bits:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Para verificar o êxito, consulte o [Verificar o êxito da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) deste tópico.

#### Para instalar a aplicação de partilha RMS e o Office suplemento apenas

1.  Instale o cliente AD RMS e aplicação de partilha RMS utilizando o seguinte comando:

    -   Para o Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para o Windows de 32 bits:

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

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Para verificar o êxito, consulte o [Verificar o êxito da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) deste tópico.

### <a name="BKMK_verifyscripted"></a>Verificar o êxito da instalação
Pode utilizar os ficheiros de registo de instalação para verificar uma instalação com êxito.

##### Para verificar o êxito da instalação da aplicação para o Office 2016 ou o Office 2013 e o Azure RMS ou o Active Directory RMS de partilha RMS

-   Para verificar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação **Rminstaller** no *%temp%\RMS_installer_ &lt; guid &gt;* pasta e, em seguida, identifique o código de saída.

    Uma instalação com êxito tem um código de saída de 0 e qualquer outro número indica uma falha na instalação.

    Nome do ficheiro de registo de exemplo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Para verificar o êxito da instalação da aplicação do Office 2010 e Azure RMS de partilha RMS

1.  Para verificar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação **Rminstaller** no *%temp%\RMS_installer_ &lt; guid &gt;* pasta e, em seguida, identifique o código de saída.

    Uma instalação com êxito tem um código de saída de 0 e qualquer outro número indica uma falha na instalação.

    Nome do ficheiro de registo de exemplo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para verificar o êxito do comando RMSSetup.exe, o utilizador deve ter os seguintes ficheiros criados no respetivo *%localappdata%\microsoft\drm* pasta:

    -   CERTIFICADO-máquina-2048.drm

    -   CERTIFICADO Machine.drm

    -   Ficheiro CLC-&#42;.drm

    -   GIC &#42;.drm

    Exemplo de um ficheiro CLC-&#42;. DRM:

    **.Drm CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf; k5b11; k4a10; kac15; k29b2b6980f4c}**

##### Para verificar o êxito da instalação da aplicação do Office 2010 e Active Directory RMS de partilha RMS

1.  Para verificar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação no *%temp%\RMS_installer_ &lt; guid &gt;* pasta e o identifique o código de saída.

    Uma instalação com êxito tem um código de saída de 0 e qualquer outro número indica uma falha na instalação.

    Nome do ficheiro de registo de exemplo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para verificar o êxito do comando aadrmprep.exe, em cada computador, procure o seguinte texto no ficheiro de registo de instalação: **aadrmprep.exe. exe saiu com o estado êxito**

    > [!NOTE]
    > Por vezes, esta instalação pode ser executada duas vezes; a primeira ocorrência falha e a segunda tem êxito.

    Se pretender verificar manualmente as alterações de registo efetuadas por esta ferramenta, são os seguintes:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @= "&lt; url de certificação &gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser = "&lt; default_user &gt;"

##### Para verificar o êxito da instalação da aplicação e do suplemento Office apenas de partilha RMS

1.  Para verificar o êxito do comando Setup_ipviewer.exe, procure o seguinte texto no ficheiro de registo de instalação: **Estado de êxito ou erro de instalação: 0**

    Linhas de exemplo de uma instalação com êxito:

    **MSI (s) (F0:B8) [14:19:57:854]: Produto: Active Directory Rights Management Services Client 2.1-- instalação concluída com êxito.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer instalou o produto. Nome do produto: Do Active Directory Rights Management Services Client 2.1. Versão do produto: 1.0.1179.1. Idioma do produto: 1033. Fabricante: Microsoft Corporation. Estado de êxito ou erro de instalação: 0.**

2.  Para verificar o êxito do suplemento Office, em cada computador, procure o seguinte texto no ficheiro de registo de instalação: **Estado de êxito ou erro de instalação: 0**

    Linhas de exemplo de uma instalação com êxito:

    **MSI (s) (9C: 88) [18:49:04:007]: Produto: Suplementos do Microsoft Office para RMS - Instalação concluída com êxito.**

    **MSI (s) (9C: 88) [18:49:04:007]: Windows Installer instalou o produto. Nome do produto: Suplementos do Microsoft Office para RMS. Versão do produto: 1.0.7. Idioma do produto: 1033. Fabricante: Microsoft. Estado de êxito ou erro de instalação: 0.**

### <a name="BKMK_uninstallscripted"></a>Comandos de desinstalação
Nem todos os comandos de instalação que são necessários para estas implementações suportam um comando de desinstalação. Pode desinstalar o cliente de AD RMS e a aplicação de partilha e pode desinstalar o suplemento do Office. Utilize os seguintes comandos para desinstalar estes elementos.

##### Para desinstalar o cliente AD RMS e aplicação de partilha RMS

-   Utilize os seguintes comandos:

    -   Para o Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Para o Windows de 32 bits:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Para desinstalar o suplemento do Office

-   Utilize os seguintes comandos:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Suprimir atualizações automáticas
Por predefinição, os utilizadores são notificados se existir uma versão posterior da aplicação de partilha RMS e lhe for pedidos para transferi-lo. Pode suprimir esta notificação ao efetuar a edição de registo seguinte:

1.  Navegue para **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e se ainda não existir, crie uma nova chave denominada **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo valor DWORD de **AllowUpdatePrompt**, e defina o valor como **0**.

Uma vez que a aplicação de partilha RMS não é suportada pelo WSUS, pode utilizar a seguinte técnica para testar quaisquer versões novas da aplicação antes de o implementar para todos os utilizadores de partilha RMS:

1.  Em computadores de todos os utilizadores, execute um script para suprimir atualizações automáticas. Nos computadores que os administradores utilizar para testar novas versões, não execute este script.

2.  Quando estiver disponível uma nova versão, os administradores transferem-lo e testá-la.

3.  Quando os testes são concluídos e todos os problemas resolvidos, implemente a versão mais recente a todos os utilizadores utilizando as instruções de implementação automática neste guia.

### <a name="BKMK_DocumentTracking"></a>Azure RMS: Configurar o controlo de documento
Se tiver um [subscrição que suporta o controlo de documento](https://technet.microsoft.com/en-us/dn858608), de monotorização de documentos site está ativado por predefinição para todos os utilizadores na sua organização.  Documento controlo mostra informações tais como endereços de correio eletrónico das pessoas que tentaram aceder a documentos protegidos que os utilizadores partilhados, quando estas pessoas tentaram aceder-lhes e a respetiva localização. Se apresentar esta informação é proibida na sua organização devido a requisitos de privacidade, pode desativar o acesso ao documento de controlo do site utilizando o  [desativar AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) cmdlet. Pode ativar novamente o acesso ao site em qualquer altura, utilizando o [Ativar AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), e pode verificar se o access atualmente é ativado ou desativado utilizando [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Para executar estes cmdlets, tem de ter, pelo menos, versão **2.3.0.0** do módulo Azure RMS para o Windows PowerShell.  Para instruções de instalação, consulte o artigo [instalar o Windows PowerShell para o Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Se anteriormente tiver transferido e instalado o módulo, verifique o número da versão executando: `(Get-Module aadrm –ListAvailable).Version`

Dos seguintes URLs são utilizados para controlo de documento e tem de ser permitidos (por exemplo, adicioná-los aos seus Sites fidedignos se estiver a utilizar o Internet Explorer com segurança avançada do):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > este URL é para mapas do Bing.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Apenas AD RMS: Suporte para múltiplos domínios de e-mail da sua organização
Se utilizar o AD RMS e os utilizadores na sua organização tiverem múltiplos domínios de e-mail, talvez, como resultado uma fusão ou aquisição, tem de efetuar a edição de registo seguinte:

1.  Navegue para **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e se ainda não existir, crie uma nova chave denominada **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo valor de cadeia múltipla denominado **FederatedDomains**, e, em seguida, adicione os domínios e todos os subdomínios que a organização utiliza. Carateres universais não são suportadas.

    Por exemplo: A empresa Coho Vineyard &amp; Winery tem um domínio de e-mail **cohovineyardandwinery.com**, mas como resultado de fusões, utiliza também os domínios de e-mail **cohowinery.com**, **eastcoast.cohowinery.com**, e **cohovineyard**. Para o **FederatedDomains** dados de valor, o administrador introduz: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Se não efetuar esta alteração ao registo, os utilizadores poderão não conseguir consumir o conteúdo que foi protegido por outros utilizadores na organização. A edição de registo não é necessária se utilizar o Azure RMS.

## <a name="BKMK_AdminOverview"></a>Descrição geral técnica para a aplicação de partilha do Microsoft Rights Management
A aplicação de partilha do Microsoft Rights Management é uma aplicação transferível e opcional para o Microsoft Windows e outras plataformas que fornece o seguinte:

-   Proteção de um ficheiro individual ou em massa de vários ficheiros, bem como todos os ficheiros numa pasta selecionada.

-   Suporte integral para proteção de qualquer tipo de ficheiro e um visualizador incorporado para tipos de ficheiro de texto e imagem utilizados frequentemente.

-   Proteção genérica para ficheiros que não suportam a proteção RMS.

-   Interoperabilidade completa com ficheiros protegidos utilizando a gestão de direitos de informação (IRM) do Office.

-   Interoperabilidade completa com ficheiros PDF protegidos utilizando SharePoint, FCI e ferramentas de criação de PDF suportadas.

A aplicação de partilha do Microsoft Rights Management utiliza a nova [AD RMS Client 2.1 runtime](http://www.microsoft.com/download/details.aspx?id=38396). Utilizando a funcionalidade do AD RMS 2.1, a aplicação de partilha do Microsoft Rights Management fornece aos utilizadores finais uma simple proteção e experiência de consumo.

Com a versão do RMS de Outubro de 2013, pode proteger documentos ao utilizar o Office 2010 e enviá-los para pessoas noutra empresa, que pode consumi-los utilizando o Azure RMS nativamente. Além disso, com esta versão, se utilizar o AD RMS no modo criptográfico 2, pode utilizar RMS para indivíduos e consumir conteúdo de pessoas noutra empresa que utiliza o Azure RMS. Para mais informações sobre o modo criptográfico 2, consulte o artigo [modos criptográficos do AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Níveis de proteção – nativa e genérica
Aplicação de partilha Microsoft Rights Management suporta proteção a dois níveis diferentes, conforme descrito na seguinte tabela.

|Tipo de proteção|Nativo|Genérico|
|--------------------|----------|------------|
|Descrição|Para texto, imagem, Microsoft Office (Word, Excel, PowerPoint) ficheiros, ficheiros. pdf e outros tipos de ficheiro de aplicação que suportam o AD RMS, a proteção nativa fornece um nível de proteção que inclui a encriptação de ambas as forte e imposição de direitos (permissões).|Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece um nível de proteção que inclui o encapsulamento de ficheiro com o tipo de ficheiro. pfile e autenticação para verificar se um utilizador está autorizado a abrir o ficheiro.|
|Proteção|Os ficheiros são totalmente encriptados e proteção é imposta da seguinte forma:<br /><br />-   Antes do conteúdo protegido é composto, é necessário ocorrer uma autenticação com êxito para aqueles que receber o ficheiro através de correio eletrónico ou que têm acesso ao mesmo através do ficheiro ou uma partilha de permissões.<br />-   Além disso, direitos de utilização e a política de definidos pelo proprietário do conteúdo quando os ficheiros são protegidos são impostos na totalidade quando o conteúdo é composto no Visualizador de IP (para os ficheiros de texto e de imagem protegidos) ou na aplicação associada (para todos os outros tipos de ficheiro suportados).|Proteção de ficheiros é imposta da seguinte forma:<br /><br />-   Antes de conteúdo protegido é composto, autenticação com êxito tem de ocorrer para aqueles que estão autorizados a abrir o ficheiro e que lhe têm acesso ao mesmo. Se a autorização falhar, o ficheiro não abrir.<br />-   Direitos de utilização e a política de definidos pelo proprietário do conteúdo são apresentados para informar os utilizadores autorizados da política de utilização.<br />-   Registo de auditoria dos utilizadores autorizados a abrir e aceder aos ficheiros ocorre, no entanto, sem direitos de utilização são impostos pelo que não suporta aplicações.|
|Predefinição para tipos de ficheiro|Este é o nível predefinido de proteção para os seguintes tipos de ficheiro:<br /><br />-   Ficheiros de texto e imagem<br />-   Ficheiros do Microsoft Office (Word, Excel, PowerPoint)<br />-   Formato Portable document Format (. pdf)<br /><br />Para mais informações, consulte a secção seguinte, [Tipos de ficheiro suportados e extensões de nome de ficheiro](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Esta é a proteção predefinida para todos os outros tipos de ficheiro (tal como. vsdx,. rtf etc.) não suportada pela proteção total.|
Pode alterar o nível de proteção predefinida que se aplica a aplicação de partilha RMS. Pode alterar o nível predefinido de nativa para genérica, de genérica para nativa e até mesmo evitar que a aplicação a partir da aplicação de proteção de partilha RMS. Para obter mais informações, consulte o [Alterar o nível de proteção predefinida dos ficheiros](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) deste tópico.

### <a name="BKMK_SupportFileTypes"></a>Tipos de ficheiro suportados e extensões de nome de ficheiro
A tabela seguinte lista os tipos de ficheiros que são suportados nativamente pela aplicação de partilha Microsoft Rights Management. Para estes tipos de ficheiro, a extensão de nome de ficheiro original é alterada quando a proteção nativa é aplicada e esses ficheiros passam a ser só de leitura.

Além disso, quando a aplicação de partilha RMS nativamente protege um ficheiro do Word, Excel ou PowerPoint que os utilizadores protegem ao partilhar, esta ação cria automaticamente um segundo ficheiro que é uma cópia do original com o mesmo nome de ficheiro, mas com um **. ppdf** ¹ de extensão de nome de ficheiro. Esta versão do ficheiro garante que os destinatários que instalam a aplicação de partilha RMS possam abrir sempre o ficheiro que tem proteção nativa aplicada.

Para ficheiros que estão protegidos genericamente, a extensão de nome de ficheiro original é sempre alterada para. pfile.

> [!WARNING]
> Se tiver firewalls, web proxies ou software de segurança que analisa e toma ações de acordo com as extensões de nome de ficheiro, poderá ter reconfigurá-los para suportar estas novas extensões de nome de ficheiro.

|Extensão de nome de ficheiro original|Extensão de nome de ficheiro protegido por RMS|
|-----------------------------------------|--------------------------------------------------|
|. txt|. ptxt|
|. XML|.pxml|
|. jpg|. pjpg|
|. JPEG|.ppng|
|. pdf|. ppdf|
|. png|.ppng|
|. tiff|.ptiff|
|. bmp|.pbmp|
|. gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.JT|.pjt|
Com tecnologia Foxit ¹ composição de PDF. Copyright © 2014 – 2003 Foxit Corporation.

A tabela seguinte lista os tipos de ficheiro que a aplicação de partilha Microsoft Rights Management suporta nativamente no Microsoft Office 2016, Office 2013 e Office 2010. Para esses ficheiros, a extensão de nome de ficheiro permanece igual depois do ficheiro está protegido por RMS.

|Tipos de ficheiro suportados pelo Office|Tipos de ficheiro suportados pelo Office|
|--------------------------------------------|--------------------------------------------|
|. doc<br /><br />. docm<br /><br />. docx<br /><br />. dot<br /><br />. dotm<br /><br />e. dotx<br /><br />. potm<br /><br />. potx<br /><br />. pps<br /><br />. ppsm<br /><br />. ppsx<br /><br />. ppt<br /><br />e. pptm|. pptx<br /><br />. thmx<br /><br />. xla<br /><br />. xlam<br /><br />. xls<br /><br />. xlsb<br /><br />. xlt<br /><br />. xlsm<br /><br />. xlsx<br /><br />e. xltm<br /><br />e. xltx<br /><br />. XPS|

### <a name="BKMK_ChangeDefaultProtection"></a>Alterar o nível de proteção predefinida dos ficheiros
Pode alterar a forma como a aplicação de partilha RMS protege a ficheiros ao editar o registo. Por exemplo, pode forçar ficheiros que suportam proteção nativa para serem protegidos genericamente pela aplicação de partilha RMS.

Razões para por que razão poderá pretender fazê-lo:

-   Para se certificar de que todos os utilizadores podem abrir o ficheiro a partir dos respetivos dispositivos móveis.

-   Para garantir que todos os utilizadores podem abrir o ficheiro se não tiverem uma aplicação que suporta a proteção nativa.

-   Para acomodar os sistemas de segurança que tomar medidas em ficheiros pelo respetivo extensão de nome de ficheiro e podem ser reconfigurados para alojar a extensão de nome de ficheiro. pfile, mas não podem ser reconfigurados para alojar várias extensões de nome de ficheiro para proteção nativa.

Da mesma forma, pode forçar a aplicação para aplicar proteção nativa aos ficheiros que, por predefinição, teriam proteção genérica aplicada de partilha RMS. Isto pode ser apropriado se tiver uma aplicação que suporta as APIs de RMS – por exemplo, uma aplicação de linha de negócio escritas por programadores internos ou uma aplicação comprada a partir de um fabricante independente de software (ISV).

Pode também forçar a bloquear a proteção de ficheiros da aplicação de partilha RMS (não aplicar proteção nativa nem proteção genérica). Por exemplo, poderá ser necessário se tiver um serviço que tem de conseguir abrir um ficheiro específico para processar o seu conteúdo ou aplicação automatizada. Quando bloqueia a proteção de um tipo de ficheiro, os utilizadores não é possível utilizar a aplicação de partilha RMS para proteger um ficheiro que tenha esse tipo de ficheiro. Quando tentam, eles veem uma mensagem que o administrador impediu a proteção e têm de cancelar a ação para proteger o ficheiro.

Para configurar a aplicação para aplicar proteção genérica a todos os ficheiros que, por predefinição, teriam proteção nativa aplicada de partilha RMS, efetue as seguintes edições de registo:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Criar uma nova chave denominada **&#42;**.

    Esta definição indica ficheiros com qualquer extensão de nome de ficheiro.

2.  Na chave recentemente adicionada **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, criar um novo valor de cadeia (REG_SZ) denominado **encriptação** que tem o valor de dados de **Pfile**.

    Esta definição resulta numa aplicação aplique a proteção genérica de partilha RMS.

Estas duas definições fazem a aplicação aplique a proteção genérica a todos os ficheiros que tenham uma extensão de nome de ficheiro de partilha RMS. Não se for este o seu objetivo, é necessária nenhuma configuração adicional. No entanto, pode definir exceções para tipos de ficheiro específico, para que estes estão protegidos ainda nativamente. Para tal, tem de efetuar três edições de registo adicionais para cada tipo de ficheiro:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Adicione uma nova chave que tem o nome da extensão de nome de ficheiro (sem o ponto final precedente).

    Por exemplo, para ficheiros que tenham um. docx extensão de nome de ficheiro, crie uma chave denominada **DOCX**.

2.  Na chave do tipo de ficheiro adicionada recentemente (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), crie um novo valor DWORD denominado **AllowPFILEEncryption** que tem um valor de **0**.

3.  Na chave do tipo de ficheiro adicionada recentemente (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), crie um novo valor de cadeia denominado **encriptação** que tem um valor de **nativo**.

Como resultado destas definições, todos os ficheiros estão protegidos genericamente, exceto os ficheiros que tenham uma extensão de nome de ficheiro. docx, que estão protegidos nativamente pela aplicação de partilha RMS.

Repita estes três passos para outros tipos de ficheiro que pretende definir como exceções, porque suportam a proteção nativa e não pretende que sejam protegidos genericamente pela aplicação de partilha RMS.

Pode efetuar edições de registo semelhantes para outros cenários, alterando o valor do **encriptação** cadeia que suporta os seguintes valores:

-   **Pfile**: Proteção genérica

-   **Nativo**: Proteção nativa

-   **Off**: Bloquear proteção

## Consultar Também
[Guia de utilizador de aplicação partilha do Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

