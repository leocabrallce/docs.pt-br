---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a>ICorDebugFrame Interface1
Representa um quadro na pilha atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Obtém um ICorDebugStepper para executar operações de revisão em relação a esse `ICorDebugFrame`.|  
|[Método GetCallee](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Obtém um ponteiro para o `ICorDebugFrame` da cadeia atual que este quadro chamado ou retorna null se esse é o quadro interno na cadeia.|  
|[Método GetCaller](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Obtém um ponteiro para o `ICorDebugFrame` da atual cadeia que chamadas a este quadro ou retorna null se esse é o quadro externo da cadeia.|  
|[Método GetChain](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Obtém um ponteiro para o ICorDebugChain isso `ICorDebugFrame` faz parte.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Obtém um ponteiro para o ICorDebugCode associado deste quadro de pilhas.|  
|[Método GetFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Obtém um ponteiro para o ICorDebugFunction que contém o código associado deste quadro de pilhas.|  
|[Método GetFunctionToken](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Obtém o token de metadados para a função que contém o código associado deste quadro de pilhas.|  
|[Método GetStackRange](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Obtém o intervalo de endereço absoluto do quadro de pilhas representado por esse `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
