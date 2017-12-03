---
title: "Método ICorDebugStepper::Step"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 914773adefd2ed4c1aa98310fd27a0cbc829bf49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="62f6b-102">Método ICorDebugStepper::Step</span><span class="sxs-lookup"><span data-stu-id="62f6b-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="62f6b-103">Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e, opcionalmente, para continuar a depuração único por meio das funções que são chamadas de dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="62f6b-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62f6b-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62f6b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="62f6b-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="62f6b-106">[in] Definido como `true` para entrar em uma função que é chamada no thread.</span><span class="sxs-lookup"><span data-stu-id="62f6b-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="62f6b-107">Definido como `false` ao passar sobre a função.</span><span class="sxs-lookup"><span data-stu-id="62f6b-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f6b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="62f6b-108">Remarks</span></span>  
 <span data-ttu-id="62f6b-109">A etapa é concluída quando o common language runtime executa a próxima instrução gerenciada no quadro deste seletor.</span><span class="sxs-lookup"><span data-stu-id="62f6b-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="62f6b-110">Se `Step` é chamado em um seletor, que não está no código gerenciado, a etapa será concluída quando a próxima instrução do código gerenciado é executada pelo thread.</span><span class="sxs-lookup"><span data-stu-id="62f6b-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f6b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62f6b-111">Requirements</span></span>  
 <span data-ttu-id="62f6b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f6b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f6b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62f6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62f6b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f6b-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>