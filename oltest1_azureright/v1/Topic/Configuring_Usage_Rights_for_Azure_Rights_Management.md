---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Configura&#231;&#227;o de direitos de utiliza&#231;&#227;o para o Azure Rights Management
Quando definir a proteção em ficheiros ou mensagens de correio eletrónico utilizando o Azure Rights Management (RMS do Azure) e não utiliza um modelo, terá de configurar os direitos de utilização-la sozinho. Além disso, quando configurar os modelos personalizados para o Azure RMS, selecione os direitos de utilização que serão, em seguida, automaticamente aplicados quando está selecionado o modelo por utilizadores, os administradores, ou configurados serviços. Por exemplo, no portal do Azure pode selecionar as funções que configurar um agrupamento lógico de direitos de utilização, ou pode configurar os direitos individuais.

Utilize este tópico para o ajudar a configurar os direitos de utilização que pretende para a aplicação que estiver a utilizar e compreender como estes direitos são interpretados por aplicações.

## Direitos de utilização e as descrições
A tabela seguinte apresenta e descreve os direitos de utilização que suporta a gestão de direitos e como são utilizadas e interpretados. Nesta tabela, o **nome comum** é, geralmente, que poderá ver a utilização da direita apresentado ou referenciada, como uma versão mais amigável do word único valor que é utilizado no código (o **codificação na política** valor). O **constante de API ou valor** é o nome SDK para uma chamada de MSIPC API utilizada quando escreve uma aplicação suportadas por RMS que verifica a existência de um direita de utilização ou adiciona uma utilização da direita para a uma política.

|Nome comum|Codificação de política|Descrição|Implementação no direitos personalizados do Office|O nome no portal do Azure|Atribua o nome modelos de AD RMS|Constante de API ou valor|Informações adicionais|
|--------------|---------------------------|-------------|------------------------------------------------------|-----------------------------|------------------------------------|-----------------------------|--------------------------|
|Edite conteúdos, editar|DOCEDIT|Permite ao utilizador modificar, reorganizar, formatar ou filtrar o conteúdo dentro da aplicação. -Lo que não conceda o direito de guardar a cópia editada.|Como parte de **alteração** e **controlo total** opções.|**Editar conteúdo**|**Editar**|Não aplicável|Nas aplicações do Office, este direito também permite ao utilizador guardar o documento.|
|Guardar|EDITAR|Permite ao utilizador guardar o documento na sua localização atual.|Como parte de **alteração** e **controlo total** opções.|**Guarde o ficheiro**|**Guardar**|IPC_GENERIC_WRITEL "EDITAR"|Nas aplicações do Office, este direito também permite ao utilizador modificar o documento.|
|Comentário|COMENTÁRIO|Ativa a opção Adicionar comentários ou anotações para o conteúdo.|Não implementado|Não implementado|Não implementado|IPC_GENERIC_COMMENTL "COMENTÁRIO"|Este direito está disponível no SDK, está disponível como uma política ad-hoc no módulo proteção RMS para o Windows PowerShell e tenha sido implementado no algumas aplicações de fornecedor de software. No entanto, não é amplamente utilizado e não é atualmente suportado por aplicações do Office.|
|Guardar como, exportar|EXPORTAR|Ativa a opção Guardar o conteúdo para um nome de ficheiro diferente (Guardar como). Dependendo da aplicação, o ficheiro poderão ser guardado sem proteção.|Como parte de **alteração** e **controlo total** opções.|**Exportar conteúdo (Guardar como)**|**Exportação (Guardar como)**|IPC_GENERIC_EXPORTL "EXPORTAÇÃO"|Este direito também permite ao utilizador efetuar outras opções de exportação em aplicações, tais como **Enviar para o OneNote**.|
|Reencaminhar|REENCAMINHAR|Ativa a opção para reencaminhar uma mensagem de correio eletrónico e adicionar os destinatários a **para** e **Cc** linhas.|Negado ao utilizar o **não reencaminhar** política padrão.|**Reencaminhar**|**Reencaminhar**|IPC_EMAIL_FORWARDL "REENCAMINHAR"|Não permitir que o reencaminhador conceder direitos para outros utilizadores como parte da ação reencaminhar.|
|Controlo total|PROPRIETÁRIO|Concede todos os direitos para o documento e podem ser efetuadas a todas as ações disponíveis.|Como o **controlo total** opção personalizado.|**Controlo total**|**Controlo total**|IPC_GENERIC_ALLL "PROPRIETÁRIO"|Inclui a capacidade para remover a proteção.|
|Imprimir|IMPRIMIR|Permite que as opções imprimir o conteúdo.|Como o **Imprimir conteúdo** opção na permissões personalizadas. Não é uma definição de por destinatário.|**Imprimir**|**Imprimir**|IPC_GENERIC_PRINTL "IMPRIMIR|Não existem informações adicionais|
|Resposta|RESPOSTA|Ativa a opção de resposta no cliente de e-mail, sem permitir alterações a **para** ou **Cc** linhas.|Não aplicável|**Resposta**|**Resposta**|IPC_EMAIL_REPLY|Não existem informações adicionais|
|Responder a todos|REPLYALL|Permite a **responder a todos** opção um cliente de e-mail, mas não permitir que o utilizador adicionar destinatários para o **para** ou **Cc** linhas.|Não aplicável|**Responder a todos**|**Responder a todos**|IPC_EMAIL_REPLYALLL "REPLYALL"|Não existem informações adicionais|
|Vista, abrir, leitura|VISTA|Permite ao utilizador abrir o documento e ver o conteúdo.|Como o **leitura** política personalizada, **vista** opção.|**Visualização de conteúdo**|**Vista**|IPC_GENERIC_READL "VISTA"|Não existem informações adicionais|
|Copiar|EXTRAIR|Permite que as opções copiar dados do documento para o mesmo livro ou de outro documento.|Como o **Permitir que os utilizadores com acesso de leitura copiar o conteúdo** opção política personalizada.|**Copiar e extrair conteúdo**|**Extrair**|IPC_GENERIC_EXTRACTL "EXTRAIR"|Em algumas aplicações também permite a todo o documento seja guardado no formulário não protegido.|
|Direitos de vista|VIEWRIGHTSDATA|Permite ao utilizador ver a política que é aplicada ao documento.|Não implementado|**Vista direitos atribuídos**|**Direitos de vista**|IPC_READ_RIGHTSL "VIEWRIGHTSDATA"|Ignorado pelo algumas aplicações.|
|Direitos de alteração|EDITRIGHTSDATA|Permite ao utilizador alterar a política é aplicada ao documento. Inclui incluindo remover a proteção.|Não implementado|**Direitos de alteração**|**Editar direitos**|IPC_WRITE_RIGHTSL "EDITRIGHTSDATA"|Não existem informações adicionais|
|Permitir que as Macros|OBJMODEL|Ativa a opção executar macros ou efetuar outro acesso programático ou remoto ao conteúdo num documento.|Como o **Permitir acesso programático** opção política personalizada. Não é uma definição de por destinatário.|**Permitir que as Macros**|**Permitir que as Macros**|Não aplicável|Não existem informações adicionais|

## Direitos incluídos nos níveis de permissões
Algumas aplicações agrupam direitos de utilização em níveis de permissões, para facilitar a selecione direitos de utilização que são normalmente utilizados em conjunto. Estes níveis de permisisons ajudá-lo para abstrair um nível de complexidade dos utilizadores, pelo que podem escolher as opções de baseada em funções.  Por exemplo, **Revisor** e **Cocriar**. Embora frequentemente estas opções mostram aos utilizadores um resumo dos direitos, estes podem não incluir todas as direita que se encontra listada na tabela anterior.

Utilize a tabela seguinte para obter uma lista destes níveis de permissões e uma lista completa dos direitos que contêm.

|Nível de permissões|Aplicações|Direitos incluídos (nome comum)|
|-----------------------|--------------|-----------------------------------|
|Visualizador|Portal do Azure<br /><br />Aplicações para Windows de partilha Rights Management|Vista, abrir, leitura<br /><br />Resposta<br /><br />Responder a todos|
|Revisor|Portal do Azure<br /><br />Aplicações para Windows de partilha Rights Management|Vista, abrir, leitura<br /><br />Guardar<br /><br />Edite conteúdos, editar<br /><br />Reply<sup>*</sup><br /><br />Responder a todos<sup>*</sup><br /><br />Reencaminhar<sup>*</sup>|
|Cocriar|Portal do Azure<br /><br />Aplicações para Windows de partilha Rights Management|Vista, abrir, leitura<br /><br />Guardar<br /><br />Edite conteúdos, editar<br /><br />Copiar<br /><br />Direitos de vista<br /><br />Direitos de alteração<br /><br />Permitir que as Macros<br /><br />Guardar como, exportar<br /><br />Imprimir<br /><br />Reply<sup>*</sup><br /><br />Responder a todos<sup>*</sup><br /><br />Reencaminhar<sup>*</sup>|
|Coproprietário|Portal do Azure<br /><br />Aplicações para Windows de partilha Rights Management|Vista, abrir, leitura<br /><br />Guardar<br /><br />Edite conteúdos, editar<br /><br />Copiar<br /><br />Direitos de vista<br /><br />Direitos de alteração<br /><br />Permitir que as Macros<br /><br />Guardar como, exportar<br /><br />Imprimir<br /><br />Reply<sup>*</sup><br /><br />Responder a todos<sup>*</sup><br /><br />Reencaminhar<sup>*</sup><br /><br />Controlo total|
<sup>*</sup> Não aplicável para a aplicação partilha Rights Management para Windows

## Direitos incluídos nos modelos predefinidos
Os direitos que estão incluídos os modelos predefinidos são os seguintes:

|Nome a apresentar|Direitos incluídos (nome comum)|
|---------------------|-----------------------------------|
|&lt; nome da organização &gt; - apenas visualização confidencial|Vista, abrir, leitura|
|&lt; nome da organização &gt; - confidencial|Vista, abrir, leitura<br /><br />Guardar<br /><br />Edite conteúdos, editar<br /><br />Direitos de vista<br /><br />Permitir que as Macros<br /><br />Reencaminhar<br /><br />Resposta<br /><br />Responder a todos|

## Consultar Também
[Configurar a gestão de direitos do Azure](../Topic/Configuring_Azure_Rights_Management.md)

