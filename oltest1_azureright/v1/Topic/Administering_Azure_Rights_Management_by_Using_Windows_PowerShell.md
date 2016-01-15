---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Administrar o Azure Rights Management utilizando o Windows PowerShell
Embora pode ativar o Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS do Azure), utilizando o [!INCLUDE[o365_2](../Token/o365_2_md.md)] Centro de administração ou portal do Azure clássico, também pode utilizar o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (AADRM) para efetuar este procedimento.

Depois de ter ativado [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], ainda mais administração para o serviço poderá não ser necessária. No entanto, alguns cenários de configuração avançada podem implicar a utilizar o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. A tabela seguinte lista algumas dos cenários de configuração avançadas que utilizam o Windows PowerShell. Para obter uma lista completa dos cmdlets disponíveis com mais informações sobre cada um deles, consulte o artigo [Cmdlets de gestão de direitos do Azure](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Se tem de instalar o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Também é um módulo do Windows PowerShell suplementar, **RMSProtection**, que suporta o Azure RMS e AD RMS. Este módulo suporta proteger e remover a proteção de vários ficheiros de modo a que, por exemplo, pode proteger em massa todos os ficheiros numa pasta. Para obter mais informações, consulte o [Opções de script para utilizadores super](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) secção a [Configurar utilizadores Super para o Azure Rights Management e os serviços de deteção ou recuperação de dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) tópico.

|Se precisar de...|…. Utilize os seguintes cmdlets|
|---------------------|-----------------------------------|
|Migrar de gestão de direitos no local (AD RMS ou do Windows RMS) para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Importar AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Ligar ou desligar a partir de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço para a sua organização.|[AadrmService ligar](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[AadrmService desligar](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Gerar e gerir a sua própria chave inquilino – a colocar o seu cenário de chave (BYOK).|[AadrmKey adicionar](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Ativar ou desativar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço para a sua organização.|[Ativar Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Desativar Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Desactivar ou activar o documento de controlo do site para o Azure Rights Management.|[Desativar AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Ativar AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Configure os controlos de integração de uma implementação faseada do Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Conjunto AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Criar e gerir modelos de política de direitos para a sua organização.|[AadrmTemplate adicionar](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Exportação AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Importar AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[Novo AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remover AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Conjunto AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Configure o número máximo de dias que pode ser acedido conteúdo que protege a sua organização sem uma ligação de Internet (utilize licença do período de validade).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Conjunto AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Gerir a funcionalidade de utilizador super do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para a sua organização.|[Ativar AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Desativar AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[AadrmSuperUser adicionar](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remover AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Gerir utilizadores e grupos que têm autorização para administrar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço para a sua organização.|[AadrmRoleBasedAdministrator adicionar](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remover AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Obter um registo de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] tarefas administrativas da sua organização.|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Inicie sessão e analisar a utilização de registo para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Ativar AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Conjunto AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Desativar AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|Apresentar o atual [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] a configuração do serviço para a sua organização.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migrar a sua organização a partir de [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para no local implementação do AD RMS.|[Conjunto AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## Consultar Também
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

