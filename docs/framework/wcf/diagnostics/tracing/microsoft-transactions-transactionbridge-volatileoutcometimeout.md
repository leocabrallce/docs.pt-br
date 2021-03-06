---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1385995165308cb1c2f2e6bd6c8a800a88b7b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
O serviço de protocolo WS-AT atingiu o tempo limite aguardando uma resposta a uma mensagem de resultado de um participante volátil. O resultado da transação pode ser em dúvida se o participante retornar.  
  
## <a name="description"></a>Descrição  
 Rastreada quando um participante volátil decidiu confirmação ou anulação, mas não respondeu a uma solicitação de confirmação ou reversão em um determinado período de tempo.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Certifique-se de que todos os participantes voláteis são capazes de responder dentro de determinado período de tempo. Período o padrão é 180 segundos.  Se isso for insuficiente, aumente o `VolatileOutcomeDelay` política de timer para WS-AT.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
