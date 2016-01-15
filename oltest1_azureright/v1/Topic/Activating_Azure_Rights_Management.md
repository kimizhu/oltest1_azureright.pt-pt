---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Ativar o Azure Rights Management
Quando ativar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS) do Azure, a organização pode começar a proteger dados importantes através da utilização de aplicações e serviços que suportam esta solução de proteção de informações. Os administradores também podem gerir e monitorizar ficheiros protegidos e os e-mails que a sua organização é proprietária. Tem de ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] antes de poder começar a utilizar as funcionalidades de gestão (IRM) de direitos de informação no Office, o SharePoint e o Exchange e proteger um ficheiro sensível ou confidencial.

Se pretender saber mais sobre a gestão de direitos do Azure antes de ativar o serviço de — por exemplo, os problemas de empresas que resolve, nalguns casos de utilização típica e como funciona, consulte [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Para ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], certifique-se de que a sua organização tiver um plano de serviço que inclui [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviços. Caso contrário, não será possível ativar o Azure RMS.
> 
> Para obter mais informações, consulte o [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico.

Depois de ter ativado o Azure RMS, todos os utilizadores na sua organização podem aplicar a proteção de informações para os respetivos ficheiros e todos os utilizadores podem abrir (consumir) ficheiros que foram protegidos pelo Azure RMS. No entanto, se preferir, pode restringir quem pode aplicar a proteção de informações, ao utilizar controlos de integração para uma implementação faseada. Para obter mais informações, consulte o [Configurar os controlos de integração para uma implementação faseada](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) deste tópico.

## Ativar o Rights Management
Utilize um dos seguintes procedimentos para ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Também pode utilizar o cmdlet do Windows PowerShell, [Ativar Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), para ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Para ativar o Rights Management a partir do Centro de administração do Office 365

1.  Depois de se inscreveu para um plano do Office 365 que inclui a gestão de direitos, [Inicie sessão no Office 365 com a sua conta escolar ou profissional](https://portal.office.com/) ou seja, um administrador para a implementação do Office 365.

2.  Se o Centro de administração do Office 365 não for apresentada automaticamente, selecione o ícone da aplicação de iniciador no canto superior esquerdo e escolha **Admin**. O **Admin** mosaico só aparece aos administradores do Office 365.

    > [!TIP]
    > Para obter ajuda do Centro de administração, consulte o artigo [Centro de administração sobre o Office 365 - ajuda da administração](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  No painel da esquerda, expanda **definições de serviço**.

4.  Clique em **Gestão de direitos de**.

    > [!NOTE]
    > Se não visualizar esta opção, poderá ser porque a versão de produtos ou plano de serviço não é possível suportar a gestão de direitos, ou ainda não foi atualizada para suportar a gestão de direitos.
    > 
    > Utilize as informações de [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico para confirmar o suporte. Se a versão de produtos ou plano de serviço é suportada, mas não vir a opção de gestão de direitos, poderá ser porque o serviço ainda não foi atualizado. Para obter ajuda com este problema, envie uma mensagem de correio eletrónico para [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  No **RIGHTS MANAGEMENT** página, clique em **Gerir**.

6.  No **Gestão de direitos de** página, clique em **Ativar**.

7.  Quando lhe for pedido **que pretende ativar o Rights Management?**, clique em **Ativar**.

Deverá ver **Rights management é ativado** e a opção para desativar.

#### Para ativar o Rights Management a partir do portal do Azure clássico

1.  Depois de se inscreveu para a sua conta Azure, [Inicie sessão no portal do Azure clássico](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  No painel da esquerda, clique em **do Active Directory**.

3.  A partir de **do Active Directory** página, clique em **RIGHTS MANAGEMENT**.

4.  Selecione o diretório para gerir para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], clique em **ATIVAR**, e, em seguida, confirme a ação.

    > [!NOTE]
    > Se vir um erro de ativação, poderá ser porque a versão de produtos ou plano de serviço não pode suportar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Utilize as informações de [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico para confirmar suporte RMS. Para obter ajuda com este problema, envie uma mensagem de correio eletrónico para [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

O **Estado da gestão de direitos** deverá agora apresentar **Active Directory** e **ATIVAR** opção é substituída pelo **DESATIVAR**.

### Valores de estado de gestão de direitos e as descrições no portal do Azure clássico
Para além de **Active Directory** Estado, o que indica que o serviço de gestão de direitos está ativado e pronto a ser utilizado, também poderá ver **inativo**, **indisponível**, ou **não autorizado**.

|Valor de estado|Descrição|
|-------------------|-------------|
|**Active Directory**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] é ativada e pronto a utilizar.|
|**Inativo**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] está desativada e tem de ser ativado antes da sua organização pode proteger ficheiros.|
|**Não disponível**|O [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] o serviço está inativo. Tente novamente mais tarde.|
|**Não autorizado**|Não tem permissões para ver o estado do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço. Por exemplo, a sua conta está bloqueada ou não for o administrador global para o inquilino selecionado.|

## <a name="BKMK_OnboardingControls"></a>Configurar os controlos de integração para uma implementação faseada
Se não pretender que todos os utilizadores para poder proteger ficheiros imediatamente utilizando o Azure RMS, pode configurar os controlos de integração do utilizador utilizando o [conjunto AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) comando do Windows PowerShell. Pode executar este comando antes ou depois de ativar o Azure RMS.

> [!IMPORTANT]
> Para utilizar este comando, tem de ter, pelo menos, versão **2.1.0.0** do [módulo do Windows PowerShell do Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Para verificar a versão que instalou, execute: **(Get-Module aadrm –ListAvailable).Version**

Por exemplo, se pretender inicialmente apenas os administradores do grupo de "Departamento de TI" (que tem um ID de objeto de fbb99ded-32a0-45f1-b038-38b519009503) para poder proteger conteúdo para fins de teste, utilize o seguinte comando:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Tenha em atenção que para esta opção de configuração, tem de especificar um grupo de; Não é possível especificar os utilizadores individuais.

Ou, se pretender certificar-se de que apenas utilizadores que são licenciados corretamente ao utilizar o Azure RMS podem proteger conteúdo:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Quando utilizar estes controlos de integração, todos os utilizadores na organização sempre podem consumir conteúdo protegido que foi protegido pelo subconjunto de utilizadores, mas não poderão aplicar-se a si proteção de informações a partir de aplicações de cliente. Por exemplo, não poderão ver os seus clientes do Office modelos predefinidos que são automaticamente publicados quando está ativado o Azure RMS ou modelos personalizados que pode configurar.  Aplicações do lado do servidor, como o Exchange, podem implementar os seus próprios controlos por utilizador para a integração do RMS alcançar o mesmo resultado.

## Próximos passos
Agora que tenha ativado [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para a sua organização, utilize o [Plano de implementação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para verificar se existem outros passos de configuração que poderá ter de fazer antes de ser realizadas [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para utilizadores e administradores. Por exemplo, pode querer utilizar [modelos personalizados](http://technet.microsoft.com/library/dn642472.aspx) para tornar mais fácil para os utilizadores aplicar proteção de informações a ficheiros, ligar-se os servidores no local para utilizar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] instalando o [conector RMS](http://technet.microsoft.com/library/dn375964.aspx), e implementar o [aplicação de partilha Rights Management](http://technet.microsoft.com/library/jj585031.aspx) que suporta proteger todos os tipos de ficheiro em todos os dispositivos. Serviços do Office, como o Exchange Online e no SharePoint Online necessitam de configuração adicional antes de poder utilizar as respetivas funcionalidades de gestão de direitos de informação (IRM). No entanto, se existirem nenhuma outra configuração os passos que necessita, ver [Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) para obter orientações sobre operacional suportar uma implementação efetuada com êxito para a sua organização.

Para obter informações sobre como as suas aplicações de trabalhar com [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], consulte o artigo [Como as aplicações suportam gestão de direitos do Azure](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

