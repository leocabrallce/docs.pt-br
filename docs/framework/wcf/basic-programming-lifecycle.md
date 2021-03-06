---
title: "Ciclo de vida de programação básica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a>Ciclo de vida de programação básica
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]permite que aplicativos se comuniquem se estiverem no mesmo computador, através da Internet, ou em diferentes plataformas de aplicativo. Este tópico descreve as tarefas que são necessárias para criar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo. Para um aplicativo de exemplo de funcionamento, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>As tarefas básicas  
 As tarefas básicas para executar são, em ordem:  
  
1.  Defina o contrato de serviço. Um contrato de serviço Especifica a assinatura de um serviço, os dados trocados por ele e outros dados necessários ao contrato. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implemente o contrato. Para implementar um contrato de serviço, crie uma classe que implementa o contrato e especificar comportamentos personalizados deve ter o tempo de execução. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Configure o serviço especificando pontos de extremidade e outras informações de comportamento. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Configurando serviços](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hospede o serviço. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Crie um aplicativo cliente. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Criação de clientes](../../../docs/framework/wcf/building-clients.md).  
  
 Embora os tópicos nesta seção siga esta ordem, alguns cenários não começar do início. Por exemplo, se você quiser criar um cliente para um serviço preexistente, você começa com a etapa 5. Ou, se você estiver criando um serviço que outras pessoas usarão, você pode ignorar a etapa 5.  
  
 Quando você estiver familiarizado com o desenvolvimento de contratos de serviço, você também pode ler [Introdução à extensibilidade](../../../docs/framework/wcf/introduction-to-extensibility.md). Se você tiver problemas com seu serviço, verifique [início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) para ver se outras pessoas tenham problemas iguais ou semelhantes.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
