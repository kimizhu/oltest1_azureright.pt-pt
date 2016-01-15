---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Configurar utilizadores Super para o Azure Rights Management e os servi&#231;os de dete&#231;&#227;o ou recupera&#231;&#227;o de dados
A funcionalidade de utilizador super do Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS do Azure) assegura que as pessoas autorizadas e os serviços podem sempre ler e inspecionar os dados que o Azure RMS protege para a sua organização. E se for necessário, remova a proteção ou alterar a proteção que estava anteriormente aplicada. Um utilizador super sempre tem direitos de proprietário completa para todas as licenças de utilização que lhe foi atribuído ao inquilino de RMS da sua organização. Esta capacidade é por vezes referida como "reasoning através de dados" e é um elemento fundamental mantém o controlo de dados da sua organização. Por exemplo, utilizaria esta funcionalidade para qualquer um dos seguintes cenários:

-   Um empregado deixar a organização e precisa de ler os ficheiros que estão protegidos.

-   Administrador de TI tem de remover a política de proteção atual que foi configurada para ficheiros e aplicar uma nova política de proteção.

-   Exchange Server tem de caixas de correio do índice para operações de pesquisa.

-   Tem de serviços de TI existentes para soluções de (DLP) de prevenção de perda de dados, os gateways de encriptação de conteúdo (CEG) e produtos de software antimalware que necessitam para inspecionar os ficheiros que já estão protegidos.

-   É necessário em massa desencriptar ficheiros de auditoria, legais ou outros motivos de conformidade.

Por predefinição, a funcionalidade de utilizador super não está ativada e, sem utilizadores são atribuídos esta função. -É ativado para si automaticamente se configurar o conector de gestão de direitos para o Exchange e não é necessária relativas a serviços padrão que executam o Exchange Online, SharePoint Online ou no SharePoint Server.

Se precisar de ativar manualmente a funcionalidade de utilizador super, utilize o cmdlet do Windows PowerShell [Ativar AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), e, em seguida, atribua utilizadores (ou contas de serviço), conforme necessário, utilizando o [Adicionar AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) cmdlet. Pode ter um ou vários utilizadores super para a sua organização, mas tem de adicionar os utilizadores individuais. grupos não são suportados.

> [!NOTE]
> Se ainda não instalou o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Melhores práticas de segurança para a funcionalidade de utilizador super:

-   Restrinja e monitorize os administradores que são atribuídos um administrador global do seu inquilino do Office 365 ou do Azure RMS ou que estão atribuídos a função GlobalAdministrator utilizando o [Adicionar AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) cmdlet. Estes utilizadores podem ativar a funcionalidade de utilizador super e atribuir utilizadores (e próprios) como utilizadores super e desencriptar potencialmente todos os ficheiros que protege a sua organização.

-   Para ver quais os utilizadores e contas de serviço são atribuídas como super utilizadores, utilize o [cmdlet Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Como todas as ações de administração, ativar ou desativar a funcionalidade super e adicionar ou remover utilizadores super são registados e pode ser auditada, utilizando o [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) comando. Quando os utilizadores super desencriptar ficheiros, esta ação é iniciada e pode ser auditada com [registo utilização](https://technet.microsoft.com/library/dn529121.aspx).

-   Se não tiver a funcionalidade de utilizador super para serviços diárias, ativar a funcionalidade apenas quando precisar dele e desativá-lo novamente utilizando o [desativar AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) cmdlet.

A extrair registo seguinte mostra algumas entradas de exemplo a partir do utilizando o cmdlet Get-AadrmAdminLog. Neste exemplo, o administrador da Contoso Lda. confirma que a funcionalidade de utilizador super está desativada, adiciona Fernando Simone como um utilizador super, verifica se o Rodrigo é o utilizador só super configurado para o Azure RMS e, em seguida, ativa a funcionalidade de utilizador super para que o Fernando agora pode desencriptar alguns ficheiros que foram protegidos por um empregado que ainda tem agora a empresa.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Opções de script para utilizadores super
Muitas vezes, uma pessoa em quem é atribuído um utilizador super para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] terá de remover a proteção de vários ficheiros, em várias localizações. Embora seja possível para o fazer manualmente, é mais eficaz (e, muitas vezes, mais fiável) para este script. Para fazê-lo, [Transfira a ferramenta de proteção RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Em seguida, utilize o  [Unprotect-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) cmdlet, e [proteger RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx)   cmdlet conforme necessário.

> [!IMPORTANT]
> Embora a ferramenta de proteção RMS foi concebida para utilizadores super em massa desproteger ficheiros para fins de recuperação, a versão atual da ferramenta não suporta a autenticação de utilizador para o Azure RMS. Até que esta limitação for resolvida, tem de utilizar uma conta principal do serviço para autenticar com o Azure RMS antes de poder remover proteção a partir dos ficheiros.  Para mais informações e instruções, consulte o artigo [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Para mais informações sobre estes cmdlets, consulte o artigo [RMS proteção Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> O módulo de RMSProtection Windows PowerShell que é fornecido com a ferramenta de proteção RMS é diferente do e complementam principal [módulo do Windows PowerShell para o Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx). Suporta Azure RMS e AD RMS.

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

