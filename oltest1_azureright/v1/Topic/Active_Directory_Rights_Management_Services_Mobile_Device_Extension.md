---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Extens&#227;o do Dispositivo M&#243;vel dos Servi&#231;os de Gest&#227;o de Direitos do Active Directory
A extensão do dispositivo móvel dos Serviços de Gestão de Direitos do Active Directory (AD RMS) é executada por cima de uma implementação do AD RMS existente. Isto permite aos utilizadores que têm dispositivos móveis proteger e consumir dados confidenciais quando o dispositivo suporta o cliente RMS mais recente e utiliza aplicações suportadas por RMS. Por exemplo, nesses dispositivos os utilizadores podem efetuar o seguinte:

-   Utilizar a aplicação de partilha RMS para consumir ficheiros de texto protegidos em diferentes formatos (incluindo .txt, .csv e .xml).

-   Utilizar a aplicação de partilha RMS para consumir ficheiros de imagem protegidos (incluindo .jpg, .gif e .tif.

-   Utilizar a aplicação de partilha RMS para abrir qualquer ficheiro que foi protegido genericamente (formato .pfile).

-   Utilizar a aplicação de partilha RMS para proteger ficheiros de imagem no dispositivo.

-   Utilizar um visualizador de PDFs suportado por RMS para dispositivos móveis, para abrir ficheiros PDF que foram protegidos com a aplicação de partilha RMS para Windows ou outra aplicação suportada por RMS.

-   Utilizar outras aplicações de fabricantes de software que fornecem aplicações suportadas por RMS e que admitem tipos de ficheiro que suportam RMS nativamente.

-   Utilizar as aplicações suportadas por RMS desenvolvidas internamente que foram escritas ao utilizar o SDK RMS.

> [!NOTE]
> Pode transferir a aplicação de partilha RMS a partir da página [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.
> 
> Para mais informações sobre os diferentes tipos de ficheiro que o RMS suporta, consulte a secção [Tipos de ficheiro suportados e extensões de nome de ficheiro](http://technet.microsoft.com/library/dn339003.aspx) no guia do administrador da aplicação de partilha Rights Management.

Não necessita que a extensão do dispositivo móvel consuma ou crie e-mail protegido em dispositivos, se estes utilizarem aplicações de e-mail que suportam o Exchange ActiveSync IRM. Este suporte nativo para RMS e dispositivos móveis foi introduzido com o Exchange 2010 Service Pack 1.

Utilize as seguintes secções para implementar a extensão do dispositivo móvel dos Serviços de Gestão de Direitos do Active Directory (AD RMS):

-   [Prerequisites for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Specifying the DNS SRV records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Deploying the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Pré-requisitos para a extensão do dispositivo móvel do AD RMS
Antes de instalar a extensão do dispositivo móvel do AD RMS, certifique-se de que estas dependências estão corretas.

|Requisito|Mais informações|
|-------------|--------------------|
|Uma implementação do AD RMS existente no Windows Server 2012 R2 ou Windows Server 2012. **Note:** O AD RMS tem de estar a utilizar a base de dados completa baseada no Microsoft SQL Server num servidor em separado e não na Base de Dados Interna do Windows, geralmente utilizada para testes no mesmo servidor.|Para obter a documentação sobre o AD RMS, consulte [Serviços de Gestão de Direitos do Active Directory](http://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server.|
|AD FS implementado no Windows Server 2012 R2|Para obter a documentação sobre o AD FS, consulte [Guia de Implementação do Windows Server 2012 R2 AD FS](http://technet.microsoft.com/library/dn486820.aspx) na biblioteca do Windows Server.<br /><br />Tem de configurar o AD FS para a extensão do dispositivo móvel. Para obter instruções, consulte a secção [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) neste tópico.|
|Registos SRV no DNS|Crie um ou mais registos SRV no domínio ou domínios da empresa:<br /><br />-   Um registo por cada sufixo de domínio de e-mail que os utilizadores utilizam<br />-   Um registo por cada FQDN utilizado pelos clusters de RMS para proteger conteúdo<br /><br />Quando os utilizadores fornecem os seus endereços de e-mail a partir do dispositivo móvel, o sufixo de domínio é utilizado para identificar se devem utilizar uma infraestrutura do AD RMS ou do Azure RMS. Quando o registo SRV é encontrado, os clientes são direcionados para o servidor do AD RMS que responde a esse URL.<br /><br />Quando os utilizadores consomem conteúdo protegido com um dispositivo móvel, a aplicação cliente procura no DNS um registo que corresponda ao FQDN no URL do cluster que protegeu o conteúdo. Em seguida, o dispositivo é direcionado para o cluster do AD RMS especificado no registo DNS e adquire uma licença para abrir o conteúdo. Na maioria dos casos, o cluster do RMS será o mesmo cluster do RMS que protegeu o conteúdo.<br /><br />Para mais informações sobre como especificar os registos SRV, consulte a secção [Specifying the DNS SRV Records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) neste tópico.|
|Clientes atualmente suportados:<br /><br />-   Dispositivos Android que utilizam a última versão da aplicação de partilha RMS para Android|Versão mínima do Android 4.0.3.<br /><br />Transfira a aplicação de partilha do RMS para Android a partir do [site Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) e efetue o sideload da aplicação para o dispositivo.|

### <a name="BKMK_ADFS"></a>Configurar o AD FS para a extensão do dispositivo móvel do AD RMS
Primeiro, tem de configurar o AD FS e, em seguida, autorizar a aplicação de partilha RMS para Android.

##### Passo 1: Para configurar o AD FS

-   Pode executar um script do Windows PowerShell para configurar automaticamente o AD FS para suportar a extensão do dispositivo móvel do AD RMS ou pode especificar manualmente as opções e os valores de configuração:

    -   Para configurar o AD FS, copie e cole o seguinte num ficheiro de script do Windows PowerShell e, em seguida, execute-o:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Para configurar manualmente o AD FS, utilize estas definições:

        |Configuração|Valor|
        |----------------|---------|
        |**Confiança de Entidade Confiadora**|api.rms.rest.com|
        |**Regra de afirmação**|**Arquivo de atributos**:  Active Directory<br /><br />**Endereços-de-e-mail**:  Endereço-de-e-mail<br /><br />**Nome-de-Utilizador-Principal**:  UPN<br /><br />**Endereço-Proxy**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Passo 2: Autorizar a aplicação de partilha RMS para Android

-   Execute o seguinte comando do Windows PowerShell para adicionar suporte para dispositivos Android:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Especificar os registos SRV de DNS para a extensão do dispositivo móvel do AD RMS
Tem de criar registos SRV de DNS para cada domínio de e-mail que os utilizadores utilizam. Se todos os utilizadores utilizarem domínios subordinados a partir de um único domínio principal e todos os utilizadores deste espaço de nome contíguo utilizarem o mesmo cluster do RMS, pode utilizar apenas um registo SRV no domínio principal, e o RMS encontrará os registos DNS adequados.

Os registos SRV têm o seguinte formato: _rmsdisco._http._tcp. *&lt;emailsuffix&gt;**&lt;portnumber&gt;**&lt;RMSClusterFQDN&gt;*

Por exemplo, se a organização tiver utilizadores com os seguintes endereços de e-mail:

-   user@contoso.com

-   user@sales.contoso.com

-   user@fabrikam.com

- e não existirem outros domínios subordinados para contoso.com que utilizem um cluster do RMS diferente do denominado **rmsserver.contoso.com**, crie dois registos SRV de DNS que tenham estes valores:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Além destes registos SRV de DNS para os domínios de e-mail, tem de criar outro registo SRV de DNS nos domínios de utilizador. Este registo tem de especificar os URLs do cluster do RMS que protege conteúdo. Todos os ficheiros protegidos pelo RMS incluem um URL para o cluster que protegeu esse ficheiro. Os dispositivos móveis utilizam o registo SRV de DNS e o FQDN do URL especificado no registo para encontrar o cluster do RMS correspondente que pode suportar dispositivos móveis.

Por exemplo, se o cluster do RMS for **rmsserver.contoso.com**, crie um registo SRV de DNS que tenha os seguintes valores: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Implementar a extensão do dispositivo móvel do AD RMS
Antes de instalar a extensão do dispositivo móvel do AD RMS, certifique-se de que os pré-requisitos da secção precedente foram cumpridos e de que sabe o URL do servidor do AD FS. Em seguida, efetue o seguinte:

1.  Transfira a extensão do dispositivo móvel do AD RMS a partir do [site do Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Execute o Setup.exe para iniciar o Assistente de Configuração da Extensão do Dispositivo Móvel dos Serviços de Gestão de Direitos do Active Directory.

3.  Quando solicitado, introduza o URL do servidor do AD FS que configurou anteriormente.

4.  Conclua o assistente.

Execute este assistente em todos os nós no cluster do RMS.

