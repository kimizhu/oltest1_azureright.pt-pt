---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Configurar modelos personalizados para o Azure Rights Management
Depois de ter ativado o Azure Rights Management (RMS) do Azure, os utilizadores são automaticamente capazes de utilizar dois modelos de predefinição que tornam mais fácil para os mesmos aplicar políticas de ficheiros confidenciais que restringir o acesso a utilizadores autorizados na sua organização. Estes dois modelos de tem as seguintes restrições de política de direitos:

-   Visualização de só de leitura para o conteúdo protegido

    -   Nome a apresentar: **&lt; nome da organização &gt; - apenas visualização confidencial**

    -   Permissão específicos: Visualização de conteúdo

-   Ler ou modificar permissões para o conteúdo protegido

    -   Nome a apresentar: **&lt; nome da organização &gt; - confidencial**

    -   Permissões específicas: Ver o conteúdo, guarde o ficheiro, editar o conteúdo, veja direitos atribuídos, permitir que as Macros, reencaminhar, responder, responder a todos

Além disso, o [aplicação de partilha RMS](http://technet.microsoft.com/library/dn339006.aspx) permite aos utilizadores definir o seu próprio conjunto de permissões. E, para o cliente do Outlook e Outlook Web Access, os utilizadores podem selecionar o **não reencaminhar** opção para mensagens de correio eletrónico.

Para muitas organizações, os modelos predefinidos poderão ser suficientes. Mas se pretender criar seus próprios direitos personalizados modelos de política, pode fazê-lo. Motivos para a criação de um modelo personalizado incluem o seguinte:

-   Um modelo para conceder direitos para um subconjunto de utilizadores na organização em vez de todos os utilizadores que pretende.

-   Pretende apenas um subconjunto de permitir que os utilizadores consigam ver e selecionar um modelo (departamental modelo) a partir de aplicações, em vez de todos os utilizadores na organização veem e pode selecionar o modelo.

-   Pretende definir um personalizado para a direita para um modelo, tal como ver e editar, mas não copiar e imprimir.

-   Se pretender configurar opções adicionais num modelo que incluem uma data de validade e se o conteúdo pode ser acedido sem uma ligação à Internet.

Para permitir que os utilizadores selecionar um modelo personalizado que contém definições como estas, tem primeiro de criar um modelo personalizado, configurá-lo e, em seguida, publicá-lo.

Utilize as secções seguintes para o ajudar a configurar e utilizar modelos personalizados:

-   [Como criar, configurar e publicar um modelo personalizado](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [Como copiar um modelo](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [Como remover modelos (arquivo)](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [Atualizar Modelos para utilizadores](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Referência do Windows PowerShell](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Como criar, configurar e publicar um modelo personalizado
Criar e gerir modelos personalizados no Portal de gestão do Azure. Pode fazê-lo diretamente a partir do portal de gestão do Azure, ou pode iniciar sessão no Centro de administração do Office 365 e escolha o **funcionalidades avançadas** para a gestão de direitos, que, em seguida, redireciona para o portal de gestão do Azure.

Utilize os procedimentos seguintes para criar, configurar e publicar modelos personalizados para o Rights Management.

#### Para criar um modelo personalizado

1.  Dependendo se iniciar sessão Centro de administração do Office 365, ou no Portal do Azure, efetue um dos seguintes procedimentos:

    -   A partir de [Centro de administração do Office 365](https://portal.office.com/):

        1.  No painel da esquerda, clique em **definições do serviço**.

        2.  A partir de **definições do serviço** página, clique em **Gestão de direitos de**.

        3.  No **proteger as suas informações** secção, clique em **Gerir**.

        4.  No **Gestão de direitos de** secção, clique em **funcionalidades avançadas**.

            > [!NOTE]
            > Se ainda não tiver ativado a gestão de direitos, primeiro clique **Ativar** e confirme a ação. Para obter mais informações, consulte o artigo [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Se ainda não clicou em **funcionalidades avançadas** antes, depois do Rights Management está ativado, siga no ecrã instruções para obter uma subscrição gratuita do Azure que seja necessário para aceder ao Portal do Azure.

            Ao clicar em **funcionalidades avançadas** carrega o portal do Azure, onde pode gerir **RIGHTS MANAGEMENT** para o Azure Active Directory da sua organização.

    -   A partir de [Portal do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  No painel da esquerda, clique em **do Active Directory**.

        2.  A partir de **do Active Directory** página, clique em **RIGHTS MANAGEMENT**.

        3.  Selecione o diretório para gerir para gestão de direitos.

        4.  Se já não tiver ativado a gestão de direitos, clique em **ATIVAR** e confirme a ação.

            > [!NOTE]
            > Para obter mais informações, consulte o artigo [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

2.  Crie um novo modelo:

    -   No portal do Azure, a partir de **começar com o Rights Management** rápida começar a página, clique em **criar um novo modelo de política de direitos**.

        Se não visualizar imediatamente esta página depois de seguir as instruções para o Office 365, utilize as instruções de navegação, acima, para o portal do Azure.

3.  No **Adicionar um novo modelo de política de direitos** página, selecione um idioma no qual irá escrever o nome do modelo e a descrição que será visto pelos utilizadores (pode adicionar mais idiomas mais tarde). Em seguida, escreva um nome exclusivo e uma descrição e clique no botão concluído.

A partir de **começar com o Rights Management** rápida começar a página, agora, clique em **Gestão de modelos de política de direitos**. Verá o modelo criado recentemente adicionado à lista de modelos, com o estado de **Archived**. Nesta fase, o modelo é criado, mas não configurado e não é visível para os utilizadores.

#### Para configurar e publicar um modelo personalizado

1.  Selecione o seu modelo criado recentemente a partir de **modelos** página no Portal de gestão do Azure.

2.  A partir do **o modelo foi adicionado** rápida começar a página, clique em **começar** no passo 1, **configurar os direitos dos utilizadores e grupos,** em seguida, clique em **começar agora** ou **Adicionar**, e, em seguida, selecione os utilizadores e grupos que irão têm direitos para utilizar o conteúdo que é protegido pelo modelo de novo.

    > [!NOTE]
    > Os utilizadores ou grupos que selecionou tem de ter um endereço de e-mail. Num ambiente de produção, este será quase sempre as maiúsculas e minúsculas mas num ambiente de teste simple, poderá ter de adicionar endereços de correio eletrónico para as contas de utilizador ou grupos.

    Como melhor prática, utilize grupos em vez de utilizadores, o que simplifica a gestão dos modelos. Se tiver do Active Directory no local e estão a sincronizar para o Azure AD, pode utilizar os grupos com capacidade de correio que são grupos de segurança ou os grupos de distribuição. No entanto, se pretende conceder direitos para todos os utilizadores na organização, irá ser mais eficiente para copiar um dos modelos predefinidos, em vez de especificar vários grupos. Para obter mais informações, consulte o [Como copiar um modelo](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) deste tópico.

    > [!TIP]
    > Mais tarde pode adicionar utilizadores a partir de fora da sua organização para o modelo utilizando o [módulo do Windows PowerShell para o Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) e utilizar um dos seguintes métodos:
    > 
    > -   **Exportação, edite e importar o modelo atualizado**:  Este é o método mais simples para adicionar utilizadores externos a um modelo existente que inclui a outros grupos. Utilize o [exportação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet para exportar o modelo a um. Ficheiro CSV que podem ser editados para adicionar os endereços de e-mail externo destes utilizadores e os respetivos direitos sobre os grupos existentes e direitos. Em seguida, utilize o [importação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) cmdlet para importar esta alteração de volta para o Azure RMS.
    > -   **Utilizar um objeto de definição de direitos para atualizar um modelo**:    Especifique os endereços de e-mail externo e os respetivos direitos de um objeto de definição de direitos, que, em seguida, utilizar para atualizar o seu modelo. Especificar o objeto de definição de direitos, utilizando o [Novo AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet para criar uma variável e, em seguida, fornecer esta variável para o parâmetro - RightsDefinition com o [AadrmTemplateProperty conjunto](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet para modificar um modelo existente. No entanto, se estiver a adicionar estes utilizadores para um modelo existente, também terá de definir os objetos de definição de direitos para os grupos existentes nos modelos e não apenas os utilizadores externos, novo.

3.  Clique no botão seguinte e, em seguida, atribua uma das indicadas direitos seus selecionada de utilizadores e grupos.

    Utilize a descrição apresentada para obter mais informações sobre cada direito (e para direitos personalizados). Informações mais detalhadas também estão disponíveis no [Configuração de direitos de utilização para o Azure Rights Management](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). No entanto, as aplicações que suportam RMS poderão variar em como implementem estes direitos. Consulte a respetiva documentação e o seu próprio teste com as aplicações que os utilizadores utilizam para verificar o comportamento antes de implementar o modelo para os utilizadores. Para tornar este modelo é visível para apenas os administradores para este teste, tornar este modelo de um modelo departamental (passo 6).

4.  Se tiver selecionado **personalizado**, clique no botão seguinte e, em seguida, selecione esses direitos personalizados.

    Apesar de poder utilizar qualquer combinação dos direitos individuais disponíveis, algumas aplicações, alguns direitos podem ter dependências nos outros direitos individuais. Quando for este o caso, os direitos dependentes são automaticamente selecionados por si.

    > [!TIP]
    > Considere adicionar o **copiar e extrair conteúdo** com o botão direito e conceder esta a administradores selecionados ou técnico nas outras funções que tenham responsabilidades para recuperação de informações. Conceder este direito permite-lhes a remover a proteção se necessário, a partir dos ficheiros e mensagens de correio eletrónico que serão protegidas utilizando este modelo. Esta capacidade para remover a proteção ao nível do modelo fornece mais controlo detalhado ao utilizar a funcionalidade de utilizador super.

5.  Clique no botão concluído.

6.  Se pretender que o modelo para estar visíveis para apenas um subconjunto de utilizadores quando poderão ver uma lista de modelos de aplicações: Clique em **âmbito** para configurar esta opção como um modelo de departamentos e clique em **começar agora**. Caso contrário, avance para o passo 9.

    Mais informações sobre modelos departamentais: Por predefinição, todos os utilizadores do Azure Active veem todos os modelos publicados e podem, em seguida, selecioná-los a partir de aplicações quando pretendem a proteger conteúdo. Se pretender que os utilizadores específicos apenas para ver alguns dos modelos publicados, deve definir o âmbito de modelos para estes utilizadores. Em seguida, apenas estes utilizadores será possível selecionar estes modelos. Outros utilizadores que não forem especificados não verá os modelos e por isso, não é possível selecioná-las. Esta técnica pode fazer com que escolher o modelo correto mais fácil para os utilizadores, especialmente quando cria modelos que são concebidos para serem utilizados por grupos específicos ou departamentos. Os utilizadores, em seguida, ver apenas os modelos que foram concebidos para os mesmos.

    Por exemplo, criou um modelo para o departamento de recursos humanos que se aplica a permissão só de leitura para os membros departamento financeiro. Para que apenas os membros do departamento de recursos humanos podem aplicar este modelo quando estiverem a utilizar a aplicação de partilha Rights Management, o âmbito o modelo para o grupo de ativar o correio eletrónico denominada HumanResources. Em seguida, apenas os membros deste grupo Consulte o artigo e pode aplicam este modelo.

7.  No **modelo visibilidade** página, selecione os utilizadores e grupos que vão conseguir ver e selecionar o modelo a partir de aplicações suportadas por RMS. Como anteriormente, como melhor prática, utilize grupos em vez de utilizadores e grupos ou utilizadores que selecionar tem de ter um endereço de e-mail.

8.  Clique no botão seguinte e decidir se precisa de configurar a compatibilidade de aplicação para o modelo departamental. Se o fizer, clicar em **compatibilidade APLICACIONAL**, selecione a caixa de verificação e clique em **concluída**.

    Por que razão poderá é necessário configurar compatibilidade aplicacional? Nem todas as aplicações podem suportar modelos departamentais. Para tal, a aplicação tem primeiro de autenticar com o serviço de RMS antes de transferir os modelos. Se o processo de autenticação não ocorrer, por predefinição, nenhum dos modelos departamentais são transferidos. Pode substituir este comportamento, especificando que todos os modelos departamentais deverá ser transferido, configurando a compatibilidade de aplicação e selecionar o **Mostrar este modelo para todos os utilizadores quando as aplicações não suportam a identidade do utilizador** caixa de verificação.

    Por exemplo, se não configurar compatibilidade de aplicação para o modelo departamental no nosso exemplo de recursos humanos, apenas os utilizadores do departamento de recursos humanos veem o modelo departamental quando utilizarem a aplicação de partilha RMS, mas nenhum utilizador ver o modelo departamental quando utilizarem o Outlook Web Access (OWA) do Exchange Server 2013 porque OWA do Exchange e do Exchange ActiveSync não atualmente suportam modelos departamentais. Se substituir este comportamento predefinido ao configurar a compatibilidade de aplicação, apenas os utilizadores do departamento de recursos humanos consulte o modelo departamental quando utilizarem a aplicação de partilha RMS, mas todos os utilizadores veem o modelo departamental quando utilizarem o Outlook Web Access (OWA). Se os utilizadores utilizam o Outlook Web App ou do Exchange ActiveSync do Exchange Online, todos os utilizadores irão ver os modelos de departamentos ou não os utilizadores não verão os modelos de departamento, com base no estado de modelo (arquivo ou publicado) no Exchange Online.

    > [!NOTE]
    > Se tiver aplicações que ainda não suportem nativamente departamentais modelos, pode utilizar um [script de transferência do modelo de RMS personalizado](http://go.microsoft.com/fwlink/?LinkId=524506) ou outras ferramentas para implementar estes modelos na pasta de cliente RMS local. Em seguida, estas aplicações apresentará corretamente os modelos departamentais apenas para os utilizadores e grupos que selecionou para o âmbito do modelo:
    > 
    > -   Para o Office 2010, a pasta do cliente é **%localappdata%\Microsoft\DRM\Templates**.
    > -   A partir de um computador cliente que tenha transferido todos os modelos, pode copiar e, em seguida, cole os ficheiros de modelo para outros computadores.
    > 
    > Office 2016 suporta nativamente departamentais modelos e, por isso faz o Office 2013 com as atualizações mais recentes do Office ([KB 3054853](https://support.microsoft.com/kb/3054853)).

9. Clique em **configurar** e adicionar outros idiomas de que os utilizadores a utilizar, juntamente com o nome e descrição deste modelo nesse idioma. Quando tiver utilizadores multilíngue, é importante adicionar cada idioma que utilizar e fornecer um nome e descrição nesse idioma. Os utilizadores verão, em seguida, o nome e descrição do modelo no mesmo idioma como respetivo sistema operativo de cliente, que garante que compreender a política aplicada a uma mensagem de correio eletrónico ou documento. Se não existir nenhuma correspondência com o respetivo sistema operativo do cliente, o nome e descrição Verão reverterá para o idioma e a descrição que foi por si definido quando é criado pela primeira vez o modelo.

    Em seguida, selecione se pretende efetuar quaisquer alterações para as seguintes definições:

    |Definição|Obter mais informações|
    |-------------|--------------------------|
    |**expiração de conteúdos**|Defina uma data ou número de dias para este modelo ao não deverá abrir ficheiros que estão protegidos pelo modelo. Pode especificar uma data ou especificar um número de dias, começando a partir do momento em que a proteção é aplicada ao ficheiro.<br /><br />Quando especificar uma data, é Efetivo meia-noite, no seu fuso horário atual.|
    |**acesso offline**|Utilize esta definição para balancear a quaisquer requisitos de segurança que pode ter contra o requisito de que os utilizadores têm de conseguir abrir ficheiros protegidos quando que não tenham uma ligação à Internet.<br /><br />Se especificar que conteúdo não está disponível sem uma ligação à Internet ou que o conteúdo só está disponível para um número especificado de dias, quando esse foi atingido o limiar, os utilizadores têm de ser novamente autenticados e os respetivos acesso está registado. Quando isto acontecer, se as respetivas credenciais não estão em cache, são pedido aos utilizadores que iniciem sessão antes de que podem abrir o ficheiro.<br /><br />Além da autenticação, é a avaliação da política e a associação ao grupo de utilizador. Isto significa que os utilizadores foi experiência resultados de acesso diferente para o mesmo ficheiro, se existirem alterações na associação política ou grupo a partir do quando estes acedida pela última vez o ficheiro.|

10. Quando tiver a certeza de que o modelo está configurado corretamente para os seus utilizadores, clique em **publicar** tornar o modelo visíveis para os utilizadores e, em seguida, clique em **Guardar**.

11. Clique no botão anterior no Portal de gestão para voltar para o **modelos** página, onde o seu modelo tem agora um Estado atualizado da **publicada**.

Para efetuar quaisquer alterações ao seu modelo, selecioná-la e, em seguida, utilize os passos de início rápido novamente. Em alternativa, selecione uma das seguintes opções:

-   Para adicionar mais utilizadores e grupos e definir os direitos para esses utilizadores e grupos: Clique em **direitos**, em seguida, clique em **Adicionar**.

-   Para remover utilizadores ou grupos que selecionou anteriormente: Clique em **direitos**, selecione o utilizador ou grupo da lista e, em seguida, clique em **Eliminar**.

-   Para alterar quais os utilizadores podem ver os modelos para os selecionar a partir de aplicações: Clique em **âmbito**, em seguida, clique em **Adicionar** ou **Eliminar**, ou **compatibilidade APLICACIONAL**.

-   Para que o modelo já não é visível para todos os utilizadores: Clique em **configurar**, clique em **arquivo**, e, em seguida, clique em **Guardar**.

-   Para efetuar outras alterações de configuração: Clique em **configurar**, efetue as alterações pretendidas e, em seguida, clique em **Guardar**.

> [!WARNING]
> Quando fizer alterações a um modelo que foi guardado anteriormente, os clientes não irão ver essas alterações para o modelo até que os modelos são atualizados nos respetivos computadores. Para obter mais informações, consulte o [Atualizar Modelos para utilizadores](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) deste tópico.

## <a name="BKMK_HowToCopyTemplates"></a>Como copiar um modelo
Se pretender criar um novo modelo que tenha definições muito semelhantes a um modelo existente, selecione o modelo original no **modelos** página, clique em **cópia**, especifique um nome exclusivo e efetue as alterações que precisa.

> [!IMPORTANT]
> Quando copiar um modelo, o **publicada** ou **Archived** estado é também copiado. Para se copiar um modelo publicado, o estado dela imediato será publicado, a menos que pode alterá-lo.

Pode copiar modelos personalizados e modelos predefinidos. Como melhor prática, copie um dos modelos predefinidos em vez de criar um novo modelo personalizado, se pretender que o modelo para conceder direitos para todos os utilizadores na sua organização. Este método significa que não tenha de criar ou selecionar vários grupos para especificar todos os utilizadores. Neste cenário no entanto, certifique-se especificar um novo nome e uma descrição para o modelo copiado para idiomas adicionais.

## <a name="BKMK_HowToArchiveTemplates"></a>Como remover modelos (arquivo)
Não não possível eliminar modelos predefinidos, mas podem ser arquivados para que os utilizadores não veem-los.

Do mesmo modo, se tiver publicado um modelo personalizado e já não pretender que os utilizadores possam vê-lo, pode editar o modelo e escolher **arquivo** e **Guardar** a partir de **configurar** página. Em alternativa, pode selecionar a partir do **modelos** página e selecione **arquivo**.

Porque não é possível editar modelos predefinidos, para arquivar estes modelos, tem de utilizar o **arquivo** opção a partir de **modelos** página. Não é possível arquivar o Outlook **não reencaminhar** opção.

#### Para remover um modelo predefinido

-   A partir de **modelos** página, selecione o modelo predefinido e clique em **arquivo**.

O estado é alterado de **publicada** para **Archived**. Se mudar de ideias, selecione o modelo e clique em **publicar**.

## <a name="BKMK_RefreshingTemplates"></a>Atualizar Modelos para utilizadores
Quando utiliza o Azure RMS, modelos são automaticamente transferidos para computadores cliente para que os utilizadores possam selecioná-las as suas aplicações. No entanto, poderá ter de efetuar passos adicionais se fizer alterações aos modelos de:

|Aplicação ou um serviço|Como os modelos são atualizados depois das alterações|
|---------------------------|---------------------------------------------------------|
|Exchange Online|Configuração manual necessária para atualizar os modelos.<br /><br />Para obter os passos de configuração, expanda a secção seguinte, [Exchange Online apenas: Como configurar o Exchange para transferir alterado modelos personalizados](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365|Atualizados automaticamente – não existem passos adicionais necessários.|
|2016 do Office e Office 2013<br /><br />Aplicação para o Windows de partilha RMS|Atualizados automaticamente – com base numa agenda:<br /><br />-   Para obter estas versões posteriores do Office: O intervalo de atualização predefinido é de 7 dias.<br />-   Para a aplicação de partilha RMS para Windows: A partir da versão 1.0.1784.0, o intervalo de atualização predefinido é a cada 1 dia. As versões anteriores têm uma predefinição atualizar o intervalo de intervalos de 7 dias.<br /><br />Para forçar uma atualização mais cedo do que esta agenda, expanda a secção seguinte, [2016 do Office, Office 2013 e aplicações para Windows de partilha RMS: Como forçar uma atualização para um modelo personalizado alterado](#BKMK_Office2013ForceUpdate).|
|Office 2010|Atualizados quando os utilizadores iniciar sessão.<br /><br />Para forçar uma atualização, solicite ou forçar utilizadores a terminar sessão e iniciar sessão novamente novamente. Ou, consulte a secção seguinte, [Apenas para o Office 2010: Como forçar uma atualização para um modelo personalizado alterado](#BKMK_Office2010ForceUpdate).|
Para dispositivos móveis que utilizam a aplicação de partilha RMS, modelos são automaticamente transferidos (e atualizados se for necessário) sem ser necessária configuração adicional.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Exchange Online apenas: Como configurar o Exchange para transferir alterado modelos personalizados
Se já tiver configurado a gestão de direitos de informação (IRM) para o Exchange Online, modelos personalizados não transferirá para utilizadores até que efetue as seguintes alterações utilizando o Windows PowerShell no Exchange Online.

> [!NOTE]
> Para obter mais informações sobre como utilizar o Windows PowerShell no Exchange Online, consulte o artigo [através do PowerShell com o Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Tem de efetuar este procedimento sempre que alterar um modelo.

##### Atualizar Modelos para o Exchange Online

1.  Com o Windows PowerShell no Exchange Online, ligar ao serviço:

    1.  Forneça o nome de utilizador do Office 365 e a palavra-passe:

        ```
        $Cred = Get-Credential
        ```

    2.  Ligar ao serviço do Exchange Online, executando os seguintes dois comandos:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Utilize o [importação RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) cmdlet para voltar a importar o domínio de publicação fidedigno (TPD) a partir do Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Por exemplo, se o nome TPD for **do RMS Online - 1** (nome típico para muitas organizações), introduza: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Para verificar o seu nome TPD, pode utilizar o [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) cmdlet.

3.  Para confirmar que os modelos importou com êxito, aguarde alguns minutos e, em seguida, execute o [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) cmdlet e definir o tipo a todos. Por exemplo:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > É útil manter uma cópia da saída para que pode facilmente copiar os nomes de modelo ou GUIDs se é um modelo de arquivar mais tarde.

4.  Para cada modelo importado que pretende que sejam disponibilizados no Outlook Web App, tem de utilizar o [conjunto RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet e definir o tipo como distribuídas:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Porque o Outlook Web Access coloca em cache da IU para 24 horas, os utilizadores não poderão ver o novo modelo para até por dia.

Além disso, se se arquivam um modelo (personalizado ou predefinido) e utilize o Exchange Online com o Office 365, os utilizadores irão continuar a ver os modelos arquivados se utilizarem o Outlook Web App ou os dispositivos móveis que utilizam o protocolo do Exchange ActiveSync.

Para que os utilizadores já não veem estes modelos, ligar ao serviço, utilizando o Windows PowerShell no Exchange Online e, em seguida, utilize o [conjunto RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet executando o seguinte comando:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>2016 do Office, Office 2013 e aplicações para Windows de partilha RMS: Como forçar uma atualização para um modelo personalizado alterado
Ao editar o registo nos computadores a executar o Office 2016, Office 2013 ou de partilha Rights Management (RMS) aplicações para Windows, pode alterar o agendamento automático para que os modelos alterados são atualizados em computadores com mais frequência do que o respetivo valor predefinido. Pode também forçar uma atualização imediata, eliminando os dados existentes um valor de registo.

> [!WARNING]
> Se a utilização incorreta do Editor de registo poderá causar problemas graves que obriguem à reinstalação do sistema operativo. A Microsoft não garante que consiga resolver os problemas resultantes da utilização incorreta do Editor de registo. Utilize o Editor de registo por sua própria conta e risco.

##### Para alterar o agendamento automático

1.  Utilizando um editor de registo, criar e definir um dos seguintes valores de registo:

    -   Para definir uma frequência de atualização em dias (mínimo de 1 dia):  Crie um novo valor de registo com o nome **TemplateUpdateFrequency** e definir um valor inteiro para os dados, que especifica a frequência em dias para transferir alterações a um modelo transferido. Utilize a tabela seguinte para localizar o caminho do registo para criar este novo valor de registo.

        |Caminho do registo|Tipo|Valor|
        |----------------------|--------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   Para definir uma frequência de atualização em segundos (mínimo de 1 segundo):  Crie um novo valor de registo com o nome **TemplateUpdateFrequencyInSeconds** e definir um valor inteiro para os dados, que especifica a frequência em segundos para transferir alterações a um modelo transferido. Utilize a tabela seguinte para localizar o caminho do registo para criar este novo valor de registo.

        |Caminho do registo|Tipo|Valor|
        |----------------------|--------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Certifique-se de que pode cria e configurar um destes valores de registo, não ambos. Se ambos estiverem presentes, **TemplateUpdateFrequency** é ignorada.

2.  Se pretender forçar uma atualização imediata dos modelos, avance para o procedimento seguinte. Caso contrário, reinicie as suas aplicações do Office e instâncias do Explorador de ficheiros agora.

##### Para forçar uma atualização imediata

1.  Utilizando um editor de registo, eliminar os dados para o **LastUpdatedTime** valor. Por exemplo, poderão apresentar os dados **2015-04-20T15:52**; eliminar 2015-04-20T15:52 para que os dados não são apresentados. Utilize a tabela seguinte para localizar o caminho do registo para eliminar estes dados de valor de registo.

    |Caminho do registo|Tipo|Valor|
    |----------------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; MicrosoftRMS_FQDN &gt; \Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > No caminho de registo, *&lt; MicrosoftRMS_FQDN &gt;* refere-se ao seu FQDN de serviço do Microsoft RMS. Se pretender verificar este valor:
    > 
    > 1.  Executar o [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet para o Azure RMS. Se ainda não o tenha já instalado o módulo Windows PowerShell para o Azure RMS, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  A partir da saída, identificar a **LicensingIntranetDistributionPointUrl** valor.
    > 
    >     Por exemplo: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  O valor, remover **https://** e **/_wmcs/licenciamento** desta cadeia. O valor restante é o seu FQDN de serviço do Microsoft RMS. No nosso exemplo, o FQDN de serviço do Microsoft RMS seria o seguinte valor:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Elimine a pasta seguinte e todos os ficheiros que contém: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Reinicie as suas aplicações do Office e instâncias do Explorador de ficheiros.

### <a name="BKMK_Office2010ForceUpdate"></a>Apenas para o Office 2010: Como forçar uma atualização para um modelo personalizado alterado
Ao editar o registo nos computadores a executar o Office 2010, pode definir um valor para que os modelos alterados são atualizados em computadores sem aguardar por utilizadores terminar a sessão e uma segurança. Pode também forçar uma atualização imediata, eliminando os dados existentes um valor de registo.

> [!WARNING]
> Se a utilização incorreta do Editor de registo poderá causar problemas graves que obriguem à reinstalação do sistema operativo. A Microsoft não garante que consiga resolver os problemas resultantes da utilização incorreta do Editor de registo. Utilize o Editor de registo por sua própria conta e risco.

##### Para alterar a frequência de atualização

1.  Utilizando um editor de registo, crie um novo valor de registo com o nome **UpdateFrequency** e definir um valor inteiro para os dados, que especifica a frequência em dias para transferir alterações a um modelo transferido. Utilize a tabela seguinte para localizar o caminho do registo para criar este novo valor de registo.

    |Caminho do registo|Tipo|Valor|
    |----------------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Se pretender forçar uma atualização imediata dos modelos, avance para o procedimento seguinte. Caso contrário, reinicie as aplicações do Office agora.

##### Para forçar uma atualização imediata

1.  Utilizando um editor de registo, eliminar os dados para o **LastUpdatedTime** valor. Por exemplo, poderão apresentar os dados **2015-04-20T15:52**; eliminar 2015-04-20T15:52 para que os dados não são apresentados. Utilize a tabela seguinte para localizar o caminho do registo para eliminar estes dados de valor de registo.

    |Caminho do registo|Tipo|Valor|
    |----------------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  Elimine a pasta seguinte e todos os ficheiros que contém: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Reinicie as aplicações do Office.

## <a name="BKMK_PowerShellTemplates"></a>Referência do Windows PowerShell
Tudo o que pode fazer no Portal de gestão do Azure para criar e gerir modelos, que pode fazer a partir da linha de comandos, utilizando o Windows PowerShell. Além disso, pode exportar e importar modelos, para que possa copiar modelos entre inquilinos ou efetuar edições em massa de propriedades complexas nos modelos, tais como nomes multilingues e descrições.

Pode também utilizar exportar e importar uma cópia de segurança e restaurar os modelos personalizados, como melhor prática, regularmente uma cópia de segurança seus modelos personalizados, para que se fizer uma alteração que não era destinada, pode facilmente reverter para uma versão anterior.

> [!IMPORTANT]
> Para utilizar o Windows PowerShell para criar e gerir modelos de política de direitos do Azure RMS, tem de ter, pelo menos, versão 2.0.0.0 do [módulo do Windows PowerShell para o Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Se tiver instalado anteriormente este módulo do Windows PowerShell, execute o seguinte comando numa janela do PowerShell para verificar o número da versão: `(Get-Module aadrm -ListAvailable).Version`

Para instruções de instalação, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Os cmdlets que suporta a criação e gestão de modelos:

-   [AadrmTemplate adicionar](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Exportação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Importar AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [Novo AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remover AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Conjunto AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Próximos passos
Após configurar a modelos personalizados para o Azure Rights Management, utilize o [Plano de implementação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para verificar se existem outros passos de configuração que pode querer fazer antes de ser realizadas [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para utilizadores e administradores. Se não existirem sem outros passos de configuração que precisa de fazer, consulte o artigo [Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) para obter orientações sobre operacional suportar uma implementação efetuada com êxito para a sua organização.

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

