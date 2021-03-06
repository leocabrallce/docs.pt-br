---
title: "Visão geral de correlação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a29f761b4a3718293c1786d23d425265603f8c84
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="correlation-overview"></a>Visão geral de correlação
Correlação é o mecanismo para relacionar as mensagens do serviço de fluxo de trabalho para outro ou para o estado de instância de aplicativo, como uma resposta a uma solicitação inicial ou uma ID de ordem específica para o estado persistente de um fluxo de trabalho de processamento de pedidos. Este tópico fornece uma visão geral de correlação. Os outros tópicos nesta seção fornecem informações adicionais para cada tipo de correlação.  
  
## <a name="types-of-correlation"></a>Tipos de correlação  
 Correlação pode ser baseada em conteúdo ou protocolo. Com base no protocolo correlações usam dados fornecidos pela infraestrutura de entrega de mensagem para fornecer mapeamento entre as mensagens. As mensagens que são correlacionadas usando correlação baseada no protocolo estão relacionadas entre si usando um objeto na memória, como um <xref:System.ServiceModel.Channels.RequestContext>, ou por um token fornecido pelo protocolo de transporte. Com base em conteúdo correlações relacionam mensagens entre si usando dados de aplicativo especificado. As mensagens que são correlacionadas usando correlação baseada em conteúdo estão relacionadas uns aos outros por alguns dados de aplicativo definido na mensagem, como um número de cliente.  
  
 Atividades que participam de correlação use um <xref:System.ServiceModel.Activities.CorrelationHandle> para unir as atividades de mensagens. Por exemplo, um <xref:System.ServiceModel.Activities.Send> que é usada para chamar um serviço e um subsequentes <xref:System.ServiceModel.Activities.Receive> que é usado para receber um retorno de chamada do serviço, compartilham o mesmo <xref:System.ServiceModel.Activities.CorrelationHandle>. Esse padrão básico é usado se a correlação é conteúdo com base ou baseado no protocolo. O identificador de correlação pode ser explicitamente definido em cada atividade ou as atividades podem estar contidas em um <xref:System.ServiceModel.Activities.CorrelationScope> atividade. Atividades contidas em uma <xref:System.ServiceModel.Activities.CorrelationScope> têm seus identificadores de correlação gerenciados pelo <xref:System.ServiceModel.Activities.CorrelationScope> e não exigem o <xref:System.ServiceModel.Activities.CorrelationHandle> a ser definido explicitamente. Um <xref:System.ServiceModel.Activities.CorrelationScope> escopo fornece <xref:System.ServiceModel.Activities.CorrelationHandle> gerenciamento para uma correlação de solicitação-resposta e um tipo de correlação adicionais. Serviços de fluxo de trabalho hospedados usando <xref:System.ServiceModel.Activities.WorkflowServiceHost> têm o mesmo gerenciamento correlação padrão como o <xref:System.ServiceModel.Activities.CorrelationScope> atividade. Este gerenciamento de correlação padrão geralmente significa que em muitos cenários, mensagens de atividades em um <xref:System.ServiceModel.Activities.CorrelationScope> ou um serviço de fluxo de trabalho não exigem seus <xref:System.ServiceModel.Activities.CorrelationHandle> definido a menos que tenha várias atividades de mensagens em paralelo ou se sobrepõem, como dois <xref:System.ServiceModel.Activities.Receive> atividades em paralelo ou dois <xref:System.ServiceModel.Activities.Send> atividades seguido por dois <xref:System.ServiceModel.Activities.Receive> atividades. Para obter mais informações sobre a correlação padrão são fornecidas nos tópicos desta seção abrangem cada tipo específico de correlação. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]atividades de mensagens consulte [atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md) e [como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md).  
  
## <a name="protocol-based-correlation"></a>Correlação baseada no protocolo  
 Correlação baseada no protocolo usa o mecanismo de transporte para relacionar as mensagens entre si e com a instância apropriada. Alguns correlações protocolo fornecido pelo sistema incluem a correlação de solicitação-resposta e correlação baseada em contexto. Uma correlação de solicitação-resposta é usada para correlacionar um único par de atividades de mensagem para formar uma operação bidirecional, como um <xref:System.ServiceModel.Activities.Send> emparelhado com um <xref:System.ServiceModel.Activities.ReceiveReply>, ou um <xref:System.ServiceModel.Activities.Receive> emparelhado com um <xref:System.ServiceModel.Activities.SendReply>. O [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Designer de fluxo de trabalho também fornece um conjunto de modelos de atividade de rapidamente implementar esse padrão. Uma correlação baseada em contexto baseia-se o mecanismo de troca de contexto descrito o [especificação do protocolo de troca de contexto de .NET](http://go.microsoft.com/fwlink/?LinkID=166059). Para usar a correlação baseada em contexto, uma com base em contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> ou <xref:System.ServiceModel.NetTcpContextBinding> deve ser usado no ponto de extremidade.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]correlação de protocolo, consulte [intercâmbio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md), [Duplex durável](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md), e [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] modelos de atividade do Designer de fluxo de trabalho, consulte [atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md). Para obter o código de exemplo, consulte o [Duplex durável &#91; Exemplos de WF &#93; ](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md) e [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) exemplos.  
  
## <a name="content-based-correlation"></a>Correlação conteudo base  
 Correlação baseada em conteúdo usa alguma informação na mensagem para associá-la a uma determinada instância. Ao contrário de correlação baseada no protocolo, correlação baseada em conteúdo requer o autor do aplicativo declarar explicitamente onde esses dados podem ser encontrados em cada mensagem relacionada. As atividades que usam a correlação baseada em conteúdo especificar esses dados de mensagem usando um <xref:System.ServiceModel.MessageQuerySet>. Correlação baseada em conteúdo é útil ao se comunicar com os serviços que não usam uma das ligações de contexto, como <xref:System.ServiceModel.BasicHttpContextBinding>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]correlação baseada em conteúdo, consulte [baseada em conteúdo](../../../../docs/framework/wcf/feature-details/content-based-correlation.md). Para obter o código de exemplo, consulte o [correlação baseada em conteúdo](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md) e [Calculadora correlacionada](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [Correlação baseada em conteúdo](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [Calculadora correlacionada](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)  
 [Frente e verso durável &#91; Exemplos de WF &#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)  
 [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)
