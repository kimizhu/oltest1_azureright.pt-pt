---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Desativa&#231;&#227;o e a desativa&#231;&#227;o do Azure Rights Management
São sempre no controlo de se a organização protege conteúdo utilizando [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS) do Azure, e se decidir já não pretender utilizar esta solução de proteção de informações, tiver assurance que não irá ser bloqueado fora do conteúdo que foi protegido anteriormente. Se não precisar de contínua acesso ao conteúdo anteriormente protegido, simplesmente desativar o serviço e pode permitir que a sua subscrição do Azure Rights Management expirar. Por exemplo, este seria adequada para quando concluiu testar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] antes de implementar num ambiente de produção.

No entanto, se tiver implementado [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] na produção, certifique-se de que tem uma cópia da sua chave de inquilino do Azure Rights Management antes de desativar o serviço e efetuar este procedimento antes da sua subscrição expirar, uma vez que isto irá garantir que pode manter o acesso ao conteúdo que foi protegido pelo Azure Rights Management após o serviço está desativado. Se utilizou a colocar a sua própria solução de chave (BYOK), a onde gerar e gerir a sua própria chave num HSM, já terá a chave de inquilino do Azure Rights Management. Mas se foi gerido pela Microsoft (predefinição), consulte as instruções para exportar a chave de inquilino na [Operações para a sua chave de inquilino do Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md) tópico.

> [!TIP]
> Mesmo após a sua subscrição expirar, o seu inquilino do Azure Rights Management permanece disponível para consumir conteúdo durante um período prolongado. No entanto, já não será possível exportar a chave de inquilino.

Quando tiver a chave de inquilino do Azure Rights Management, pode implementar gestão de direitos no local (AD RMS) e importar a chave de inquilino como um domínio de publicação fidedigno (TPD). Em seguida, tem as seguintes opções para desativar a implementação do Azure Rights Management:

|Se isto aplica-se a si...|… Faça o seguinte:|
|-----------------------------|----------------------|
|Pretender todos os utilizadores para continuar a utilizar a gestão de direitos, mas utilizar uma solução no local em vez de utilizar o Azure RMS →|Utilize o [conjunto AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) cmdlet para direcionar utilizadores existentes para a implementação no local, quando estes consumam conteúdo protegido após esta alteração. Os utilizadores serão automaticamente a utilizar a instalação do AD RMS para consumir conteúdo protegido.<br /><br />Para que os utilizadores consomem conteúdo que foi protegido antes desta alteração, redirecionar os seus clientes para a implementação no local utilizando o **LicensingRedirection** chave de registo para o Office 2016 ou o Office 2013, tal como descrito no [secção de deteção do serviço](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) nas notas de implementação do cliente de RMS e o **LicenseServerRedirection** chave de registo para o Office 2010, conforme descrito em [definições de registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende parar de utilizar tecnologias de gestão de direitos completamente →|Conceder um administrador designado [super direitos de utilizador](https://technet.microsoft.com/library/mt147272.aspx) e dê a essa pessoa o [ferramenta de proteção RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Este administrador, em seguida, pode utilizar a ferramenta para em massa-desencriptar ficheiros em pastas que estavam protegidos pelo Azure Rights Management para que os ficheiros de reverter para estarem desprotegidos e, por conseguinte, podem ser lido sem uma tecnologia de Rights Management, tais como o Azure RMS ou o AD RMS. Esta ferramenta pode ser utilizada com o Azure RMS e AD RMS, pelo que terá a opção de desencriptação de ficheiros antes ou depois de desativar o Azure RMS ou uma combinação.|
|Não é possível identificar todos os ficheiros que estavam protegidos pelo Azure RMS ou pretender que todos os utilizadores possam ler automaticamente os ficheiros protegidos que foram perdidas →|Implementar uma definição de registo em todos os computadores cliente utilizando o **LicensingRedirection** chave de registo para 2016 do Office e Office 2013, tal como descrito no [secção de deteção do serviço](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) nas notas de implementação do cliente de RMS e o **LicenseServerRedirection** chave de registo para o Office 2010, conforme descrito em [definições de registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Também implementar outra definição de registo para impedir que os utilizadores novos ficheiros a proteger definindo **DisableCreation** para **1**, conforme descrito em [definições de registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende que um serviço de recuperação manual controlada para todos os ficheiros que foram perdida →|Conceder designados utilizadores num grupo de recuperação de dados [super direitos de utilizador](https://technet.microsoft.com/library/mt147272.aspx) e conceder-lhes o [ferramenta de proteção RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256) para que eles podem desproteger ficheiros quando solicitado por utilizadores padrão.<br /><br />Em todos os computadores, implemente o definição para impedir que os utilizadores novos ficheiros a proteger através da definição de registo **DisableCreation** para **1**, conforme descrito em [definições de registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Para mais informações sobre os procedimentos nesta tabela, consulte os seguintes recursos:

-   Para obter informações sobre o AD RMS e referências de implementação, consulte [Active Directory direitos de serviços de descrição geral da gestão](https://technet.microsoft.com/library/hh831364.aspx).

-   Para obter instruções para importar a chave de inquilino do Azure RMS como um ficheiro TPD, consulte o artigo [Adicionar um domínio de publicação fidedigno](https://technet.microsoft.com/library/cc771460.aspx).

-   Para instalar o módulo do Windows PowerShell para o Azure RMS, para definir o URL de migração, consulte o artigo [Instalação do Windows PowerShell para o Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Quando estiver pronto para desativar o serviço do Azure RMS para a sua organização, utilize as instruções seguintes.

## Desativar o Rights Management
Utilize um dos seguintes procedimentos para desativar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Também pode utilizar o cmdlet do Windows PowerShell, [desativar Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), para desativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Para desativar o Rights Management a partir do Centro de administração do Office 365

1.  [Inicie sessão no Office 365 com a sua conta escolar ou profissional](https://portal.office.com/) ou seja, um administrador para a implementação do Office 365.

2.  Se o Centro de administração do Office 365 não for apresentada automaticamente, selecione o ícone da aplicação de iniciador no canto superior esquerdo e escolha **Admin**. O **Admin** mosaico só aparece aos administradores do Office 365.

    > [!TIP]
    > Para obter ajuda do Centro de administração, consulte o artigo [Centro de administração sobre o Office 365 - ajuda da administração](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  No painel da esquerda, expanda **definições de serviço**.

4.  Clique em **Gestão de direitos de**.

5.  No **RIGHTS MANAGEMENT** página, clique em **Gerir**.

6.  No **Gestão de direitos de** página, clique em **desativar**.

7.  Quando lhe for pedido **que pretende desativar o Rights Management?**, clique em **desativar**.

Deverá ver **Rights Management não se encontra ativado** e a opção para ativar.

#### Para desativar o Rights Management a partir do portal do Azure

1.  Início de sessão para o [portal do Azure clássico](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  No painel da esquerda, clique em **do Active Directory**.

3.  A partir de **do Active Directory** página, clique em **RIGHTS MANAGEMENT**.

4.  Selecione o diretório para gerir para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], clique em **DESATIVAR**, e, em seguida, confirme a ação.

O **Estado da gestão de direitos** deverá agora apresentar **inativo** e **DESATIVAR** opção é substituída pelo **ATIVAR**.

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

