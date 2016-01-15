---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# Prote&#231;&#227;o RMS com infraestrutura de classifica&#231;&#227;o de ficheiros (FCI) do Windows Server
Utilize este artigo para obter instruções e um script para utilizar o cliente de gestão de direitos (RMS) com a ferramenta de proteção RMS para configurar o Gestor de recursos do servidor de ficheiros e infraestrutura de classificação de ficheiros (FCI).

Soluções de permite-lhe proteger automaticamente todos os ficheiros numa pasta num servidor de ficheiros com o Windows Server ou proteger automaticamente os ficheiros que correspondam a critérios específicos. Por exemplo, ficheiros que tenham sido classificados como contendo informações sensíveis ou confidenciais. Esta solução usa [Azure Rights Management](../Topic/Azure_Rights_Management.md) (RMS) do Azure para proteger os ficheiros de, pelo que tem de ter esta tecnologia implementada na sua organização.

> [!NOTE]
> Embora o Azure RMS inclui um [conector](https://technet.microsoft.com/library/dn375964.aspx) que suporta a infraestrutura de classificação de ficheiros, se a solução suporta apenas a proteção nativa — por exemplo, ficheiros do Office.
> 
> Para suportar a todos os tipos de ficheiro com a infraestrutura de classificação de ficheiros, tem de utilizar o Windows PowerShell **proteção RMS** módulo, conforme documentado neste artigo. Os cmdlets de proteção RMS, como a aplicação de partilha RMS suporta a proteção genérica, bem como a proteção nativa, o que significa que todos os ficheiros podem ser protegidos. Para mais informações sobre estes níveis de proteção diferentes, consulte o [Níveis de proteção – nativa e genérica](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) secção a [Guia partilha Rights Management aplicação administrador](../Topic/Rights_Management_sharing_application_administrator_guide.md).

As instruções que se seguem são para o Windows Server 2012 R2 ou Windows Server 2012. Se executar outras versões suportadas do Windows, poderá ter de adaptar alguns dos passos de diferenças entre a versão do sistema operativo e a descrita neste artigo.

## Pré-requisitos para proteção do Azure RMS com o Windows Server FCI
Pré-requisitos para estas instruções:

-   Em cada servidor de ficheiros onde será executada Gestor de recursos de ficheiros com infraestrutura de classificação de ficheiros:

    -   Instalou o Gestor de recursos do servidor de ficheiros como um dos serviços de função para a função Serviços de ficheiros.

    -   Identificar uma pasta local que contenha ficheiros que pretende proteger com o Rights Management. Por exemplo, C:\FileShare.

    -   Instalou a ferramenta de proteção RMS, incluindo os pré-requisitos para a ferramenta (por exemplo, o cliente RMS) e para o Azure RMS (por exemplo, a conta principal do serviço). Para obter mais informações, consulte o artigo [RMS proteção Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Se pretender alterar o nível predefinido de proteção RMS (nativo ou genérico) para extensões de nome de ficheiro específico, editou o registo, tal como descrito no [configuração ficheiro API](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) página.

    -   Tiver uma ligação à Internet, com as definições de computador configurado, se necessário para um servidor proxy. Por exemplo: `netsh winhttp import proxy source=ie`

-   Configurou as pré-requisitos adicionais para a implementação do Azure Rights Management, conforme descrito em [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). Especificamente, tem os seguintes valores para ligar para o Azure RMS, utilizando um principal de serviço:

    -   BposTenantId

    -   AppPrincipalId

    -   Chave simétrica

-   Foram sincronizados suas contas de utilizador do Active Directory no local com o Azure Active Directory ou o Office 365, incluindo o respetivo endereço de e-mail. Isto é necessário para todos os utilizadores que possam necessitar para aceder a ficheiros quando são protegidas pelo FCI e o Azure RMS. Se não efetuar este passo (por exemplo, num ambiente de teste), os utilizadores poderão estar impedidos de aceder a estes ficheiros. Se precisar de mais informações sobre esta configuração de conta, consulte o artigo [Preparar para o Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

-   Identificar o modelo de gestão de direitos para utilizar, que irá proteger os ficheiros. Certifique-se de que sabe o ID para este modelo utilizando o [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) cmdlet.

## Instruções para configurar o Gestor de recursos do servidor de ficheiros FCI para proteção do Azure RMS
Siga estas instruções para proteger automaticamente todos os ficheiros numa pasta, utilizando um script do Windows PowerShell como uma tarefa personalizada. Efetue estes procedimentos pela seguinte ordem:

1.  Guarde o script do Windows PowerShell

2.  Criar uma propriedade de classificação para gestão de direitos (RMS)

3.  Criar uma regra de classificação (classificar para RMS)

4.  Configurar a agenda de classificação

5.  Criar uma tarefa de gestão de ficheiros personalizadas (ficheiros proteger com RMS)

6.  Teste a configuração executando manualmente a regra e tarefas

No final destas instruções, irão ser classificados de todos os ficheiros na sua pasta selecionada com a propriedade personalizada do RMS e estes ficheiros, em seguida, serão protegidos por Rights Management. Para uma configuração mais complexa que protege seletivamente alguns ficheiros e não outros, em seguida, pode criar ou utilizar uma classificação diferente a propriedade e a regra, com uma tarefa de gestão de ficheiros que protege apenas esses ficheiros.

#### Guarde o script do Windows PowerShell

1.  Expanda o [Script do Windows PowerShell para a proteção do Azure RMS utilizando o Gestor de recursos do servidor de ficheiros FCI](#BKMK_RMSProtection_Script) secção neste artigo e copie o respetivo conteúdo. Colar o conteúdo do script e um nome de ficheiro **RMS-Protect-FCI.ps1** no seu próprio computador.

2.  Reveja o script e efetuar as seguintes alterações:

    -   Procurar o seguinte da cadeia e substituí-la com o seu próprio AppPrincipalId que utiliza com o [conjunto RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet para estabelecer ligação ao Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Por exemplo, o script poderá ser semelhante a:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Procurar o seguinte da cadeia e substituí-la com a sua própria chave simétrica que utiliza com o [conjunto RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet para estabelecer ligação ao Azure RMS:

        ```
        <enter your key here>
        ```
        Por exemplo, o script poderá ser semelhante a:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Procurar o seguinte da cadeia e substituí-la com o seu próprio BposTenantId (ID do inquilino), que utiliza com o [conjunto RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet para estabelecer ligação ao Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Por exemplo, o script poderá ser semelhante a:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Se o servidor está a executar o Windows Server 2012, terá de carregar manualmente o módulo de RMSProtection no início do script. Adicione o seguinte comando (ou equivalente, se a pasta de "Ficheiros de programa" está numa unidade diferente na unidade c::

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Inicie sessão o script. Se não iniciar o script (mais seguro), tem de configurar o Windows PowerShell nos servidores que execução-lo. Por exemplo, executar uma sessão do Windows PowerShell com o **Executar como administrador** opção e tipo: **Set-ExecutionPolicy Unrestricted**. No entanto, esta configuração permite executar (menos seguro) de scripts não assinados tudo.

    Para obter mais informações sobre como iniciar sessão scripts do Windows PowerShell, consulte o artigo [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) na biblioteca de documentação do PowerShell.

4.  Guarde o ficheiro localmente em cada servidor de ficheiros que será executado o Gestor de recursos de ficheiros com infraestrutura de classificação de ficheiros. Por exemplo, guarde o ficheiro no **C:\RMS-Protection**. Protege este ficheiro utilizando as permissões NTFS para que os utilizadores não autorizados não é possível modificá-lo.

Agora está pronto para iniciar a configuração do Gestor de recursos do servidor de ficheiros.

#### Criar uma propriedade de classificação para gestão de direitos (RMS)

-   No ficheiro de recurso Gestor de servidor, classificação de gestão, crie uma nova propriedade local:

    -   **Name**: Tipo **RMS**

    -   **Descrição**:   Tipo **Rights Management protection**

    -   **Tipo de propriedade**: Selecione **Sim/não**

    -   **Value**: Selecione **Sim**

Agora podemos criar uma regra de classificação que utiliza esta propriedade.

#### Criar uma regra de classificação (classificar para RMS)

-   Crie uma nova regra de classificação:

    -   No **Geral** separador:

        -   **Name**: Tipo **Classify for RMS**

        -   **Ativada**: Mantenha a predefinição, o que é que esta caixa de verificação está selecionada.

        -   **Descrição**: Tipo de **Classify all files in the &lt;folder name&gt; folder for Rights Management**.

            Substituir *&lt; nome da pasta &gt;* com o seu nome de pasta escolhida. Por exemplo, **classificar todos os ficheiros na pasta C:\FileShare para gestão de direitos**

        -   **Scope**: Adicione a sua pasta escolhida. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   No **classificação** separador:

    -   **Método classificação**: Selecione **classificador de pasta**

    -   **Propriedade** nome: Selecione **RMS**

    -   Propriedade **valor**: Selecione **Sim**

Apesar de conseguir executar as regras de classificação manualmente, para operações em curso, pretenderá esta regra a ser executado com base numa agenda, de modo a que irão ser classificados de novos ficheiros com a propriedade do RMS.

#### Configurar a agenda de classificação

-   No **classificação automática** separador:

    -   **Ativar agenda fixa**: Selecione esta caixa de verificação.

    -   Configure a agenda para todas as regras de classificação executar, que inclui a nossa nova regra para classificar ficheiros com a propriedade do RMS.

    -   **Permitir classificação contínua para novos ficheiros**: Selecione esta caixa de verificação para que seja classificados novos ficheiros.

    -   Opcional: Faça as alterações que pretende, como configurar as opções de relatórios e notificações.

Agora que concluiu a configuração de classificação, está pronto para configurar uma tarefa de gestão para aplicar a proteção RMS para os ficheiros.

#### Criar uma tarefa de gestão de ficheiros personalizadas (ficheiros proteger com RMS)

-   No **tarefas de gestão de ficheiros**, criar uma nova tarefa de gestão do ficheiro:

    -   No **Geral** separador:

        -   **Nome da tarefa**: Tipo **Protect files with RMS**

        -   Manter o **Ativar** caixa de verificação selecionada.

        -   **Descrição**: Tipo **Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script.**

            Substituir *&lt; nome da pasta &gt;* com o seu nome de pasta escolhida. Por exemplo, **proteger ficheiros em C:\FileShare com gestão de direitos e um modelo utilizando um script do Windows PowerShell**

        -   **Scope**: Selecione a pasta escolhida. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   No **ação** separador:

        -   **Type**: Selecione **personalizada**

        -   **Executável**: Especifique o seguinte:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Se o Windows não estiver na sua unidade c:, modificar este caminho ou procure este ficheiro.

        -   **Argumento**: Especifique o seguinte, fornecer os seus próprios valores para &lt; caminho &gt; e &lt; ID do modelo &gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Por exemplo, se copiou o script para C:\RMS-Protection e o ID de modelo identificou a partir das pré-requisitos é e6ee2481-26b9-45e5-b34a-f744eacd53b0, especifique o seguinte:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            Este comando, **[caminho de ficheiro de origem]** e **[E-mails de proprietário do ficheiro de origem]** estão ambas as variáveis de FCI específicos, por isso, escreva estas exatamente tal como aparecem no comando acima. Primeiro é utilizado pelo FCI para especificar automaticamente o ficheiro identificado na pasta e o segundo é para FCI obter o endereço de e-mail do proprietário com nome do ficheiro identificado automaticamente. Este comando é repetido para cada ficheiro na pasta, sendo no nosso exemplo, cada ficheiro na pasta C:\FileShare que tem para além disso, o RMS como uma propriedade de classificação de ficheiros.

            > [!NOTE]
            > O **-OwnerMail [Source File Owner Email]** parâmetro e o valor garante que o proprietário do ficheiro original é concedido o proprietário de gestão de direitos do ficheiro depois de ser protegido. Isto garante que o proprietário do ficheiro original tem todos os direitos de gestão de direitos para os seus ficheiros. Quando os ficheiros são criados por um utilizador de domínio, o endereço de e-mail é obtido automaticamente a partir do Active Directory utilizando o nome de conta de utilizador na propriedade de proprietário do ficheiro. Para fazer isto, o servidor de ficheiros tem de ser no mesmo domínio ou domínio fidedigno como o utilizador.
            > 
            > Sempre que possível, atribua os proprietários originais para documentos protegidos, para garantir que estes utilizadores continuam a ter controlo total sobre os ficheiros que são criados. No entanto, se utilizar a variável [E-mails de proprietário do ficheiro de origem] conforme apresentado acima e um ficheiro não tem um utilizador de domínio definido como o proprietário (por exemplo, uma conta local foi utilizada para criar o ficheiro, para que o proprietário apresenta SYSTEM), o script irá falhar.
            > 
            > Para ficheiros que não dispõem de um utilizador de domínio como proprietário, pode copiar e poupe estes ficheiros como um utilizador de domínio, para que o tornam-se o proprietário apenas a estes ficheiros. Em alternativa, se tiver as permissões, pode alterar manualmente o proprietário.  Ou, em alternativa, pode fornecer um endereço de correio eletrónico específico (tal como a sua própria ou um endereço de grupo para o departamento de TI) em vez da variável [E-mails de proprietário do ficheiro de origem], o que significa que todos os ficheiros a proteger ao utilizar este script irão utilizar este endereço de correio eletrónico para definir o novo proprietário.

    -   **Execute o comando como**: Selecione **Sistema Local**

    -   No **condição** separador:

        -   **Propriedade**: Selecione **RMS**

        -   **Operador**: Selecione **igual**

        -   **Value**: Selecione **Sim**

    -   No **agenda** separador:

        -   **Run at**: Configure a sua agenda preferencial.

            Permita bastante tempo para o script concluir. Embora esta solução protege todos os ficheiros na pasta, o script é executado uma vez para cada ficheiro, cada vez. Apesar de isto demora mais do que a proteger todos os ficheiros ao mesmo tempo, que a ferramenta de proteção RMS suporta, esta configuração de ficheiro ao ficheiro para FCI é mais eficiente. Por exemplo, os ficheiros protegidos podem ter diferentes proprietários (manter o proprietário original) quando utiliza a variável [E-mails de proprietário do ficheiro de origem] e esta ação ao ficheiro será necessária se posteriormente alterar a configuração para seletivamente proteger ficheiros em vez de todos os ficheiros numa pasta.

        -   **Executar continuamente em novos ficheiros**: Selecione esta caixa de verificação.

#### Teste a configuração executando manualmente a regra e tarefas

1.  Execute a regra de classificação:

    1.  Clique em **regras de classificação** &gt; **Executar agora classificação com todas as regras**

    2.  Clique em **aguardar classificação concluir**, e, em seguida, clique em **OK**.

2.  Aguarde que o **Executar classificação** caixa de diálogo Fechar e, em seguida, ver os resultados no relatório automaticamente apresentado. Deverá ver **1** para o **Propriedades** campo e o número de ficheiros na sua pasta. Certifique-se através do Explorador de ficheiros e a verificar as propriedades dos ficheiros na sua pasta escolhido. No **classificação** separador, deverá ver **RMS** como um nome de propriedade e **Sim** para o respetivo **valor**.

3.  Execute a tarefa de gestão do ficheiro:

    1.  Clique em **tarefas de gestão de ficheiros** &gt; **Proteja os ficheiros com RMS** &gt; **Executar ficheiro gestão tarefa agora**

    2.  Clique em **Espere que a tarefa concluir**, e, em seguida, clique em **OK**.

4.  Aguarde que o **executar tarefa de gestão do ficheiro** caixa de diálogo Fechar e, em seguida, ver os resultados no relatório automaticamente apresentado. Deverá ver o número de ficheiros que estão na sua pasta escolhida no **ficheiros** campo. Certifique-se de que os ficheiros na sua pasta escolhido estão agora protegidos pelo RMS. Por exemplo, se a sua pasta escolhida é C:\FileShare, escreva o seguinte numa sessão do Windows PowerShell e confirme que não existem ficheiros têm um Estado de **UnProtected**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Algumas sugestões de resolução de problemas:
    > 
    > -   Se vir **0** no relatório, em vez do número de ficheiros na sua pasta, isto indica que o script não foi executado. Em primeiro lugar, verifique o script próprio por carregá-lo no ISE do Windows PowerShell para validar os conteúdos de script e tentar executar para ver se os erros são apresentados. Sem argumentos especificado, o script irá tentar estabelecer ligação e autenticar o Azure RMS.
    > 
    >     -   Se o script de relatórios que não foi possível ligar ao Azure RMS, verifique os valores que é apresentado para a conta serviço principal que especificou no script.  Para obter mais informações sobre como criar esta conta principal do serviço, consulte o pré-requisito segundo no [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Se o script de relatórios que que foi possível estabelecer ligação ao Azure RMS e a sua região Azure está fora da América do Norte, verifique que editou o registo corretamente para esta configuração. Um teste boa para isto é execute Get-RMSTemplate diretamente a partir do Windows PowerShell no servidor. Para mais informações sobre as edições de registo, consulte o pré-requisito no terceiro [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Se o script por si só é executada no ISE do Windows PowerShell sem erros, tente executar o seguinte a partir de uma sessão do PowerShell, especificando um nome de ficheiro para proteger e sem o parâmetro - OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Se o script seja executada com êxito nesta sessão do Windows PowerShell, verifique as entradas para **Executive** e **argumento** na ação de tarefa de gestão de ficheiros.  Se tiver especificado **- OwnerEmail [E-mails de proprietário do ficheiro de origem]**, tente remover este parâmetro.
    > 
    >         Se a tarefa de gestão de ficheiro funciona com êxito sem  **- OwnerEmail [E-mails de proprietário do ficheiro de origem]**, verifique se os ficheiros de grupo de computadores portáteis têm um utilizador de domínio listado como o proprietário do ficheiro, em vez de **sistema**.  Para tal, utilize o **segurança** separador Propriedades do ficheiro e, em seguida, clique em **Avançadas**. O **proprietário** valor é apresentado imediatamente após o ficheiro **nome**. Além disso, certifique-se de que o servidor de ficheiros está no mesmo domínio ou num domínio fidedigno para pesquisar o endereço de correio eletrónico do utilizador a partir de serviços de domínio do Active Directory.
    > -   Se vir o número correto de ficheiros no relatório, mas os ficheiros não são protegidos, experimente proteger os ficheiros manualmente utilizando o [proteger RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) cmdlet, para ver se os erros são apresentados.

Quando tiver confirmado que estas tarefas são executadas com êxito, pode fechar o Gestor de recursos de ficheiros. Novos ficheiros serão protegidos automaticamente e todos os ficheiros serão protegidos novamente ao executam as agendas. Volte a proteger ficheiros garante que quaisquer alterações ao modelo são aplicadas para os ficheiros.

### <a name="BKMK_RMSProtection_Script"></a>Script do Windows PowerShell para a proteção do Azure RMS utilizando o Gestor de recursos do servidor de ficheiros FCI
Esta secção contém o script de exemplo para copiar e editar, conforme descrito na secção anterior.

*&#42;&#42;Exclusão de responsabilidade&#42;&#42;: Este script de exemplo não é suportado em qualquer serviço ou programa de suporte padrão da Microsoft. Este script de exemplo é fornecido como é, sem garantias de qualquer tipo.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## Modificar as instruções para seletivamente proteger ficheiros
Quando tiver as instruções anteriores a trabalhar, em seguida, é muito fácil modificá-los para uma configuração mais sofisticada. Por exemplo, proteger ficheiros utilizando o mesmo script mas apenas para ficheiros que contêm informações de identificação pessoas e, talvez, selecione um modelo que tenha direitos mais restritivas.

Para tal, utilize uma das propriedades de classificação incorporadas (por exemplo, **informação identificativa**) ou criar o seu próprio nova propriedade. Em seguida, crie uma nova regra que utiliza esta propriedade. Por exemplo, poderá selecionar o **classificador conteúdo**, escolha o **informação identificativa** propriedade com um valor de **elevada**, e configurar o padrão de cadeia ou expressão que identifica o ficheiro a ser configurado para esta propriedade (tais como a cadeia "**data de nascimento**").

Agora que precisa é criar uma nova tarefa de gestão de ficheiros que utiliza o mesmo script, mas talvez com um modelo diferente e configurar a condição para a propriedade de classificação que tiver configurado recentemente. Por exemplo, em vez da condição que são configurados anteriormente (**RMS** propriedade **igual**, **Sim**), selecione o **informação identificativa** propriedade com o **operador** valor definido para **igual** e o **valor** de **elevada**.

