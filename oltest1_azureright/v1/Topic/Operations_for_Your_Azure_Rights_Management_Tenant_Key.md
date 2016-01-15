---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Opera&#231;&#245;es para a sua chave de inquilino do Azure Rights Management
Dependendo do seu inquilino chave topologia (gerido por Microsoft ou geridos pelo cliente), está a ter diferentes níveis de controlo e de responsabilidade para a sua chave de inquilino do Microsoft Azure Rights Management (RMS do Azure) estiver implementado.

Quando gere a sua própria chave do inquilino, isto é frequentemente referido como colocar o seu próprio chave (BYOK). Para obter mais informações sobre este cenário e como escolher entre as topologias de chave do dois inquilino, consulte o artigo [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

A tabela seguinte identifica as operações que pode fazer, consoante a topologia de que escolheu para a sua chave de inquilino do Azure RMS.

|Operação de ciclo de vida|Gerido por Microsoft (predefinição)|Cliente gerido (BYOK)|
|-----------------------------|---------------------------------------|-------------------------|
|Revogar a sua chave de inquilino|Nenhum (automática)|Nenhum (automática)|
|Chave novamente a chave de inquilino|Sim|Sim|
|Cópia de segurança e recuperar a sua chave de inquilino|Não|Sim|
|Exportar a chave de inquilino|Sim|Não|
|Responder a uma violação|Sim|Sim|
Depois de identificar qual topologia ter implementado, utilize uma das secções seguintes para obter mais informações sobre estas operações para a sua chave de inquilino do Azure RMS.

## <a name="BKMK_MSManagedOperations"></a>Gerido por Microsoft: Operações de ciclo de vida de chaves de inquilino
Se a Microsoft gere a sua chave de inquilino do Azure Rights Management (predefinição), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que sejam relevantes para esta topologia:

-   [Revogar a sua chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Chave novamente a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Cópia de segurança e recuperar a sua chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Exportar a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Responder a uma violação](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>Revogar a sua chave de inquilino
Quando anular a subscrição do Azure RMS, deixa de Azure RMS utilizando a chave de inquilino e não é necessária nenhuma ação do utilizador.

### <a name="BKMK_MSRekey"></a>Chave novamente a chave de inquilino
Novamente keying também é conhecido como a sua chave. Não voltar a chave a chave do inquilino, a menos que é realmente necessário. Clientes antigos, como o Office 2010, não foram concebidos para processar alterações chave diminuir corretamente. Neste cenário, tem de limpar o estado do RMS em computadores utilizando a política de grupo ou um mecanismo equivalente. No entanto, existem alguns eventos legítimos que poderão forçar a tecla novamente a chave de inquilino. Por exemplo:

-   A sua empresa tem dividida em duas ou mais empresas. Quando a chave novamente a chave do inquilino, a empresa novo não terão acesso a conteúdo novo que publicar os seus funcionários. Estes podem aceder ao conteúdo antigo que possuam uma cópia da chave de inquilinos antigo.

-   Considerar que a cópia principal da sua chave de inquilino (cópia no seu posse) foi comprometida.

Pode voltar a chave a chave de inquilino chamar Microsoft suporte ao cliente (CSS) e comprovar que é o administrador inquilino.

Quando a chave novamente a chave do inquilino, novo conteúdo é protegido através da utilização a nova chave de inquilino. Isto acontece de forma faseada, pelo que, durante um período de tempo, algum conteúdo novo irá continuar a ser protegidos com a chave de inquilinos antigo. Anteriormente conteúdo protegido permanece protegido a sua chave de inquilinos antigo. Para suportar este cenário, o Azure RMS retém a chave de inquilinos antigo, de modo a que pode emitir licenças para o conteúdo antigo.

### <a name="BKMK_MSBackup"></a>Cópia de segurança e recuperar a sua chave de inquilino
A Microsoft é responsável pela cópia a chave de inquilino de segurança e não é necessária a partir de nenhuma ação.

### <a name="BKMK_MSExport"></a>Exportar a chave de inquilino
Pode exportar a configuração do Azure RMS e a chave de inquilino, seguindo as instruções nestes três passos:

##### Passo 1: Iniciar a exportação

-   Para fazer isto, contacte o suporte de serviço ao cliente da Microsoft (CSS). Terá de provar a que é um administrador do seu inquilino do Azure RMS.

##### Passo 2: Aguarde pela verificação

-   Microsoft verifica se o seu pedido para libertar a chave do RMS inquilino é legítimo. Este processo pode demorar cerca de 3 semanas.

##### Passo 3: Receba instruções chave CSS

-   Microsoft suporte ao cliente (CSS) irá enviar-o a configuração do Azure RMS e a chave de inquilino como encriptados num ficheiro protegido por palavra-passe que tem uma extensão de nome de ficheiro .tpd. Para fazer isto, CSS primeiro envia-lhe (como a pessoa que iniciou a exportação) uma ferramenta por correio eletrónico. Tem de executar a ferramenta a partir de uma linha de comandos da seguinte forma:

    ```
    AadrmTpd.exe -createkey
    ```
    Isto gera um par de chaves RSA e guarda as halves públicas e privadas, como ficheiros na pasta atual. Por exemplo: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** e **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Responder à mensagem de e-mail a partir de CSS, anexar o ficheiro que tem um nome que comece com **PublicKey**. CSS junto enviará é um ficheiro TPD como um ficheiro. XML que está encriptado com a sua chave RSA. Copie este ficheiro para a mesma pasta que executou a ferramenta de AadrmTpd originalmente, e execute a ferramenta de novamente, utilizando o ficheiro que começa com **PrivateKey** e o ficheiro da CSS. Por exemplo:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    A saída deste comando deve ser dois ficheiros: Contém a palavra-passe de texto simples para TPD protegidas por palavra-, e a outra é TPD protegidos por palavra-passe próprio. Para cross-referencing fins, ambos devem ter o mesmo GUID do que os ficheiros de chaves públicos e privados a partir do quando tiver executado o comando de - createkey AadrmTpd.exe:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Estes ficheiros de cópia de segurança e armazená-los de forma segura para se certificar de que pode continuar a desencriptar o conteúdo que é protegido com esta chave de inquilino. Além disso, se está a migrar para o AD RMS, pode importar este ficheiro TPD (o ficheiro que começa com **ExportedTDP**) para o seu servidor AD RMS.

##### Passo 4: Em curso: Proteger a sua chave de inquilino

-   Depois de receber a sua chave de inquilino, mantê-lo bem protegidos, porque se alguém obtém acesso ao mesmo, podem desencriptar todos os documentos que estão protegidos utilizando essa chave.

    Se o motivo para exportar a chave do inquilino é uma vez que já não pretende utilizar o Azure RMS, como melhor prática, agora a desativar o seu inquilino do RMS. Não atrase fazê-lo Depois de receber a sua chave de inquilino porque este precaução irão ajudar a minimizar as consequências se a sua chave de inquilino é acedida por alguém que não deva ter. Para obter instruções, consulte o artigo [Desativação e a desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Responder a uma violação
Nenhum sistema de segurança, independentemente de como segura, foi concluído sem um processo de resposta ser infringidos. A chave de inquilino pode ser comprometida ou roubada. Mesmo quando é bem protegida bem, poderão encontrar vulnerabilidades na tecnologia HSM geração atual ou atuais comprimentos de chaves e algoritmos.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança dos seus produtos e serviços. Assim que existe um relatório credible de um incidente, esta equipa engages investigar as atenuações, âmbito e causa raiz. Se este incidente afetar os ativos, em seguida, Microsoft irá notificar os administradores de inquilinos do Azure RMS por correio eletrónico utilizando o endereço que especificou quando subscreveu.

Se tiver uma violação, a melhor ação que o utilizador ou a Microsoft pode demorar depende no âmbito da violação; Microsoft irá trabalhará consigo através deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável que, apesar da resposta exata irá depender de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|--------------------------|---------------------|
|A chave do inquilino é obtidas ilicitamente.|Chave novamente a chave de inquilino. Consulte o [Chave novamente a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) deste tópico.|
|Uma pessoa não autorizada ou software maligno tem direitos para utilizar a sua chave de inquilino, mas a chave próprio não fuga.|Keying novamente a chave de inquilino não ajuda aqui e requer a análise da causa de raiz. Se um erro de processo ou software foi responsável pelo individuais obter acesso não autorizado, essa situação tem de ser resolvida.|
|Vulnerabilidade detetada no algoritmo RSA, ou comprimento de chave ou ataques de força bruta tornam-se computationally exequível.|Microsoft tem de atualizar o Azure RMS para suportar a nova algoritmos e mais os comprimentos de chave são resilientes e instruir todos os clientes para renovar as respetivas chaves de inquilino.|

## <a name="BKMK_BYOKManagedOperations"></a>Cliente gerido: Operações de ciclo de vida de chaves de inquilino
Se gerir a sua chave de inquilino do Azure Rights Management (a colocar os seus próprios chave ou BYOK, cenário), utilize as secções seguintes para obter mais informações sobre as operações de ciclo de vida que sejam relevantes para esta topologia:

-   [Revogar a sua chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Chave novamente a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Cópia de segurança e recuperar a sua chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Exportar a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Responder a uma violação](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>Revogar a sua chave de inquilino
Quando anular a subscrição do Azure RMS, deixa de Azure RMS utilizando a chave de inquilino e não é necessária nenhuma ação do utilizador.

### <a name="BKMK_BYOKRekey"></a>Chave novamente a chave de inquilino
Novamente keying também é conhecido como a sua chave. Não voltar a chave a chave do inquilino, a menos que é realmente necessário. Clientes antigos, como o Office 2010, não foram concebidos para processar alterações chave diminuir corretamente. Neste cenário, tem de limpar o estado do RMS em computadores utilizando a política de grupo ou um mecanismo equivalente. No entanto, existem alguns eventos legítimos que poderão forçar a tecla novamente a chave de inquilino. Por exemplo:

-   A sua empresa tem dividida em duas ou mais empresas. Quando a chave novamente a chave do inquilino, a empresa novo não terão acesso a conteúdo novo que publicar os seus funcionários. Estes podem aceder ao conteúdo antigo que possuam uma cópia da chave de inquilinos antigo.

-   Considerar que a cópia principal da sua chave de inquilino (cópia no seu posse) foi comprometida.

Quando a chave novamente a chave do inquilino, novo conteúdo é protegido através da utilização a nova chave de inquilino. Isto acontece de forma faseada, pelo que, durante um período de tempo, algum conteúdo novo irá continuar a ser protegidos com a chave de inquilinos antigo. Anteriormente conteúdo protegido permanece protegido a sua chave de inquilinos antigo. Para suportar este cenário, o Azure RMS retém a chave de inquilinos antigo, de modo a que pode emitir licenças para o conteúdo antigo.

A chave novamente a chave do inquilino, gerar e crie uma nova chave através da Internet ou na pessoa, utilizando os procedimentos apresentados a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) secção a partir do [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico.

### <a name="BKMK_BYOKBackup"></a>Cópia de segurança e recuperar a sua chave de inquilino
É responsável pela sua chave de inquilino de segurança. Se gerado a chave de inquilino num HSM Thales, para agregar a chave, basta cópia de segurança o ficheiro da chave foi Atomizada, o ficheiro do mundo e o administrador cartões.

Se transferir a chave de seguindo os procedimentos apresentados a [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) secção a partir do [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tópico, o Azure RMS serão mantidas o ficheiro da chave foi Atomizada, para proteção contra falhas de quaisquer nós do Azure RMS. No entanto, não considere esta seja uma cópia de segurança completa. Por exemplo, se alguma vez precisar de uma cópia de texto simples da sua chave para utilizar fora um HSM Thales, Azure RMS não será possível recuperá-la por si, porque tem apenas uma cópia não recuperável.

### <a name="BKMK_BYOKExport"></a>Exportar a chave de inquilino
Se utilizar BYOK, não é possível exportar a chave de inquilino do Azure RMS. A cópia no Azure RMS é não recuperável. Se pretende eliminar esta chave, para que possam ser utilizados, contacte o suporte de serviço ao cliente da Microsoft (CSS).

### <a name="BKMK_BYOKBreach"></a>Responder a uma violação
Nenhum sistema de segurança, independentemente de como segura, foi concluído sem um processo de resposta ser infringidos. A chave de inquilino pode ser comprometida ou roubada. Mesmo quando é bem protegida bem, poderão encontrar vulnerabilidades na tecnologia HSM geração atual ou atuais comprimentos de chaves e algoritmos.

A Microsoft tem uma equipa dedicada para responder a incidentes de segurança dos seus produtos e serviços. Assim que existe um relatório credible de um incidente, esta equipa engages investigar as atenuações, âmbito e causa raiz. Se este incidente afetar os ativos, em seguida, Microsoft irá notificar os administradores de inquilinos do Azure RMS por correio eletrónico utilizando o endereço que especificou quando subscreveu.

Se tiver uma violação, a melhor ação que o utilizador ou a Microsoft pode demorar depende no âmbito da violação; Microsoft irá trabalhará consigo através deste processo. A tabela seguinte mostra algumas situações típicas e a resposta provável que, apesar da resposta exata irá depender de todas as informações que são reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|--------------------------|---------------------|
|A chave do inquilino é obtidas ilicitamente.|Chave novamente a chave de inquilino. Consulte o [Chave novamente a chave de inquilino](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) deste tópico.|
|Uma pessoa não autorizada ou software maligno tem direitos para utilizar a sua chave de inquilino, mas a chave próprio não fuga.|Keying novamente a chave de inquilino não ajuda aqui e requer a análise da causa de raiz. Se um erro de processo ou software foi responsável pelo individuais obter acesso não autorizado, essa situação tem de ser resolvida.|
|Vulnerabilidade detetada na tecnologia HSM geração atual.|A Microsoft tem de atualizar os HSMs. Se existir razão para considerar que a vulnerabilidade expostos chaves, o Microsoft instruirá todos os clientes para renovar as respetivas chaves de inquilino.|
|Vulnerabilidade detetada no algoritmo RSA, ou comprimento de chave ou ataques de força bruta tornam-se computationally exequível.|Microsoft tem de atualizar o Azure RMS para suportar a nova algoritmos e mais os comprimentos de chave são resilientes e instruir todos os clientes para renovar as respetivas chaves de inquilino.|

## Consultar Também
[Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

