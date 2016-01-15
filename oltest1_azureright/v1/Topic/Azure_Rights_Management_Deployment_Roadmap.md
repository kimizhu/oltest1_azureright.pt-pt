---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Plano de implementa&#231;&#227;o do Azure Rights Management
Utilize os seguintes passos para preparar, implementar e gerir Azure Rights Management (RMS do Azure) para a sua organização.

No entanto, se pretender apenas para tentar rapidamente o Azure RMS para si próprio, que é possível reduzir num ambiente de produção, ver [Tutorial guia de introdução para o Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Antes de efetuar os seguintes passos, certifique-se de que reviu [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Passo 1: Confirme se tem uma subscrição que inclui o Azure Rights Management
Existe mais do que um tipo de subscrição que inclui [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Consulte o [Subscrições de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) secção a [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tópico e verifique se a sua subscrição inclui as funcionalidades que pretende utilizar na sua organização através da referenciação a tabela [ofertas de comparação do Rights Management Services (RMS)](https://technet.microsoft.com/dn858608).

## Passo 2: Preparar a sua conta de inquilino para utilizar a gestão de direitos
Antes de começar a utilizar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], efetue a preparação do seguinte:

1.  Certifique-se de que o seu inquilino do Azure ou do Office 365 contém as contas de utilizador e grupos que vão ser utilizados pelo Azure RMS para autenticar os utilizadores da sua organização. Se necessário, crie estes conta e grupos ou sincronize-os partir do directory no local. Para obter mais informações, consulte o artigo [Preparar para o Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Decida se pretende que a Microsoft para gerir a sua chave de inquilino (predefinição), ou gerar e gerir a sua chave de inquilino sozinho (conhecidas como repor a sua própria chave ou BYOK). Tenha em atenção que, atualmente, não é possível utilizar BYOK se utilizar o Exchange Online. Para obter mais informações, consulte o artigo [Planear e implementar a sua chave de inquilino do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Instalar o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] em, pelo menos, um computador que tenha acesso à Internet. Pode efetuar este passo agora, ou posterior. Para obter mais informações, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Se estiver a utilizar serviços de gestão de direitos no local: Efetue uma migração para mover as chaves, modelos e URLs para a nuvem. Para obter mais informações, consulte o artigo [Migrar do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Ative a gestão de direitos de modo a que pode começar a utilizar o serviço. Se for necessária uma implementação faseada, configure os controlos de integração do utilizador para restringir a utilização a utilizadores específicos. Para obter mais informações, consulte o artigo [Ativar o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

Opcionalmente, considere configurar o seguinte:

-   Modelos personalizados, se a predefinição de direitos de modelos de política não são suficientes para a sua organização. Pode efetuar este passo agora, ou posterior. Para obter mais informações, consulte o artigo [Configurar modelos personalizados para o Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Registo de utilização para que possa monitorizar a forma como a sua organização utiliza Rights Management. Pode efetuar este passo agora, ou posterior. Para obter mais informações, consulte o artigo [Registo e analisar a utilização de gestão de direitos do Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Passo 3: Configurar as suas aplicações e serviços para gestão de direitos
Configurar as aplicações pode incluir a instalação de gestão de direitos de aplicação de partilha e ativar o suporte para funcionalidades de gestão (IRM) de direitos de informação no SharePoint Online ou Exchange Online. Para obter mais informações, consulte o artigo [Configurar as aplicações para o Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Se tiver de serviços de TI existentes que necessitam para inspecionar os ficheiros que irá proteger o Azure RMS — tais como soluções de prevenção (DLP) de fuga de dados, conteúdo gateways de encriptação (CEG) e produtos de software antimalware — configure as contas de serviço para ser super utilizadores para o Azure RMS. Para obter mais informações, consulte o artigo [Configurar utilizadores Super para o Azure Rights Management e os serviços de deteção ou recuperação de dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Se tiver de serviços no local que pretende utilizar com o Azure Rights Management, instalar e configurar o conector de gestão de direitos. Para obter mais informações, consulte o artigo [Implementar o conector de gestão de direitos do Azure](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Passo 4: Publicar e consumir conteúdo protegido por direitos
Agora está pronto para publicar e consumir conteúdo protegido e, como a sua empresa estiver a utilizar gestão de direitos de registo. Para obter mais informações, consulte o artigo [Utilizar o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Passo 5: Administrar o Rights Management para a sua conta de inquilino conforme necessário
Como começar a utilizar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], poderá considerar a [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] módulo para o Windows PowerShell útil para ajudar o script ou automatizar alterações administrativas. Para obter mais informações, consulte o artigo [Administrar o Azure Rights Management utilizando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

