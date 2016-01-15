---
description: na
keywords: na
title: Planning and Implementing Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
---
# Planear e implementar a sua chave de inquilino do Azure Rights Management
Utilize as informações deste tópico para o ajudar a planear e gerir a sua chave de inquilino do Rights Management (RMS) do serviço para o Azure RMS. Por exemplo, em vez do Microsoft gerir a sua chave de inquilino (predefinição), poderá gerir a sua própria chave de inquilino para cumprir as normas específicas que se aplicam à sua organização.  Gerir a sua própria chave do inquilino é também referido como colocar o seu próprio chave ou BYOK.

> [!NOTE]
> A chave do RMS inquilino também é conhecido como a chave do certificado de licenciante de servidor (SLC). Azure RMS mantém uma ou mais teclas para cada organização que subscreve Azure RMS. Sempre que é utilizada uma chave para o RMS numa organização (por exemplo, as chaves de utilizador, chaves de computador, as chaves de encriptação do documento), estes encadeiam cryptographically a sua chave de inquilino do RMS.

**Uma visão:** Utilize a tabela seguinte como um guia rápido para a topologia de chave do inquilino recomendado. Em seguida, utilize as secções adicionais para obter mais informações.

Se implementar o Azure RMS utilizando uma chave de inquilino que é gerida pelo Microsoft, pode alterar para BYOK mais tarde. No entanto, atualmente não é possível alterar a chave de inquilino do Azure RMS a partir do BYOK gerido pela Microsoft.

|Necessidade comercial|Topologia de chaves de inquilino recomendado|
|-------------------------|------------------------------------------------|
|Implementar o Azure RMS rapidamente e sem necessidade de hardware especial|Gerido pela Microsoft|
|Precisarem de funcionalidades IRM completa no Exchange Online com o Azure RMS|Gerido pela Microsoft|
|As chaves são criadas por si e protegidas de um módulo de segurança de hardware (HSM)|BYOK<br /><br />Atualmente, esta configuração irá resultar na funcionalidade reduzida do IRM no Exchange Online. Para obter mais informações, consulte o [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) secção.|
Utilize as secções seguintes para ajudar a escolher a chave de inquilino topologia para utilizar, compreender o ciclo de vida de chaves de inquilino, como implementar colocar o seu próprio chave (BYOK) e o que os passos para efetuar o seguinte:

-   [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey)

-   [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing)

-   [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)

-   [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps)

## <a name="BKMK_ChooseTenantKey"></a>Selecione o seu inquilino topologia chave: Geridos pela Microsoft (predefinição) ou geridos por si (BYOK)
Decida qual topologia de chave do inquilino é melhor para a sua organização. Por predefinição, o Azure RMS gera a chave de inquilino e gere a maioria dos aspetos do ciclo de vida de chaves de inquilino. Esta é a opção mais simples com mais sobrecargas administrativas. Na maioria dos casos, não, mesmo que terá de saber o que tem uma chave de inquilino. Apenas inscrever-se para o Azure RMS e o resto do processo de gestão de chaves é processado pela Microsoft.

Em alternativa, pode querer controlo total sobre a chave de inquilino, o que envolve criar a sua chave de inquilino e manter a cópia principal no local. Este cenário é frequentemente referido como colocar o seu próprio chave (BYOK). Com esta opção, ocorrerá o seguinte:

1.  Gerar a chave de inquilino no local, de acordo com as políticas de TI.

2.  Em segurança transferir a chave do inquilino a partir de um módulo de segurança de Hardware (HSM) na sua posse para HSMs que são propriedade e são geridos pela Microsoft. Durante este processo, a chave de inquilino nunca deixa o limite de proteção de hardware.

3.  Ao transferir a chave de inquilino para a Microsoft, permanece protegido por Thales HSMs. Microsoft trabalhou com Thales para se certificar de que a chave de inquilino não pode ser extraída a contar HSMs da Microsoft.

Embora seja opcional, irá provavelmente também pretende utilizar a utilização em tempo real near registos a partir do Azure RMS para ver exatamente como e quando está a ser utilizada a chave de inquilino.

> [!NOTE]
> Uma medida adicional de proteção, o Azure RMS utiliza mundo de segurança para os respetivos centros de dados na América do Norte, EMEA (Europa, Médio Oriente e África) e da Ásia. Quando gere a sua própria chave do inquilino, está associado para o mundo de segurança de região no qual está registado o seu inquilino do RMS. Por exemplo, não é possível utilizar uma chave de inquilino a partir de um cliente Europeu na América do Norte ou da Ásia os centros de dados.

## <a name="BKMK_OverviewLifecycle"></a>O ciclo de vida de chaves de inquilino
Se decidir que Microsoft deve gerir a sua chave de inquilino, o Microsoft processa a maioria das operações de ciclo de vida de chave. No entanto, se optar por gerir a sua chave de inquilino, é responsável por muitas das operações de ciclo de vida de chave e alguns procedimentos adicionais.

Os diagramas seguintes mostram e compara estas duas opções. O diagrama primeiro mostra como pouca sobrecargas de administrador que existem por si na configuração predefinida quando Microsoft gere a chave de inquilino.

![](../Image/RMS_BYOK_cloud.png)

O segundo diagrama mostra os passos adicionais necessários quando gere a sua própria chave do inquilino.

![](../Image/RMS_BYOK_onprem.png)

Se decidir deixar de gerir a sua chave de inquilino do Microsoft, é necessária gerar a chave mais nenhuma ação e pode ignorar as seguintes secções e ir diretamente para [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps).

Se optar por gerir a sua chave de inquilino sozinho, leia as secções seguintes para obter mais informações.

### Mais informações sobre as adições Thales HSMs e da Microsoft
Azure RMS utiliza Thales HSMs para proteger as suas chaves.

Segurança i Thales é um fornecedor global à esquerda da encriptação de dados e soluções de segurança de cyber para os serviços financeiros, tecnologia de alta, fabrico, administração pública e setores de tecnologia. Com um ano de 40 registar registo proteger empresarial e informações para a administração pública, soluções Thales são utilizadas pelos quatro dos cinco energia maior e empresas aerospace, 22 NATO países/regiões e proteger mais de 80 por cento de transações de pagamento todo o mundo.

A Microsoft tem colaborado com Thales para melhorar o estado do ClipArt para HSMs. Estes melhoramentos permitem-lhe obtém as vantagens típicas do serviços alojados sem relinquishing controlo sobre as chaves. Especificamente, estas melhorias de permitem Microsoft gerir os HSMs para que não é necessário. Como um serviço em nuvem, o Azure RMS dimensiona em breve aviso para satisfazer as pontas de utilização da sua organização. Ao mesmo tempo, a chave está protegida no interior HSMs da Microsoft: Manter o controlo sobre o ciclo de vida chave porque gerar a chave e transferi-lo para HSMs da Microsoft.

Para obter mais informações, consulte o artigo [Thales HSMs e o Azure RMS](http://www.thales-esecurity.com/msrms/cloud) no Thales web site.

## <a name="BKMK_Pricing"></a>As restrições e BYOK preços
Organização que tenham uma subscrição do Azure gestão de TI pode utilizar BYOK e inicie a sua utilização sem qualquer custo adicional. As organizações que utilizam o RMS para indivíduos não é possível utilizar BYOK e registo porque não têm um administrador de inquilino para configurar estas funcionalidades.

> [!NOTE]
> Para mais informações sobre RMS para indivíduos, consulte o artigo [RMS para indivíduos e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

![](../Image/RMS_BYOK_noExchange.png)

BYOK e o registo de forma totalmente integrada trabalhar com todas as aplicações que se integra com o Azure RMS. Isto inclui serviços em nuvem como o SharePoint Online, servidores que executem o Exchange e SharePoint que funcionam com o Azure RMS utilizando o conector do RMS e aplicações de cliente, como o Office 2013 no local a pedido. Irá obter registos de utilização de chave, independentemente do que a aplicação torna pedidos do Azure RMS.

Existe uma exceção: Atualmente, **Azure RMS BYOK não é compatível com o Exchange Online**.  Se pretender utilizar o Exchange Online, recomendamos que implementa o Azure RMS no agora, o modo de gestão de chaves predefinido onde o Microsoft gera e gere a sua chave. Tem a opção para mover para BYOK mais tarde, por exemplo, quando o Exchange Online suporta BYOK do Azure RMS. No entanto, se não puder aguardar, outra opção é implementar o Azure RMS com BYOK agora, com a funcionalidade reduzida do RMS para o Exchange Online (desprotegidas mensagens de correio eletrónico e anexos desprotegidos permanecem totalmente funcional):

-   Não não possível apresentar mensagens de correio eletrónico protegidas ou anexos protegidos no Outlook Web Access.

-   Não não possível apresentar mensagens de e-mail protegidas em dispositivos móveis que utilizam o Exchange ActiveSync IRM.

-   Transporte desencriptação (por exemplo, para procurar software maligno) e desencriptação do diário não for possível, por isso, são protegidos os e-mails e anexos protegidos serão ignorados.

-   Transporte proteção regras e os dados prevenção de perda (DLP) que impor políticas IRM não é possível, pelo que não é possível aplicar a proteção RMS utilizando estes métodos.

-   Baseada em servidor procure protegidas mensagens de correio eletrónico, para que os e-mails protegidos serão ignorados.

Quando utiliza o Azure RMS BYOK com funcionalidade reduzida do RMS para o Exchange Online, o RMS irá funcionar com os clientes de e-mail no Outlook no Windows e Mac e em outros clientes de correio eletrónico que não utilizam o Exchange ActiveSync IRM.

Caso esteja a migrar para o Azure RMS a partir do AD RMS, possa ter importado a chave como um domínio de publicação fidedigno (TPD) para o Exchange Online (também denominada BYOK na terminologia de Exchange, que é separada do Azure RMS BYOK). Neste cenário, tem de remover o TPD a partir do Exchange Online para evitar modelos e as políticas em conflito. Para obter mais informações, consulte o artigo [Remover RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) da biblioteca de cmdlets do Exchange Online.

Por vezes, a exceção de BYOK do Azure RMS para o Exchange Online não é um problema na prática. Por exemplo, as organizações que precisam de BYOK e o registo de executam os seus dados aplicações (Exchange, SharePoint, escritório) no local e utilizar o Azure RMS para a funcionalidade que não está disponível facilmente com o AD local RMS (por exemplo, a colaboração com outras empresas e o acesso a partir de clientes móveis). BYOK e trabalho do registo well neste cenário e permitem a sua organização têm controlo total sobre a subscrição do Azure RMS.

## <a name="BKMK_ImplementBYOK"></a>Implementar a colocar a sua própria chave (BYOK)
Utilize as informações e procedimentos nesta secção se decidiu gerar e gerir a sua chave de inquilino; a colocar o seu cenário de chave (BYOK):

-   [Prerequisites for BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Preqs)

-   [Generate and transfer your tenant key – over the Internet](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOK_Internet)

-   [Generate and transfer your tenant key – in person](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOK_InPerson)

> [!IMPORTANT]
> Se já tiver iniciado a utilizar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (o serviço está ativado) e tiver utilizadores que executar o Office 2010, contacte a Microsoft suporte ao cliente (CSS) antes de executar estes procedimentos. Dependendo do seu cenário e requisitos, pode continuar a utilizar BYOK mas com algumas limitações ou passos adicionais.
> 
> Contacte o CSS também se a sua organização tiver políticas específicas para processamento de chaves.

### <a name="BKMK_Preqs"></a>Pré-requisitos para BYOK
Consulte a tabela seguinte para obter uma lista de pré-requisitos para colocar a sua própria chave (BYOK).

|Requisito|Obter mais informações|
|-------------|--------------------------|
|Uma subscrição que suporta o Azure RMS|Para mais informações sobre as subscrições disponíveis, consulte o [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico.|
|Não utilize RMS para indivíduos ou ao Exchange Online. Ou, se utilizar o Exchange Online, compreender e aceitar as limitações da utilização BYOK com esta configuração.|Para mais informações sobre as restrições e limitações atuais para BYOK, consulte o [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) deste tópico. **Important:** Atualmente, BYOK não é compatível com o Exchange Online.|
|Thales HSM, smart cards e software de suporte<br /><br />Caso esteja a migrar a partir do AD RMS para o Azure RMS utilizando a chave de software a chave de hardware, tem de ter a versão mínima do 11.62 para obter os controladores de Thales.|Tem de ter acesso a um módulo de segurança de Hardware Thales e conhecimento operacional básico dos Thales HSMs. Consulte o artigo [Thales Hardware segurança módulo](http://www.thales-esecurity.com/msrms/buy) para a lista de modelos compatíveis ou comprar um HSM se não tiver um.|
|Se pretende transferir a chave de inquilino através da Internet em vez de estar fisicamente presentes na Redmond, EUA:<br /><br />1.  Um x64 offline estação de trabalho com um sistema de operação mínimo do Windows do Windows 7 e Thales nShield software, pelo menos, versão 11.62.<br />    Se esta estação de trabalho executa o Windows 7, tem de [instalar Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkId=225702).<br />2.  Uma estação de trabalho que está ligada à Internet e tem um sistema de operação mínimo do Windows do Windows 7.<br />3.  Uma unidade USB ou outro dispositivo de armazenamento portátil que tenha pelo menos 16 MB de espaço livre.|Estes pré-requisitos não são necessários se viajam para Redmond e transferir a sua chave de inquilino na pessoa.<br /><br />Por motivos de segurança, recomendamos que a primeira estação de trabalho não está ligada a uma rede. No entanto, isto não é através de programação imposto. **Note:** As instruções que se seguem, esta estação de trabalho é referida como a estação de trabalho desligada.<br />Além disso, se a chave de inquilino destina-se numa rede de produção, recomendamos que utilize uma estação de trabalho segunda separada para o conjunto de ferramentas de transferir e carregar a chave de inquilino. Mas, para fins de teste, pode utilizar a mesma estação de trabalho como primeiro. **Note:** As instruções que se seguem, esta estação de trabalho segunda é referida como a estação de trabalho ligado à Internet.|
|Opcional: Subscrição do Azure|Se pretender iniciar a utilização de chave de inquilino (e utilização do Rights Management), tem de ter uma subscrição do Azure e suficiente armazenamento no Azure para armazenar os seus registos.|
Os procedimentos para gerar e utilizar a sua própria chave inquilino dependem se pretende fazê-lo através da Internet ou na pessoa:

-   **Através da Internet:** Isto requer que alguns passos de configuração adicionais, tais como transferir e utilizar um conjunto de ferramentas e cmdlets do Windows PowerShell. No entanto, não terá de estar fisicamente no efectuar Microsoft para transferir a chave de inquilino. Segurança é mantida através dos seguintes métodos:

    -   Gerar a chave do inquilino a partir de uma estação de trabalho offline, o que reduz a superfície de ataque.

    -   A chave do inquilino é encriptada com uma chave Exchange chave (KEK), que permanece encriptados até serem transferidos para o HSMs de RMS do Azure. Apenas a versão encriptada do sua chave de inquilino deixa a estação de trabalho original.

    -   Uma ferramenta define as propriedades chave do inquilino que une a sua chave de inquilino para o mundo de segurança do Azure RMS. Por isso, depois do HSMs de RMS do Azure receber e desencriptar a chave do inquilino, apenas estas HSMs podem utilizá--lo. Não é possível exportar a chave de inquilino. Este enlace é imposta pelo HSMs Thales.

    -   A chave de Exchange de chave (KEK) que é utilizado para encriptar a chave do inquilino é gerado no interior do HSMs de RMS do Azure e não é exportável. Os HSMs impor que pode ser não limpar qualquer versão do KEK fora dos HSMs. Além disso, o conjunto de ferramentas inclui atestado de Thales que o KEK não é exportável e foi gerado no interior de um HSM genuine que foi fabricado por Thales.

    -   O conjunto de ferramentas inclui atestado de Thales que o mundo de segurança do Azure RMS também foi gerado num HSM genuine produzido por Thales. Isto prove a para a Microsoft está a utilizar genuine hardware.

    -   Microsoft utiliza KEKs separados, bem como separar mundo de segurança de cada região geográfica, o que garante que a chave de inquilino pode ser utilizada apenas nos centros de dados na região no qual é encriptado. Por exemplo, não é possível utilizar uma chave de inquilino a partir de um cliente Europeu na América American ou da Ásia os centros de dados.

    > [!NOTE]
    > A chave de inquilino pode mover em segurança através de computadores não fidedignos e redes porque é encriptada e protegida com permissões ao nível do controlo de acesso, que torna utilizável apenas dentro do seu HSMs e HSMs da Microsoft para o Azure RMS. Pode utilizar os scripts que são fornecidos no conjunto de ferramentas para verificar as medidas de segurança e ler mais informações sobre como isto funciona de Thales: [a gestão de chaves de hardware na nuvem RMS](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud).

-   **Na pessoa:** Isto requer que contacte o Microsoft suporte ao cliente (CSS) para agendar um compromisso de transferência da chave para o Azure RMS. Tem viajam para um Microsoft office no Redmond, Washington, Unidos Estados of America para transferir a chave de inquilino para o mundo de segurança do Azure RMS.

### <a name="BKMK_BYOK_Internet"></a>Gerar e transferir a chave de inquilino – através da Internet
Se pretende transferir a chave de inquilino através da Internet em vez de viajam para efectuar uma Microsoft para transferir a chave de inquilino na pessoa, utilize os seguintes procedimentos:

-   [Prepare your Internet-connected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareWorkstation)

-   [Prepare your disconnected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_DisconnectedPrepareWorkstation)

-   [Generate your tenant key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate)

-   [Prepare your tenant key for transfer](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer)

-   [Transfer your tenant key to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer)

#### <a name="BKMK_InternetPrepareWorkstation"></a>Preparar a estação de trabalho ligado à Internet
Para preparar a estação de trabalho que está ligada à Internet, siga estes 3 passos:

-   [Step 1: Install Windows PowerShell for Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation1)

-   [Step 2: Get your Azure Active Directory tenant ID](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation2)

-   [Step 3: Download the BYOK toolset](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation3)

##### <a name="BKMK_PrepareInternetConnectedWorkstation1"></a>Passo 1: Instalar o Windows PowerShell para o Azure Rights Management
A partir da estação de trabalho ligado à Internet, transfira e instale o módulo Windows PowerShell para o Azure Rights Management.

> [!NOTE]
> Se tiver transferido anteriormente este módulo do Windows PowerShell, execute o seguinte comando para verificar se o seu número de versão está, pelo menos, 2.1.0.0: `(Get-Module aadrm -ListAvailable).Version`

Para instruções de instalação, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

##### <a name="BKMK_PrepareInternetConnectedWorkstation2"></a>Passo 2: Obter o ID de inquilino do Azure Active Directory
Inicie o Windows PowerShell com o **Executar como administrador** opção e, em seguida, execute os seguintes comandos:

-   Utilize o [Ligar AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet para ligar ao serviço do Azure RMS:

    ```
    Connect-AadrmService
    ```
    Quando lhe for pedido, introduza o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] credenciais de administrador de inquilinos (normalmente, utilizará uma conta que seja um administrador global do Azure Active Directory ou do Office 365).

-   Utilize o [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet para visualizar a configuração do seu inquilino:

    ```
    Get-AadrmConfiguration
    ```
    A partir da saída, guarde o GUID da primeira linha (BPOSId). Este é o ID de inquilino do Azure Active Directory, que irá precisar mais tarde quando a preparar-se a chave de inquilino para carregamento.

-   Utilize o [Desligar AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet para desligar do serviço do Azure RMS até estar pronto para carregar a chave:

    ```
    Disconnect-AadrmService
    ```

Não feche a janela do Windows PowerShell.

##### <a name="BKMK_PrepareInternetConnectedWorkstation3"></a>Passo 3: Transferir o toolset BYOK
Aceda ao Center Download Microsoft e [Transferir o toolset BYOK](http://go.microsoft.com/fwlink/?LinkId=335781) para sua região:

|Região|Nome do pacote|
|----------|------------------|
|América do Norte|United de AzureRMS BYOK ferramentas States.zip|
|Europe|AzureRMS-BYOK-ferramentas-Europe.zip|
|Ásia|AzureRMS-BYOK-ferramentas-AsiaPacific.zip|
O conjunto de ferramentas inclui o seguinte:

-   Um pacote de chave Exchange chave (KEK) que tenha uma nome a partir **BYOK-KEK-pkg -**.

-   Um pacote de mundo de segurança que tenha uma nome a partir **BYOK-SecurityWorld-pkg -**.

-   Um script de python com o nome **verifykeypackage.py**.

-   Um ficheiro executável da linha de comandos com o nome **KeyTransferRemote.exe**, um ficheiro de metadados com o nome **KeyTransferRemote.exe.config**, e associou DLLs.

-   Um Visual C++ Redistributable Package, com o nome **vcredist_x64.exe**.

Copie o pacote para outro armazenamento portátil ou uma unidade USB.

#### <a name="BKMK_DisconnectedPrepareWorkstation"></a>Preparar a estação de trabalho desligada
Para preparar a estação de trabalho que não está ligada a uma rede (Internet ou a rede interna), siga estes passos de 2:

-   [Step 1: Prepare the disconnected workstation with Thales HSM](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareDisconnectedWorkstation1)

-   [Step 2: Install the BYOK toolset on the disconnected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareDisconnectedWorkstation2)

##### <a name="BKMK_PrepareDisconnectedWorkstation1"></a>Passo 1: Preparar a estação de trabalho desligada com Thales HSM
Na estação de trabalho desligada, instalar o software de suporte de nCipher (Thales) num computador Windows e, em seguida, anexe um HSM Thales nesse computador.

Certifique-se de que as ferramentas de Thales o caminho de **(%nfast_home%\bin** e **%nfast_home%\python\bin**). Por exemplo, escreva o seguinte:

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
Para mais informações, consulte o guia de utilizador incluído com o HSM Thales ou visitar o Web site Thales para o Azure RMS em [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

##### <a name="BKMK_PrepareDisconnectedWorkstation2"></a>Passo 2: Instalar o conjunto de ferramentas BYOK na estação de trabalho desligada
Copie o pacote de toolset BYOK a pen USB ou outro armazenamento portátil e, em seguida, efetue o seguinte procedimento:

1.  Extraia os ficheiros do pacote transferido para qualquer pasta.

2.  A partir da pasta a que, execute vcredist_x64.exe.

3.  Siga as instruções para a instalar os componentes de tempo de execução do Visual C++ para Visual Studio 2012.

#### <a name="BKMK_InternetGenerate"></a>Gerar a chave de inquilino
Na estação de desligado trabalho, a seguir estes 3 passos para gerar a sua própria chave do inquilino:

-   [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1)

-   [Step 2: Validate the downloaded package](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate2)

-   [Step 3: Create a new key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate3)

##### <a name="BKMK_InternetGenerate1"></a>Passo 1: Criar um mundo de segurança
Começar uma linha de comandos e executar o programa de novo mundo Thales.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Este programa cria um **segurança mundo** ficheiro em % NFAST_KMDATA%\local\world, que corresponde à pasta C:\ProgramData\nCipher\Key Data\local de gestão. Pode utilizar valores diferentes para o quórum mas no nosso exemplo, lhe for pedido para introduzir três cartões em branco e pins para cada um deles. Em seguida, pode ser necessário qualquer dois cartões que têm acesso administrativo para o mundo de segurança (o quórum especificado).  Estes cartões tornam-se a **administrador cartão definido** para o novo mundo de segurança. Nesta fase, pode especificar a palavra-passe ou PIN para cada cartão de ACS ou adicioná-lo mais tarde com um comando.

> [!TIP]
> Pode verificar o estado da configuração atual da sua HSM utilizando o `nkminfo` comando.

Em seguida, efetue o seguinte:

1.  Instalar o fornecedor de Thales CNG conforme descrito na documentação do Thales e configure-o para utilizar o novo mundo de segurança.

2.  Criar uma cópia de segurança o ficheiro mundo **%nfast_kmdata%\local**. Proteger e proteger o ficheiro do mundo, os cartões de administrador e os respetivos pins e certifique-se de que nenhum única pessoa tem acesso a mais do que um cartão.

##### <a name="BKMK_InternetGenerate2"></a>Passo 2: Validar o pacote transferido
Este passo é opcional mas recomendada para que possa validar o seguinte:

-   A chave de troca de chave que está incluído no toolset foi gerada a partir de um HSM Thales genuine.

-   O hash do mundo de segurança do Azure RMS que está incluído no toolset foi gerado num HSM Thales genuine.

-   A chave de troca de chave é não exportável.

> [!NOTE]
> Para validar o pacote transferido, o HSM tem de estar ligado, ligado e tem de ter um mundo de segurança no mesmo (tal como a que acabou de criar).

###### Para validar o pacote transferido

1.  Execute o script de verifykeypackage.py por associando um dos seguintes, consoante a região do utilizador:

    -   Na América do Norte:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Para Europa:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Da Ásia:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > O software de Thales inclui um interpretador Python em %NFAST_HOME%\python\bin

2.  Confirme que verá o seguinte, o que indica a validação com êxito: **Resultado:  ÊXITO**

Este script valida a cadeia de signatário até a chave de raiz Thales. O hash desta chave de raiz é incorporado no script e respetivo valor deve ser **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**. Pode também confirmar este valor separadamente, visitando o [Web site Thales](http://www.thalesesec.com/).

Agora está pronto para criar uma nova chave que será a sua chave de inquilino do RMS.

##### <a name="BKMK_InternetGenerate3"></a>Passo 3: Crie uma nova chave
Gerar uma chave CNG utilizando o Thales **generatekey** e **cngimport** programas.

Execute o seguinte comando para gerar a chave:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Quando executar este comando, utilize estas instruções:

-   Para o tamanho da chave, é recomendável 2048 mas também suportam chaves RSA de 1024 bits para clientes existentes do AD RMS que tem estas chaves e estão a migrar para o Azure RMS.

-   Substitua o valor do *contosokey* para o **ident** e **plainname** com qualquer valor de cadeia. Para minimizar a sobrecargas administrativas e reduzir o risco de erros, recomendamos que utilize o mesmo valor para ambos e utilize todos os carateres minúsculos.

-   O pubexp fica em branco (predefinição), neste exemplo, mas pode especificar valores específicos. Para mais informações, consulte a documentação de Thales.

Em seguida, execute o seguinte comando para importar a chave para CNG:

```
cngimport --import -M --key=contosokey --appname=simple contosokey
```
Quando executar este comando, utilize estas instruções:

-   Substituir *contosokey* com o mesmo valor que especificou no [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) a partir de *gerar a chave de inquilino* secção.

-   Utilize o **- M** opção para que a chave é adequada para este cenário. Sem esta situação, a chave resultante será uma chave de específica do utilizador para o utilizador atual.

Este comando cria um ficheiro de chave foi Atomizada na sua pasta %NFAST_KMDATA%\local com um nome, começando **key_caping_** seguido por um SID. Por exemplo: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Este ficheiro contém uma chave encriptada.

> [!TIP]
> Pode ver o estado da configuração atual chaves de utilizando o `nkminfo –k` comando.

Agregar este ficheiro de chave foi Atomizada numa localização segura.

> [!IMPORTANT]
> Ao transferir a chave para o Azure RMS mais tarde, a Microsoft não é possível exportar esta chave devolver para que fique muito importante que uma cópia de segurança do mundo de chave e segurança com segurança. Procure Thales orientações e melhores práticas para a sua chave de segurança.

Agora está pronto para transferir a chave de inquilino para o Azure RMS.

#### <a name="BKMK_InternetPrepareTransfer"></a>Preparar a sua chave de inquilino para transferência
Na estação de desligado trabalho, estes 4 passos para preparar a sua própria chave do inquilino:

-   [Step 1: Create a copy of your key with reduced permissions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer1)

-   [Step 2: Inspect the new copy of the key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer2)

-   [Step 3: Encrypt your key by using Microsoft’s Key Exchange Key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer3)

-   [Step 4: Copy your key transfer package to the Internet-connected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer4)

##### <a name="BKMK_InternetPrepareTransfer1"></a>Passo 1: Criar uma cópia da sua chave com permissões reduzidas
Para reduzir as permissões na sua chave de inquilino, efetue o seguinte:

-   A partir de uma linha de comandos, execute um dos seguintes procedimentos, consoante a região do utilizador:

    -   Na América do Norte:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Para Europa:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Da Ásia:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

Quando executar este comando, substitua *contosokey* com o mesmo valor que especificou no [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) a partir de *gerar a chave de inquilino* secção.

Será pedido de fixação no seus cartões de ACS de mundo de segurança e se for especificado, a respetiva palavra-passe ou PIN..

Quando o comando for concluído, verá **resultado: Êxito** e a cópia da sua chave de inquilino com permissões reduzidas vai estar num ficheiro denominado key_xferacId_*&lt; contosokey &gt;*.

##### <a name="BKMK_InternetPrepareTransfer2"></a>Passo 2: Inspecione a nova cópia da chave
Opcionalmente, execute o Thales utilitários para confirmar o mínimo de permissões a nova chave de inquilino:

-   aclprint.PY:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

Quando executar estes comando, substitua *contosokey* com o mesmo valor que especificou no [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) a partir de *gerar a chave de inquilino* secção.

##### <a name="BKMK_InternetPrepareTransfer3"></a>Passo 3: Encriptar a chave, utilizando a chave de troca de chave da Microsoft
Execute um dos comandos seguintes, consoante a região do utilizador:

-   Na América do Norte:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Para Europa:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Da Ásia:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

Quando executar este comando, utilize estas instruções:

-   Substituir *contosokey* com o identificador que utilizou para gerar a chave no [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) a partir de *gerar a chave de inquilino* secção.

-   Substituir *GUID* com o Azure Active Directory inquilino ID obtidas em [Step 2: Get your Azure Active Directory tenant ID](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation2) a partir de *preparar a estação de trabalho ligado à Internet* secção.

-   Substituir *ContosoFirstKey* com uma etiqueta que será utilizada para o seu nome de ficheiro de saída.

Quando esta ação for concluída com êxito-apresenta **resultado: Êxito** e haverá um novo ficheiro na pasta atual que tem o seguinte nome: TransferPackage -*ContosoFirstkey*.byok

##### <a name="BKMK_InternetPrepareTransfer4"></a>Passo 4: Copie o pacote de transferência da chave para a estação de trabalho ligado à Internet
Utilizar uma unidade USB ou outro armazenamento portátil para copiar o ficheiro de saída do passo anterior (KeyTransferPackage -*ContosoFirstkey*.byok) para a estação de trabalho ligado à Internet.

> [!NOTE]
> Utilize as práticas de segurança para proteger o ficheiro, pois inclui a chave privada.

#### <a name="BKMK_InternetTransfer"></a>Transferir a chave de inquilino para o Azure RMS
Na estação de trabalho ligado à Internet, siga estes passos para transferir a nova chave de inquilino para o Azure RMS, 3:

-   [Step 1: Connect to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer1)

-   [Step 2: Upload the key package](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer2)

-   [Step 3: Enumerate your tenant keys – as needed](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer3)

##### <a name="BKMK_InternetTransfer1"></a>Passo 1: Ligar ao Azure RMS
Regressar à janela do Windows PowerShell e escreva o seguinte:

1.  Restabelecer a ligação a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] serviço:

    ```
    Connect-AadrmService
    ```

2.  Utilize o [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx) cmdlet para ver a configuração atual da chave do inquilino:

    ```
    Get-AadrmKeys
    ```

##### <a name="BKMK_InternetTransfer2"></a>Passo 2: Carregar o pacote de chave
Utilize o [Adicionar AadrmKey](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx) cmdlet para carregar o pacote de transferência da chave que copiou de estação de trabalho desligada:

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> Lhe for pedido para confirmar esta ação. É importante compreender que esta ação não pode ser anulada. Ao carregar uma chave de inquilino, é assumida automaticamente a chave de inquilino principal da sua organização e utilizadores irão começar a utilizar esta chave de inquilino quando estes protegem documentos e ficheiros.

Se o carregamento for bem-sucedido, verá a seguinte mensagem: **O serviço de gestão de direitos adicionada com êxito a chave.**

Esperado um atraso de replicação para que a alteração a ser propagada para todas as [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] centros de dados.

##### <a name="BKMK_InternetTransfer3"></a>Passo 3: Enumerar as chaves de inquilino – conforme necessário
Utilize o cmdlet Get-AadrmKeys novamente para ver a alteração na sua chave de inquilino e, sempre que pretender ver uma lista das chaves de inquilino. As chaves de inquilino apresentadas incluem a chave de inquilino inicial Microsoft gerado por si e as chaves de inquilino que adicionou:

```
Get-AadrmKeys
```
A chave do inquilino que está marcada **Active Directory** é o que a sua organização está atualmente a utilizar para proteger documentos e ficheiros.

Agora concluiu todos os passos necessários para colocar a sua própria chave através da Internet e podem aceder ao [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps).

### <a name="BKMK_BYOK_InPerson"></a>Gerar e transferir a chave de inquilino – pessoalmente
Utilize os procedimentos seguintes se não pretende transferir a chave de inquilino através da Internet, mas em vez disso, transferir a chave de inquilino na pessoa.

-   [Generate your tenant key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateKey)

-   [Transfer your tenant key to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Transfer)

#### <a name="BKMK_GenerateKey"></a>Gerar a chave de inquilino
Para gerar a sua própria chave do inquilino, siga estes 3 passos:

-   [Step 1: Prepare a workstation with Thales HSM](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey1)

-   [Step 2: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey2)

-   [Step 3: Create a new key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey3)

##### <a name="BKMK_GenerateYourKey1"></a>Passo 1: Preparar uma estação de trabalho com Thales HSM
Instale o software de suporte nCipher (Thales) num computador Windows. Anexe um HSM Thales nesse computador. Certifique-se de que as ferramentas de Thales estão no seu caminho. Para mais informações, consulte o guia de utilizador incluído com o HSM Thales ou visitar o Web site Thales para o Azure RMS em [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

##### <a name="BKMK_GenerateYourKey2"></a>Passo 2: Criar um mundo de segurança
Começar uma linha de comandos e executar o programa de novo mundo Thales.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Este programa cria um **segurança mundo** ficheiro em % NFAST_KMDATA%\local\world, que corresponde à pasta C:\ProgramData\nCipher\Key Data\local de gestão. Pode utilizar valores diferentes para o quórum mas no nosso exemplo, lhe for pedido para introduzir três cartões em branco e pins para cada um deles. Em seguida, quaisquer dois cartões dará acesso total para o mundo de segurança.  Estes cartões tornam-se a **administrador cartão definido** para o novo mundo de segurança.

Em seguida, efetue o seguinte:

1.  Instalar o fornecedor de Thales CNG conforme descrito na documentação do Thales e configure-o para utilizar o novo mundo de segurança.

2.  Agregar o ficheiro do mundo. Proteger e proteger o ficheiro do mundo, os cartões de administrador e os respetivos pins e certifique-se de que nenhum única pessoa tem acesso a mais do que um cartão.

Agora está pronto para criar uma nova chave que será a sua chave de inquilino do RMS.

##### <a name="BKMK_GenerateYourKey3"></a>Passo 3: Crie uma nova chave
Gerar uma chave CNG utilizando o Thales **generatekey** e **cngimport** programas.

Execute o seguinte comando para gerar a chave:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Quando executar este comando, utilize estas instruções:

-   Para o tamanho da chave, é recomendável 2048 mas também suportam chaves RSA de 1024 bits para clientes existentes do AD RMS que tem estas chaves e estão a migrar para o Azure RMS.

-   Substitua o valor do *contosokey* para o **ident** e **plainname** com qualquer valor de cadeia. Para minimizar a sobrecargas administrativas e reduzir o risco de erros, recomendamos que utilize o mesmo valor para ambos e utilize todos os carateres minúsculos.

-   O pubexp fica em branco (predefinição), neste exemplo, mas pode especificar valores específicos. Para mais informações, consulte a documentação de Thales.

Em seguida, execute o seguinte comando para importar a chave para CNG:

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
Quando executar este comando, utilize estas instruções:

-   Substituir *contosokey* com o mesmo valor que especificou no passo 1.

-   Utilize o **- M** opção para que a chave é adequada para este cenário. Sem esta situação, a chave resultante será uma chave de específica do utilizador para o utilizador atual.

Este comando cria um ficheiro de chave foi Atomizada na sua pasta %NFAST_KMDATA%\local com um nome, começando **key_caping_** seguido por um SID. Por exemplo: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Este ficheiro contém uma chave encriptada.

Agregar este ficheiro de chave foi Atomizada numa localização segura.

> [!IMPORTANT]
> Ao transferir a chave para o Azure RMS mais tarde, Microsoft terá uma cópia da sua chave não recuperável. Isto significa que ninguém pode obter a sua chave de HSMs na Microsoft. Isto permite-lhe manter exclusivo controlo sobre a sua chave de inquilino. E por isso torna muito importante que uma cópia de segurança do mundo de chave e de segurança em segurança. Procure Thales orientações e melhores práticas para a sua chave de segurança.

Agora está pronto para transferir a chave de inquilino para o Azure RMS.

#### <a name="BKMK_Transfer"></a>Transferir a chave de inquilino para o Azure RMS
Depois de ter gerado a sua própria chave, tem de transferi-lo para o Azure RMS antes de o utilizar. Para o nível mais elevado de segurança, esta transferência é um processo manual que requer que surgir para Microsoft office no Redmond, Washington, Unidos Estados of America. Para concluir este processo, siga estes 3 passos:

-   [Step 1: Bring your key to Microsoft](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey1)

-   [Step 2: Transfer your key to the Window Azure RMS security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey2)

-   [Step 3: Closing procedures](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey3)

###### Passo 1: Colocar a chave para a Microsoft

-   Contacte o Microsoft suporte ao cliente (CSS) para agendar um compromisso de transferência da chave para o Azure RMS. Trazer o seguinte procedimento para a Microsoft na Redmond:

    -   Um quórum dos seus cartões administrativo. Se se seguiu as instruções anteriores no [Step 2: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey2), estes são os dois dos seus três cartões.

    -   Técnico autorizado para realizar o seu cartões administrativas e pins, normalmente duas (uma para cada cartão).

    -   O ficheiro de segurança mundo (% NFAST_KMDATA%\local\world) numa unidade USB.

    -   O ficheiro chave, Atomizada, numa unidade USB.

###### Passo 2: Transferir a chave para o mundo de segurança de janela Azure RMS

1.  Quando chegar ao Microsoft para transferir a chave, ocorrerá o seguinte:

    -   A Microsoft fornece-lhe uma estação de trabalho offline com um HSM Thales ligado, o software de Thales instalado e um ficheiro do mundo de segurança do Azure RMS previamente carregado para a pasta C:\Temp\Destination.

    -   Desta estação de trabalho, carregar o ficheiro de segurança mundo e Atomizada ficheiro da chave a partir da sua unidade USB para a pasta C:\Temp\Source.

    -   Operadores do Azure RMS em segurança transferem a chave para o mundo de segurança do Azure RMS utilizando utilitários Thales.

    Este processo será semelhante ao seguinte, onde o último parâmetro da chave xfer MI neste exemplo é substituído pelo seu nome de ficheiro de chave foi Atomizada:

    **C:\ &gt; mk-reprogram.exe - c:\Temp\Destination proprietário adicionar c:\Temp\Source**

    **C:\ &gt; chave-xfer-im.exe c:\Temp\Source c:\Temp\Destination - c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb módulo**

2.  MK reprogram irá pedir-lhe e os operadores do Azure RMS para ligar os seus respetivos cartões de administrador e pins. Estes comandos gera um ficheiro de chave foi Atomizada no C:\Temp\Destination que contém a chave de protegidos pelo mundo de segurança do Azure RMS.

###### Passo 3: Fechar procedimentos

-   No seu estado de presença, os operadores do Azure RMS, efetue o seguinte:

    -   Execute uma ferramenta que desenvolvida pela Microsoft em colaboração com Thales que remove as duas permissões: A permissão para recuperar a chave e a permissão para alterar as permissões. Depois de terminar, esta cópia da sua chave está bloqueada para o mundo de segurança do Azure RMS. Thales HSMs irão permitir que os operadores do Azure RMs com os seus cartões de administrador para recuperar a cópia de texto simples da sua chave.

    -   Copie o ficheiro de chave resultante para uma unidade USB mais tarde carregar para o serviço do Azure RMS.

    -   Reposição de fábrica do HSM e apagar a estação de trabalho correto.

Agora concluiu todos os passos necessários para colocar a sua própria chave na pessoa e podem regressar à sua organização para conhecer os passos seguintes.

## <a name="BKMK_NextSteps"></a>Próximos passos

1.  Começa a utilizar a sua chave de inquilino:

    -   Se ainda não o fez, tem agora a ativar a gestão de direitos para que a sua organização pode começar a utilizar o RMS. Os utilizadores imediatamente a começar a utilizar a sua chave de inquilino (geridos pela Microsoft ou geridos por si).

        Para obter mais informações sobre a ativação, consulte o artigo [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

    -   Se tinha já ativado a gestão de direitos e, em seguida, decidiu gerir a sua própria chave do inquilino, os utilizadores gradualmente transição a partir da chave de inquilino antiga para a nova chave de inquilino e esta transição escalonada pode demorar alguns semanas a concluir. Documentos e ficheiros que foram protegidos com a chave de inquilinos antigo permanece acessível a utilizadores autorizados.

2.  Considere ativar o registo de utilização, que regista todas as transações que efetua RMS.

    Se decidiu gerir a sua própria chave do inquilino, o registo inclui informações sobre como utilizar a sua chave de inquilino. Consulte o exemplo seguinte de um ficheiro de registo apresentado no Excel onde o **desencriptar** e **SignDigest** pedido tipos mostrar que está a ser utilizada a chave de inquilino.

    ![](../Image/RMS_Logging.gif)

    Para obter mais informações sobre o registo de utilização, consulte o artigo [Registo e analisar a utilização de gestão de direitos do Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

3.  Manter a sua chave de inquilino.

    Para obter mais informações, consulte o artigo [Operações para a sua chave de inquilino do Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

