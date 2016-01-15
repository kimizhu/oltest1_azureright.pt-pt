---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Preparar para o Azure Rights Management
Depois de ter inscrito para uma subscrição de nuvem e estabelecer a sua organização com uma conta para [!INCLUDE[o365_1](../Token/o365_1_md.md)] ou do Azure Active Directory, está pronto para ativar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço.

No entanto, antes de fazê-lo, certifique-se de que o seguem-se no local:

-   Contas de utilizador e grupos na nuvem que pode criar manualmente ou automaticamente que são criadas e sincronizadas a partir de serviços de domínio do Active Directory (AD DS).

    Quando sincroniza as suas contas no local e grupos, nem todos os atributos tem de ser sincronizados. Para obter uma lista dos atributos que têm de ser sincronizados para o Azure RMS, consulte este [secção do Azure RMS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) da documentação do Azure Active Directory. Para facilitar a implementação, recomendamos que utilize [o Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) para ligar o seu no local diretórios com o Azure Active Directory, mas podem utilizar qualquer método de sincronização de diretório que alcança o mesmo resultado.

-   Grupos com capacidade de correio na nuvem que irá utilizar com o Rights Management. Estes podem ser grupos incorporados ou criar manualmente os grupos que contêm os utilizadores que irão utilizar a gestão de direitos.

    Se tiver o Exchange Online, pode criar e utilizar grupos com capacidade de correio utilizando o Centro de administração do Exchange. Se tiver o AD DS e estão a sincronizar para o Azure AD, que pode criar e utilizar grupos com capacidade de correio que são grupos de segurança ou os grupos de distribuição.

## Ativar o Rights Management
Por predefinição, [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] é desativada quando se inscreve no seu [!INCLUDE[o365_2](../Token/o365_2_md.md)] ou conta do Azure AD. Para ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para a sua organização, tem de ativar o serviço. Para obter mais informações, consulte o artigo [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

