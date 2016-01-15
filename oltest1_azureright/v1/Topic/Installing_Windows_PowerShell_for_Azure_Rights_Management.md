---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Instala&#231;&#227;o do Windows PowerShell para o Azure Rights Management
Utilize as seguintes informações para o ajudar a instalar o Windows PowerShell para o Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (RMS do Azure).

Pode utilizar este módulo do Windows PowerShell para administrar [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] na linha de comandos, utilizando qualquer computador que tenha uma ligação à Internet e que cumpre os pré-requisitos indicados na secção seguinte. O Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] suporta scripts para automatização ou poderá ser necessário para cenários de configuração avançada. Para obter mais informações sobre as tarefas de administração e configurações que suporte o módulo, consulte o artigo [Administrar o Azure Rights Management utilizando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Pré-requisitos
Esta tabela lista os pré-requisitos para instalar e utilizar o Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Requisito|Obter mais informações|
|-------------|--------------------------|
|Uma versão do Windows que suporte o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] módulo de administração|Verifique a lista de sistemas operativos suportados no **requisitos de sistema** secção a [página de transferência para a ferramenta de administração de gestão de direitos de Azure](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Versão mínima do Windows PowerShell: 2.0|Suporte para o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] módulo administração é introduzido no Windows PowerShell 2.0.<br /><br />Por predefinição, a maioria dos sistemas de operativos Windows instalar com, pelo menos, versão 2.0 do Windows PowerShell. Se precisar de instalar o Windows PowerShell 2.0, consulte o artigo [instalar o Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** Pode confirmar a versão do Windows PowerShell que estiver a executar, escrevendo **$PSVersionTable** numa sessão do Windows PowerShell.|
|Versão mínima do Microsoft .NET Framework: 4.5 **Tip:** Esta versão do Microsoft .NET Framework está incluída em sistemas de operativos posteriores, pelo que só deverá precisar de instalar manualmente se o sistema operativo do cliente for menor que o Windows 8.0 ou o sistema operativo do servidor é inferior ao Windows Server 2012.|Se esta ainda não estiver instalada, pode transferir o [o Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Esta versão do Microsoft .NET Framework é necessária para algumas das classes que o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] utiliza o módulo de administração.|
|Início de sessão do assistente 7.0 do Microsoft Online Services|O assistente Microsoft Online Services início de sessão é necessário para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] autenticação.<br /><br />Para obter mais informações, consulte o artigo [Centro de transferências: Assistente para IT profissionais RTW do Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Como instalar o módulo de gestão de direitos de administração

1.  Aceda ao Center Download Microsoft e [Transfira a ferramenta de administração do Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721), que contém o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] módulo de administração para o Windows PowerShell.

2.  A partir da pasta local em que é transferido e guardado o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] instalador de ficheiros, faça duplo clique no ficheiro executável que transferiu para a plataforma (WindowsAzureADRightsManagementAdministration_x64 ou WindowsAzureADRightsManagementAdministration_x86.exe) para iniciar o Azure AD Rights Management administração Assistente de configuração.

3.  Conclua o assistente.

O Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] está agora instalado.

## Próximos passos
Para ver os cmdlets estão disponíveis, inicie o Windows PowerShell com o **Executar como administrador** opção e escreva o seguinte:

```
Get-Command -Module aadrm
```
Utilize `the Get-Help <cmdlet_name>` comando para ver a ajuda para um cmdlet específico.

Para obter mais informações:

-   Lista completa dos cmdlets disponíveis: [Cmdlets de gestão de direitos do Azure](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Lista dos cenários de configuração principal, que suporta o Windows PowerShell: [Administrar o Azure Rights Management utilizando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Antes de poder executar os comandos que configurem o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] serviço, tem de ligar ao serviço, utilizando o [Ligar AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet. Quando terminar de executar os comandos de configuração que pretende, desligar do serviço, utilizando o [Desligar AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet.

> [!NOTE]
> Se ainda não ativado [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], pode fazê-depois de ligar ao serviço, utilizando o [Ativar Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) cmdlet.

## Consultar Também
[Administrar o Azure Rights Management utilizando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

