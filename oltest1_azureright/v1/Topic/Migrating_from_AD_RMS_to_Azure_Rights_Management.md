---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migrar do AD RMS para o Azure Rights Management
Utilize o seguinte conjunto de instruções para migrar a implementação do Active Directory Rights Management Services (AD RMS) para o Azure Rights Management (RMS do Azure). Após a migração, os utilizadores continuará a ter acesso a documentos e mensagens de correio eletrónico que a sua organização protegidos utilizando o AD RMS e recentemente protegeu o conteúdo irão utilizar o Azure RMS.

Não tem a certeza se esta migração de AD RMS é mais adequada para a sua organização?

-   Para uma introdução ao Azure RMS, os que pode resolver problemas de empresas, o que parece para administradores e utilizadores, e como funciona, consulte [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Para uma comparação do Azure RMS com o AD RMS, consulte o artigo [Comparar o Azure Rights Management e o AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Pré-requisitos para migrar AD RMS para o Azure RMS
Antes de iniciar a migração para o Azure RMS, certifique-se de que os seguintes pré-requisitos estão assegurados e de que compreende quaisquer limitações.

|Requisito|Obter mais informações|
|-------------|--------------------------|
|Uma implementação de RMS suportado|Todas as versões do AD RMS a partir do Windows Server 2008 através do Windows Server 2012 R2 suportam uma migração para o Azure RMS:<br /><br />-   Windows Server 2008 (x86 ou x64)<br />-   Windows Server 2008 R2 (x64)<br />-   Windows Server 2012 (x64)<br />-   Windows Server 2012 R2 (x64) **Note:** Se estiver a executar o Windows RMS no Windows Server 2003, esta versão do sistema operativo será fora do suporte durante 2015. Pode migrar nesta versão do RMS para o Azure RMS, mas este processo é suportado apenas se o sistema operativo ainda é suportado. Como solução, pode importar o seu domínio de publicação fidedigno (TPD) para uma versão do AD RMS, que é suportado e, em seguida, volte a importar TPD sem a opção de compatibilidade do RMS 1.0. Para mais informações sobre TPDs, consulte o artigo [domínio de publicação fidedigno](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Todas as topologias de AD RMS válidas são suportadas:<br /><br />-   Única floresta, a única origem de cluster do RMS<br />-   Floresta única, vários clusters de RMS de só de licenciamento<br />-   Várias florestas, vários clusters de RMS **Note:** Por predefinição, vários clusters de RMS migram para um único inquilino do Azure RMS. Se pretender que os inquilinos de RMS diferentes, tem de os trate como migrações diferentes. Uma chave de um cluster do RMS não é possível importar mais do que um inquilino do Azure RMS.|
|Todos os requisitos para executar o Azure RMS, incluindo um inquilino do Azure RMS (não ativado)|Consulte o artigo [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Embora tem de ter um inquilino do Azure RMS para poder migrar a partir do AD RMS, recomendamos que não ativar o serviço de gestão de direitos antes da migração. O processo de migração inclui este passo, depois de ter exportado chaves e modelos a partir do AD RMS e importado-los para o Azure RMS. No entanto, se o Azure RMS já estiver ativado, pode ainda migrar a partir do AD RMS.|
|Preparação para o Azure RMS:<br /><br />-   Sincronização de diretórios entre o seu diretório no local e o Azure Active Directory<br />-   Grupos com capacidade de correio no Azure Active Directory|Consulte o artigo [Preparar para o Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Se tiver utilizado a funcionalidade de gestão de direitos de informação (IRM) do Exchange Server (por exemplo, regras de transporte e Outlook Web Access) ou no SharePoint Server com o AD RMS:<br /><br />-   Planear um curto período de tempo quando a IRM não estará disponível nestes servidores|Pode continuar a utilizar a IRM nestes servidores com o Azure RMS após a migração. No entanto, um dos passos de migração é desativar temporariamente o serviço de IRM, instalar e configurar um conector, reconfigurar os servidores e, em seguida, volte a ativar a IRM.<br /><br />Esta é a única interrupções no serviço durante o processo de migração.|
Limitações:

-   Apesar do processo de migração permite migrar o seu servidor de licenciamento de chave do certificado (SLC) a um módulo de segurança de hardware (HSM) para o Azure RMS, Exchange Online não suporta atualmente esta configuração. Se pretender que todas funcionalidades IRM com o Exchange Online após a migração para o Azure RMS, a chave de inquilino do Azure RMS tem de ser [geridos pelo Microsoft](http://technet.microsoft.com/library/dn440580.aspx). Em alternativa, pode executar IRM com funcionalidade reduzida no Exchange Online quando o inquilino do Azure RMS é gerido por si (BYOK). Para obter mais informações sobre como utilizar o Exchange Online com o Azure RMS, consulte o artigo [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) nestas instruções.

-   Se tiver o software e os clientes que não são suportados com o Azure RMS, irá não poderão proteger ou consumir conteúdo que seja protegido pelo Azure RMS. Não se esqueça de verificar as aplicações suportadas e os clientes secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico.

-   Se importar a chave no local para Azure RMS como arquivados (não definido TPD para ser o ativo durante o processo de importação) e migrar utilizadores em lotes de uma migração faseada, o conteúdo que é protegido recentemente pelos utilizadores migrados não serão acessível aos utilizadores que permanecem no AD RMS. Neste cenário, sempre que possível, mantenha o tempo de migração curto e migrar utilizadores em lotes de lógicas de forma a que se possam colaborar entre si, são migrados em conjunto.

    Esta limitação não se aplica ao definir o TPD ao Active Directory durante o processo de importação, porque todos os utilizadores irão proteger conteúdo utilizando a mesma chave. Recomendamos esta configuração porque lhe permite migrar todos os utilizadores de forma independente e ao seu ritmo.

-   Se lhe colaborar com parceiros externos (por exemplo, através da utilização de domínios de utilizadores fidedignos ou Federação), também deve migrar para o Azure RMS ou ao mesmo tempo como a migração ou logo que seja possível posteriormente. Para continuar a aceder ao conteúdo de que a organização anteriormente protegida utilizando o AD RMS, do mesmo têm tomar cliente alterações de configuração que são semelhantes às que fizer e incluídos neste documento.

    Devido às variações de configuração possíveis que possam ter os parceiros, instruções exatas para este reconfiguração estão fora do âmbito deste documento. Para obter ajuda, contacte o Microsoft suporte ao cliente (CSS).

## Passos para migrar AD RMS para o Azure RMS

|Passo de migração|Obter mais informações|
|---------------------|--------------------------|
|**1. Transfira as ferramentas de administração de gestão do Azure RMS**|Para obter instruções, consulte o artigo [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Exportar dados de configuração a partir de AD RMS e importá-lo para o Azure RMS**|Exportar os dados de configuração (chaves, modelos, os URLs) a partir do AD RMS para um ficheiro XML e, em seguida, carregar esse ficheiro para o Azure RMS utilizando o cmdlet Import-AadrmTpd Windows PowerShell. Poderão ser necessário passos adicionais, consoante a configuração de chave do AD RMS em:<br /><br />-   Chave protegidos por software para a migração chave protegidos por software: Chaves geridas centralmente, baseado em palavra-passe do AD RMS a chave de inquilino geridos pelo Microsoft Azure RMS. Este é o caminho de migração mais simples e não existem passos adicionais são necessários.<br />-   Chave HSM protegidas para migração chave HSM protegidas: Chaves de que são armazenadas por um HSM de AD RMS a chave de inquilino do Azure RMS geridos pelo cliente (a "colocar o seu próprio chave" ou cenário BYOK). Isto requer que os passos adicionais para transferir a chave a partir do seu HSM de Thales no local para o HSM de RMS do Azure.<br />-   Chave protegidos por software para a migração chave HSM protegidas: Geridas centralmente, chaves baseado em palavra-passe do AD RMS a chave de inquilino do Azure RMS geridos pelo cliente (a "colocar o seu próprio chave" ou cenário BYOK). Isto requer que a configuração de maioria dos porque tem de primeiro extrair a chave de software e importá-lo para um HSM no local e, em seguida, efetue os passos adicionais para transferir a chave a partir do seu HSM de Thales no local para o HSM de RMS do Azure.<br /><br />Para obter instruções, consulte o artigo [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Ativar o seu inquilino do RMS**|Se possível, execute este passo depois do processo de importação e não antes.<br /><br />Para mais informações e instruções, consulte o artigo [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Configurar modelos importados**|Ao importar os modelos de política de direitos, o respetivo estado é arquivado. Se pretender que os utilizadores possam ver e utilizá-los, tem de alterar o estado de modelo publicados no portal do Azure clássico.<br /><br />Para obter instruções, consulte o artigo [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Reconfigure os clientes utilizam o Azure RMS**|Computadores existentes do Windows tem de ser reconfigurados para utilizar o serviço do Azure RMS em vez de AD RMS. Este passo aplica-se a computadores na sua organização e para computadores em organizações parceiras se tiver colaborado com os mesmos enquanto despendiam a executar o AD RMS.<br /><br />Além disso, se tiver implementado o [extensões de dispositivo móvel](http://technet.microsoft.com/library/dn673574.aspx) para suportar dispositivos móveis, como o iOS telefones e iPads, telemóveis Android e tablets, Windows phone e computadores Mac, tem de remover os registos SRV no DNS que esses clientes para utilizar o AD RMS e/s redirecionada.<br /><br />Para obter instruções, consulte o artigo [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Configurar a integração de IRM com o Exchange Online**|Este passo é necessário se pretender utilizar o Exchange Online com o Azure RMS.<br /><br />Para obter instruções, consulte o artigo [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Implementar o conector do RMS**|Este passo é necessário se pretender utilizar qualquer um dos seguintes serviços no local com o Azure RMS:<br /><br />-   Exchange Server (por exemplo, regras de transporte e Outlook Web Access)<br />-   Servidor do SharePoint<br />-   Windows Server que executa a infraestrutura de classificação de ficheiros<br /><br />Para obter instruções, consulte o artigo [Step 7. Deploy the RMS connector](#BKMK_Step7Migration).|
|**8. Encerrar o AD RMS**|Quando tiver confirmado que todos os clientes estão a utilizar o Azure RMS e já não aceder aos servidores do AD RMS, pode desativar a implementação do AD RMS.<br /><br />Para obter instruções, consulte o artigo [Step 8. Decommission AD RMS](#BKMK_Step8Migration).|
|**9. Chave novamente a chave de inquilino do Azure RMS**|Este passo é necessário se foram não está em execução no modo criptográfico 2 antes da migração e opcional mas recomendada para todas as migrações para o ajudar a salvaguarde a segurança da sua chave de inquilino do Azure RMS.<br /><br />Para obter instruções, consulte o artigo [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Passo 1: Transfira a ferramenta de administração do Azure Rights Management
Ir para o Center Download Microsoft e transferir o [ferramenta de administração do Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721), que contém o módulo de administração do Azure RMS para o Windows PowerShell.

### <a name="BKMK_Step2Migration"></a>Passo 2. Exportar dados de configuração a partir de AD RMS e importá-lo para o Azure RMS
Este passo é um processo de duas partes:

1.  Exporte os dados de configuração de AD RMS exportando os domínios de publicação fidedignos (TPDs) para um ficheiro. XML. Este processo é o mesmo para todas as migrações.

2.  Importe os dados de configuração para o Azure RMS. Existem diferentes processos para este passo, consoante a configuração de implementação atual do AD RMS e a topologia preferida para a sua chave de inquilino do Azure RMS.

#### Exporte os dados de configuração de AD RMS
Faça o seguinte procedimento em todos os clusters de AD RMS, para todos os domínios de publicação fidedignos que protegidos conteúdo para a sua organização. Não é necessário executar esta em clusters de só de licenciamento.

> [!NOTE]
> Se estiver a utilizar gestão de direitos do Windows Server 2003, em vez destas instruções, siga o procedimento [SLC exportar, TUD, TPD e RMS chave privada](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) a partir de [Migrar do Windows RMS para o AD RMS numa infraestrutura de diferentes](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) tópico.

###### Para exportar os dados de configuração (fidedignidade publicação de informações de domínio)

1.  Inicie sessão no cluster do AD RMS como um utilizador com o AD RMS permissões de administração.

2.  A partir da consola de gestão do AD RMS (**Serviços de gestão de direitos do Active Directory**), expanda o nome de cluster do AD RMS, expanda **Confiar políticas**, e, em seguida, clique em **domínios publicação fidedignos**.

3.  No painel de resultados, selecione o domínio de publicação fidedigno e, em seguida, a partir do painel ações, clique em **Exportar domínio de publicação fidedigno**.

4.  No **Exportar publicação domínio fidedigno** caixa de diálogo:

    -   Clique em **Guardar como** e guardar no caminho e um nome de ficheiro à sua escolha. Certifique-se especificar **.xml** como a extensão de nome de ficheiro (isto não é acrescentado automaticamente).

    -   Especifique e confirme uma palavra-passe. Lembre-se esta palavra-passe, porque irá precisar dele mais tarde, quando importa os dados de configuração para o Azure RMS.

    -   Não selecione a caixa de verificação para guardar o ficheiro de domínio fidedigno na RMS versão 1.0.

Quando exportou todos os domínios de publicação fidedignos, está pronto para iniciar o procedimento para importar dados para o Azure RMS.

#### Importar os dados de configuração para o Azure RMS
Os procedimentos exatos para este passo dependem da configuração de implementação atual do AD RMS e a topologia preferida para a sua chave de inquilino do Azure RMS.

A implementação do AD RMS atual irá utilizar uma das seguintes configurações para a sua chave de certificado (SLC) de licenciante servidor:

-   Proteção de palavra-passe na base de dados do AD RMS. Esta é a configuração predefinida.

-   Proteção de HSM através da utilização de um módulo de segurança de hardware Thales (HSM).

-   Proteção de HSM através da utilização de um módulo de segurança de hardware (HSM) a partir de um fornecedor diferente Thales.

-   Palavra-passe protegido através da utilização de um fornecedor de criptografia externo.

> [!NOTE]
> Para obter mais informações sobre a utilização de módulos de segurança do hardware com o AD RMS, consulte o artigo [utilizando o AD RMS com módulos de segurança de Hardware](http://technet.microsoft.com/library/jj651024.aspx).

As duas opções de topologia chaves de inquilino do Azure RMS são: Microsoft gere a sua chave de inquilino (**gerido por Microsoft**) ou que gere a sua chave de inquilino (**geridos pelo cliente**). Quando gere a sua própria chave de inquilino do Azure RMS, é por vezes referida como "bring a sua própria chave" (BYOK) e necessita de um módulo de segurança de hardware (HSM) a partir do Thales. Para obter mais informações, consulte o [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico.

> [!IMPORTANT]
> Exchange Online não é atualmente compatível com o Azure RMS BYOK.  Se pretender utilizar BYOK após a migração e planeie a utilizar o Exchange Online, certifique-se de que compreende como esta configuração reduz a funcionalidade IRM para o Exchange Online. Reveja as informações no [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) secção a  [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico para ajudar a escolher a melhor Azure RMS inquilino topologia chave para a sua migração.

Utilize a tabela seguinte para identificar o procedimento a utilizar para a migração. Não são suportadas as combinações que não estão listadas.

|Implementação atual do AD RMS|Topologia de chave de inquilino escolhida Azure RMS|Instruções de migração|
|---------------------------------|-------------------------------------------------------|--------------------------|
|Proteção de palavra-passe na base de dados do AD RMS|Gerido por Microsoft|Consulte o **protegidos por Software chave para a migração chave protegidos por software** procedimento após esta tabela.<br /><br />Este é o caminho de migração mais simples e requer apenas que transfere os dados de configuração para o Azure RMS.|
|Proteção de HSM através da utilização de um módulo de segurança de hardware de nShield Thales (HSM)|Cliente gerido (BYOK)|Consulte o **chave HSM protegidas para migração chave HSM protegidas** procedimento após esta tabela.<br /><br />Isto requer que o conjunto de ferramentas BYOK e dois conjunto de passos para transferir a chave a partir do seu HSM no local para o HSMs de RMS do Azure e, em seguida, transfere os dados de configuração para o Azure RMS.|
|Proteção de palavra-passe na base de dados do AD RMS|Cliente gerido (BYOK)|Consulte o **protegidos por Software chave para a migração chave HSM protegidas** procedimento após esta tabela.<br /><br />Isto requer que o conjunto de ferramentas BYOK e três conjuntos de passos primeiro para extrair a sua chave de software e importe-o para uma HSM no local, em seguida, transferir a chave a partir do seu HSM no local para o HSMs de RMS do Azure e, finalmente transferir os dados de configuração para o Azure RMS.|
|Proteção de HSM através da utilização de um módulo de segurança de hardware (HSM) a partir de um fornecedor diferente Thales|Cliente gerido (BYOK)|Contacte o fornecedor para si HSM para obter instruções como transferir a chave a partir deste HSM para um nShield Thales módulo de segurança de Hardware (HSM). Em seguida, siga as instruções para o **chave HSM protegidas para migração chave HSM protegidas** procedimento após esta tabela.|
|Palavra-passe protegido através da utilização de um fornecedor de criptografia externo|Cliente gerido (BYOK)|Contacte o fornecedor para o fornecedor de criptografia para obter instruções de como transferir a chave para um módulo de segurança de hardware de nShield Thales (HSM). Em seguida, siga as instruções para o **chave HSM protegidas para migração chave HSM protegidas** procedimento após esta tabela.|
Antes de iniciar estes procedimentos, certifique-se de que pode aceder os ficheiros. XML que criou anteriormente quando que exportou os domínios de publicação fidedignos. Por exemplo, estas poderão ser guardadas para uma pen USB que movem a partir do servidor do AD RMS para a estação de trabalho ligado à Internet.

> [!NOTE]
> No entanto, pode armazena estes ficheiros, utilize recomendados de segurança para protegê-las uma vez que estes dados incluem a chave privada.

##### Chave protegidos por software protegidos por software chave migração
Utilize este procedimento para importar a configuração de AD RMS para o Azure RMS, resultará na sua chave de inquilino do Azure RMS que é gerido pelo Microsoft.

###### Para importar os dados de configuração para o Azure RMS

1.  Numa estação de trabalho ligado à Internet, transfira e instale o módulo Windows PowerShell para o Azure RMS (versão mínima 2.1.0.0), que inclui o [importação AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) cmdlet.

    > [!TIP]
    > Se anteriormente tiver transferido e instalado o módulo, verifique o número da versão executando: `(Get-Module aadrm -ListAvailable).Version`

    Para instruções de instalação, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Inicie o Windows PowerShell com o **Executar como administrador** opção e utilizar o [Ligar AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) cmdlet para ligar ao serviço do Azure RMS:

    ```
    Connect-AadrmService
    ```
    Quando lhe for pedido, introduza o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] credenciais de administrador de inquilinos (normalmente, utilizará uma conta que seja um administrador global do Azure Active Directory ou do Office 365).

3.  Utilize o [importação AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) exportados de cmdlet para carregar o primeiro ficheiro de domínio (. xml) de publicação fidedigno. Se tiver mais do que um ficheiro. XML porque tinha vários domínios de publicação fidedignos, selecione o ficheiro que contém o exportado domínio de publicação fidedigno que pretende utilizar no Azure RMS para proteger conteúdo após a migração. Utilize o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Quando lhe for pedido, introduza a palavra-passe que especificou anteriormente e confirme que pretende efetuar esta ação.

4.  Quando o comando for concluído, repita o passo 3 para cada ficheiro. XML restantes que criou exportando os domínios de publicação fidedignos. Mas para esses ficheiros, definir **-Active** para **false** ao executar o comando de importação. Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Utilize o [Desligar AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) cmdlet para desligar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora está pronto para ir para [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Chave HSM protegidas migração chave HSM protegidas
É um procedimento de duas partes para importar a chave HSM e a configuração de AD RMS para o Azure RMS, resultará na sua chave de inquilino do Azure RMS que é gerido por si (BYOK).

A chave HSM primeiro tem de empacotar para que fique pronto para transferir para o Azure RMS e, em seguida, importá-lo com os dados de configuração.

###### Parte 1: A chave HSM do pacote para que fique pronto para transferir para o Azure RMS

1.  Siga os passos a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), utilizando o procedimento **gerar e transfira o inquilino chave – através da Internet** com as seguintes exceções:

    -   Não siga os passos para **gerar a chave de inquilino**, porque já tem o equivalente a partir da sua implementação do AD RMS. Tem de identificar a chave utilizada pelo seu servidor AD RMS da instalação Thales e utilizar esta chave durante a migração. Thales chaves de ficheiros encriptados, normalmente, são denominados **key_(keyAppName)_(keyIdentifier)** localmente no servidor.

    -   Não siga os passos para **Transferir a chave de inquilino para o Azure RMS**, que utiliza o comando Adicionar AadrmKey.  Em vez disso, irá transferir a chave HSM preparada ao carregar o seu domínio de publicação fidedigno exportado, utilizando o comando de importação AadrmTpd.

2.  Na estação de trabalho ligado à Internet, numa sessão do Windows PowerShell, voltar a ligar ao serviço do Azure RMS.

Agora que já preparado a chave HSM para o Azure RMS, está pronto para importar o ficheiro da chave HSM e dados de configuração de AD RMS.

###### Parte 2: Importar os dados de configuração e a chave HSM para o Azure RMS

1.  Continua na estação de trabalho ligar de Internet e na sessão do Windows PowerShell, carregar o primeiro fidedigna publicação domínio (. xml) ficheiro exportado. Se tiver mais do que um ficheiro. XML porque tinha vários domínios de publicação fidedignos, selecione o ficheiro que contém o exportado domínio de publicação fidedigno que corresponde à chave HSM que pretende utilizar no Azure RMS para proteger conteúdo após a migração. Utilize o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Por exemplo: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Quando lhe for pedido, introduza a palavra-passe que especificou anteriormente e confirme que pretende efetuar esta ação.

2.  Quando o comando for concluído, repita o passo 1 para cada ficheiro. XML restantes que criou exportando os domínios de publicação fidedignos. Mas para esses ficheiros, definir **-Active** para **false** ao executar o comando de importação.  Por exemplo: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Utilize o [Desligar AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet para desligar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora está pronto para ir para [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Chave protegidos por software migração chave HSM protegidas
É um procedimento de três partes para importar a configuração de AD RMS para o Azure RMS, resultará na sua chave de inquilino do Azure RMS que é gerido por si (BYOK).

Deve primeiro extrair a chave de certificado (SLC) do servidor licenciante dos dados de configuração e transferir a chave para HSM um Thales no local, em seguida, o pacote e transferir a chave HSM para o Azure RMS e, em seguida, importar os dados de configuração.

###### Parte 1: Extrair o SLC dos dados de configuração e importar a chave para sua HSM no local

1.  Utilize os seguintes passos de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico:

    -   **Gerar e transfira o inquilino chave – através da Internet**: **Preparar a estação de trabalho ligado à Internet**

    -   **Gerar e transfira o inquilino chave – através da Internet**: **Preparar a estação de trabalho desligada**

    Não siga os passos para gerar a chave de inquilino, porque já tem o equivalente no ficheiro de dados (. xml) de configuração exportado. Em vez disso, será executado um comando para extrair esta chave a partir do ficheiro e importá-lo para o seu HSM no local.

2.  Na estação de trabalho desligada, execute o seguinte comando:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Por exemplo, para a América do Norte: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Informações adicionais:

    -   O parâmetro ImportRmsCentrallyManagedKey indica que a operação está a importar a chave SLC.

    -   Se não especificar a palavra-passe no comando, será pedido para especificá-la.

    -   O parâmetro KeyIdentifier destina-se um nome amigável da chave que cria o nome do ficheiro de chave. Tem de utilizar apenas, minúsculas carateres ASCII.

    -   O parâmetro ExchangeKeyPackage Especifica um pacote de chave (KEK) de troca de chaves específicos da região que tem um início de nome com BYOK-KEK - pkg-.

    -   O parâmetro NewSecurityWorldPackage Especifica um pacote de mundo de segurança específicos da região que tem um início de nome com BYOK-SecurityWorld - pkg-.

    Este comando resulta no seguinte:

    -   Um ficheiro de chave HSM: %NFAST_KMDATA%\local\key_mscapi_ &lt; KeyID &gt;

    -   Ficheiro de dados de configuração de RMS com o SLC removidos: %NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt;. XML devolvido por

3.  Se tiver mais do que um ficheiros de dados de configuração de RMS, repita o passo 2 para o resto destes ficheiros.

Agora que o seu SLC tem foram extraído para que seja uma chave com base em HSM, está pronto para o pacote e transferi-lo para o Azure RMS.

###### Parte 2: O pacote e transferir a chave HSM para o Azure RMS

1.  Utilize os passos seguintes a partir de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Gerar e transfira o inquilino chave – através da Internet**: **Preparar a sua chave de inquilino para transferência**

    -   **Gerar e transfira o inquilino chave – através da Internet**: **Transferir a chave de inquilino para o Azure RMS**

Agora que tenha transferido a chave HSM para Azure RMS, está pronto para importar os dados de configuração de AD RMS, que contém apenas um ponteiro para a chave de inquilino transferidos recentemente.

###### Parte 3: Importar os dados de configuração para o Azure RMS

1.  Ainda na estação de trabalho ligado à Internet e na sessão do Windows PowerShell, copie os ficheiros de configuração do RMS com SLC removido (a desligado estação de trabalho,. XML %NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt;)

2.  Carregar o ficheiro primeiro. Se tiver mais do que um ficheiro. XML porque tinha vários domínios de publicação fidedignos, selecione o ficheiro que contém o exportado domínio de publicação fidedigno que corresponde à chave HSM que pretende utilizar no Azure RMS para proteger conteúdo após a migração. Utilize o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Por exemplo: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Quando lhe for pedido, introduza a palavra-passe que especificou anteriormente e confirme que pretende efetuar esta ação.

3.  Quando o comando for concluído, repita o passo 2 para cada ficheiro. XML restantes que criou exportando os domínios de publicação fidedignos. Mas para esses ficheiros, definir **-Active** para **false** ao executar o comando de importação. Por exemplo: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Utilize o [Desligar AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet para desligar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora está pronto para ir para [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Passo 3. Ativar o seu inquilino do RMS
Instruções para este passo totalmente descritas a [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tópico.

> [!TIP]
> Se tiver uma subscrição do Office 365, pode ativar o Azure RMS a partir do Centro de administração do Office 365 ou o portal do Azure clássico. Recomendamos que utilize o portal do Azure clássico dado que irá utilizar este portal de gestão para concluir o passo seguinte.

**E se o seu inquilino do Azure RMS já foi ativado?** Se o serviço do Azure RMS já se encontra ativado para a sua organização, os utilizadores poderão já utilizou Azure RMS para proteger conteúdo com uma chave de inquilino gerada automaticamente (e os modelos predefinidos) em vez das chaves existentes (e modelos) a partir do AD RMS. Este é pouco provável ocorrer em computadores que estão bem geridas na sua intranet, porque estas serão automaticamente configuradas para a sua infraestrutura de AD RMS. Mas pode acontecer nos computadores de grupo de trabalho ou computadores que raramente à sua intranet. Infelizmente, também é difíceis de identificar estes computadores, que é a razão pela qual é recomendável que não ativar o serviço antes de importar os dados de configuração de AD RMS.

Se o seu inquilino do Azure RMS já se encontra ativado e pode identificar estes computadores, certifique-se de que executa o script de CleanUpRMS_RUN_Elevated.cmd nestes computadores, conforme descrito no passo 5. A execução deste script força-los ao reinicializar o ambiente do utilizador, para que possam transferiram a chave de inquilino atualizada e modelos importados.

### <a name="BKMK_Step4Migration"></a>Passo 4. Configurar modelos importados
Uma vez que os modelos que importou tem um estado predefinido do **Archived**, tem de alterar este estado é **publicada** se pretender que os utilizadores possam utilizar estes modelos com o Azure RMS.

Além disso, se os modelos no AD RMS utilizado o **ANYONE** grupo, este grupo é removido automaticamente quando importa os modelos para o Azure RMS; tem de adicionar manualmente o grupo equivalente ou utilizadores e os direitos mesmos para os modelos importados. O grupo equivalente para o Azure RMS é designado **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Por exemplo, este grupo poderá ser semelhante às seguintes opções para Contoso: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Se não tiver a certeza se os modelos de AD RMS incluem a qualquer pessoa grupo, expanda o  [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) secção este passo para copiar e utilizar o script do PowerShell de exemplo para identificar estes modelos. Para obter mais informações sobre como utilizar o Windows PowerShell com o AD RMS, consulte o artigo  [através do Windows PowerShell para administrar o AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Pode ver a sua organização do criado automaticamente o grupo se que copie um dos modelos de política de direitos predefinidos no portal do Azure clássico e, em seguida, identifique o **nome de utilizador** no **direitos** página. No entanto, não é possível utilizar o portal de clássico para adicionar este grupo a um modelo que criou ou importou manualmente e em vez disso, tem de utilizar uma das seguintes opções do PowerShell do Azure RMS:

-   Utilize o [Novo AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet PowerShell para definir o grupo de "AllStaff" e direitos como um objeto de definição de direitos e execute este comando novamente para cada um dos outros grupos ou utilizadores já concedidos direitos no modelo original, além do grupo de ANYONE. Em seguida, adicione todos os objetos de definição estes direitos para os modelos utilizando o  [conjunto AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) cmdlet.

-   Utilize o [exportação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet para exportar o modelo a um. Ficheiro XML que pode editar para adicionar o grupo de "AllStaff" e direitos sobre os grupos existentes e os direitos e, em seguida, utilize o [importação AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) cmdlet para importar esta alteração de volta para o Azure RMS.

> [!NOTE]
> Este grupo equivalente "AllStaff" não é exatamente o mesmo que o grupo ANYONE no AD RMS:  O grupo de "AllStaff" inclui todos os utilizadores no seu inquilino do Azure, enquanto que o grupo de todas as pessoas inclui todos os utilizadores autenticados, que podem ser fora da sua organização.
> 
> Devido a esta diferença entre os dois grupos, poderá ter de também adicionar utilizadores externos para além do grupo de "AllStaff". Endereços de e-mail externo de grupos não são atualmente suportados.

Os modelos que importar a partir de AD RMS aspeto e assemelham-se apenas às modelos personalizados que pode criar no portal do Azure clássico. Para alterar importados modelos para ser publicado para que os utilizadores possam vê-los e selecione-os partir de aplicações ou para efetuar outras alterações aos modelos, consulte o artigo [Configurar modelos personalizados para o Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Para uma experiência mais consistente para utilizadores durante o processo de migração, não faça alterações aos modelos de importados que não seja estas alterações de dois; e não publicar modelos dois predefinidos que vêm com o Azure RMS, ou criar novos modelos neste momento. Em vez disso, aguarde até que o processo de migração está concluído e tem de encerrar os servidores AD RMS.

#### <a name="BKMK_ScriptForANYONE"></a>Script de exemplo do Windows PowerShell para identificar os modelos de AD RMS que incluem o grupo ANYONE
Esta secção contém o script de exemplo para o ajudar a identificar os modelos de AD RMS que tenham o grupo ANYONE definido, conforme descrito na secção anterior.

*&#42;&#42;Exclusão de responsabilidade:&#42;&#42; Este script de exemplo não é suportado em qualquer serviço ou programa de suporte padrão da Microsoft. Este script de exemplo é fornecido como é, sem garantias de qualquer tipo.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>Passo 5. Reconfigure os clientes utilizam o Azure RMS
Para clientes do Windows:

1.  [Transferir os scripts de migração](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Estes scripts reposição da configuração em computadores Windows, para que utilizará o serviço do Azure RMS em vez de AD RMS.

2.  Siga as instruções no script de redirecionamento (Redirect_OnPrem.cmd) para modificar o script para apontar para o novo inquilino do Azure RMS.

3.  Em computadores Windows, execute estes scripts com privilégios elevados no contexto do utilizador.

Para clientes de dispositivos móveis e computadores Mac:

-   Remover os registos SRV de DNS que criou quando implementou o [extensão de dispositivo móvel do AD RMS](http://technet.microsoft.com/library/dn673574.aspx).

#### Alterações efetuadas pelos scripts de migração
Esta secção documentos as alterações que tornam os scripts de migração. Pode utilizar estas informações apenas a fins de referência ou para resolução de problemas ou, se preferir efetuar estas alterações sozinho.

CleanUpRMS_RUN_Elevated.cmd:

-   Elimine o conteúdo das pastas %userprofile%\AppData\Local\Microsoft\DRM e %userprofile%\AppData\Local\Microsoft\MSIPC, incluindo quaisquer subpastas e ficheiros com nomes de ficheiro longos.

-   Elimine o conteúdo das seguintes chaves de registo:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Elimine os seguintes valores de registo:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Crie os seguintes valores de registo para cada URL fornecido como parâmetro em cada uma das seguintes localizações:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Cada entrada tem um valor REG_SZ **https://OldRMSserverURL/_wmcs/licensing** com os dados no seguinte formato: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* tem o seguinte formato: **{GUID} .rms. [Região].aadrm.com**.
    > 
    > Por exemplo:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Pode encontrar este valor ao identificar a **RightsManagementServiceId** valor ao executar o [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet para o Azure RMS.

### <a name="BKMK_Step6Migration"></a>Passo 6. Configurar a integração de IRM para o Exchange Online
Se tiver importado anteriormente seu TDP a partir do AD RMS para o Exchange Online, tem de remover esta TDP para evitar modelos em conflito e políticas após migração para o Azure RMS. Para tal, utilize o [Remover RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) cmdlet a partir do Exchange Online.

Se optou por um Azure RMS inquilino chave topologia do **Microsoft gerido**:

-   Consulte o [Exchange Online: Configuração de IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) secção a [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) tópico. Esta secção inclui comandos típicos para executar que estabelece ligação ao serviço Exchange Online, que importa a chave de inquilino do Azure RMS e ativa a funcionalidade de IRM para o Exchange Online. Depois de concluir estes passos, terá da funcionalidade completa do RMS com o Exchange Online.

Se optou por um Azure RMS inquilino chave topologia do **cliente gerido por (BYOK)**:

-   Terá RMS funcionalidades reduzidas com o Exchange Online, como descrito a [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) secção a [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico.

### <a name="BKMK_Step7Migration"></a>Passo 7. Implementar o conector do RMS
Se tiver utilizado a funcionalidade de gestão de direitos de informação (IRM) do Exchange Server ou SharePoint Server com o AD RMS, tem de desativar IRM nestes servidores e remova a configuração de AD RMS. Em seguida, implemente o conector de gestão de direitos (RMS), que é funciona como uma interface de comunicações (um reencaminhamento) entre os servidores no local e o Azure RMS.

Por fim, para este passo, se importou TPDs várias para o Azure RMS que foram utilizadas para proteger as mensagens de correio eletrónico, tem de editar manualmente o registo nos computadores do Exchange Server para redirecionar todos os URLs de TPDs para o conector do RMS.

> [!NOTE]
> Antes de começar, verifique as versões suportadas dos servidores no local que o conector de RMS suporta "servidores a no local que suportam o Azure RMS" no [Aplicações que suportem o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico.

##### Desative a IRM em servidores do Exchange e remova a configuração de AD RMS

1.  Em cada servidor Exchange, localize a pasta seguinte e eliminar todas as entradas nessa pasta: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  A partir de um dos servidores do Exchange, utilizar o Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) cmdlet desativar primeiro IRM funcionalidades para as mensagens que são enviadas para os destinatários internos:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Em seguida, utilize o mesmo cmdlet para desativar as funcionalidades de IRM para mensagens enviadas para os destinatários externos:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Em seguida, utilize o mesmo cmdlet para desativar a IRM do Microsoft Office Outlook Web App e do Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Por fim, utilize o mesmo cmdlet para limpar todos os certificados em cache:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Em cada servidor Exchange, agora repor o IIS, por exemplo, ao executar uma linha de comandos como administrador e escrever **iisreset**.

##### Desative a IRM em servidores do SharePoint e remover a configuração de AD RMS

1.  Certifique-se de que não existem nenhuns documentos com saída dada a partir de bibliotecas protegidas por RMS. Se existirem, estes ser estarão inacessíveis no final deste procedimento.

2.  O SharePoint Web Administração Central de sites, além de **Iniciação rápida** secção, clique em **segurança**.

3.  No **segurança** página, no **política informações** secção, clique em **Configurar gestão de direitos de informação**.

4.  No **Information Rights Management** página, no **Information Rights Management** secção, selecione **não utilize IRM neste servidor**, em seguida, clique em **OK**.

5.  Em cada um dos computadores servidor do SharePoint, elimine o conteúdo da \ProgramData\Microsoft\MSIPC\Server\ a pasta*&lt; SID da conta a executar o SharePoint Server &gt;*.

##### Instalar e configurar o conector do RMS

-   Utilize as instruções no [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tópico.

##### Para o Exchange só e TPDs vários: Editar o registo

-   Em cada servidor Exchange, adicione manualmente as chaves do registo seguinte para cada TPD adicional que tiver importado, para redirecionar os URLs de TPD para o conector do RMS. Estas entradas de registo são específicas para a migração e não são adicionadas pela ferramenta de configuração de servidor para o conector do Microsoft RMS.

    Quando efetuar estas edições de registo, utilize as instruções seguintes:

    -   Substituir *ConnectorFQDN* com o nome que foi por si definido no DNS para o conector. Por exemplo, **rmsconnector.contoso.com**.

    -   Utilize o prefixo HTTP ou HTTPS para o URL de conector, dependendo se configurou o conector para utilizar HTTP ou HTTPS para comunicar com os servidores no local.

    **Para o Exchange 2013:**

    |Caminho do registo|Tipo|Valor|Dados|
    |----------------------|--------|---------|---------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;ad URL de licenciamento de Intranet do RMS &gt;/_wmcs/licenciamento|Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS a partir do seu Exchange server para o conector do RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS na Extranet licenciamento URL &gt;/_wmcs/licenciamento|Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS a partir do seu Exchange server para o conector do RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/Licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/Licensing|
    **Para o Exchange Server 2010:**

    |Caminho do registo|Tipo|Valor|Dados|
    |----------------------|--------|---------|---------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;ad URL de licenciamento de Intranet do RMS &gt;/_wmcs/licenciamento|Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS a partir do seu Exchange server para o conector do RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS na Extranet licenciamento URL &gt;/_wmcs/licenciamento|Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS a partir do seu Exchange server para o conector do RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/Licensing<br />-   https://&lt;connectorName&gt;/_wmcs/Licensing|

Depois de concluir estes procedimentos, certifique-se de que ler o **passos** secção a [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tópico.

### <a name="BKMK_Step8Migration"></a>Passo 8. Encerrar o AD RMS
Opcional: Remova o ponto de ligação de serviço (SCP) do Active Directory para impedir que computadores detetar a infraestrutura de gestão de direitos no local. Isto é opcional devido ao redirecionamento que foram configurados no registo (por exemplo, ao executar o script de migração). Para remover o ponto de ligação de serviço, utilize a ferramenta de registo de SCP do AD a partir de [Toolkit de administração de serviços de gestão de direitos](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorizar os servidores de AD RMS de atividade, por exemplo, verificando o [pedidos no relatório de estado de funcionamento do sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [ServiceRequest tabela](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou [auditoria de acesso de utilizador a protegeu o conteúdo](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Quando tiver confirmado que os clientes de RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure RMS, pode remover a função de servidor do AD RMS a partir destes servidor. Se estiver a utilizar servidores dedicados, poderá preferir que o passo cautionary da primeira encerrar os servidores para um período de tempo para se certificar de que não existem comunicados problemas que exijam reiniciar estes servidores para assegurar a continuidade do serviço enquanto estiver a investigar por que razão os clientes não utilizam o Azure RMS.

Após a desativação de servidores AD RMS, pode querer tomar a oportunidade de rever os modelos no portal do Azure clássico e consolidá-las para que os utilizadores tenham menos para escolher entre, ou reconfigure-os ou até adicionar novos modelos. É também o momento indicado para publicar modelos predefinidos. Para obter mais informações, consulte o artigo [Configurar modelos personalizados para o Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Passo 9. Chave novamente a chave de inquilino do Azure RMS
Este passo é necessário quando a migração estiver concluída, se a sua implementação do AD RMS estava a utilizar 1 de modo criptográfico RMS, porque novamente keying cria uma nova chave de inquilino que utiliza o RMS modo criptográfico 2. Utilizar o Azure RMS com 1 de modo criptográfico é suportada apenas durante o processo de migração.

Este passo é opcional mas recomendada quando a migração estar concluída, mesmo se estavam em execução no RMS modo criptográfico 2, porque ajuda a proteger a chave de inquilino do Azure RMS a partir de potenciais falhas de segurança para a chave de AD RMS. Quando a chave novamente a chave de inquilino do Azure RMS (também conhecido como "sucessiva a chave"), é criada uma nova chave e a chave original é arquivada. No entanto, porque a mover de uma chave para outro não ocorrer imediatamente mas através de alguns semanas, não aguardar pelo suspeitar uma violação para a chave original mas chave novamente a chave do RMS inquilino assim que a migração estar concluída.

A chave novamente a chave de inquilino do Azure RMS:

-   Se a chave de inquilino do RMS for gerida pelo Microsoft: Microsoft suporte ao cliente (CSS) de chamadas e provar que é o administrador de inquilino do RMS.

-   Se a chave de inquilino do RMS for gerida por si (BYOK): Repita o procedimento BYOK para gerar e crie uma nova chave através da Internet ou na pessoa.

Para obter mais informações sobre como gerir a sua chave de inquilino do RMS, consulte o artigo [Operações para a sua chave de inquilino do Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

