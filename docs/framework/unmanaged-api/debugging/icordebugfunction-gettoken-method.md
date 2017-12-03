---
title: "Método ICorDebugFunction::GetToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 010cd1f4cf5886859ffe66275c7f2173408e28fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="c61a2-102">Método ICorDebugFunction::GetToken</span><span class="sxs-lookup"><span data-stu-id="c61a2-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="c61a2-103">Obtém os metadados de token para essa função.</span><span class="sxs-lookup"><span data-stu-id="c61a2-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c61a2-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c61a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c61a2-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="c61a2-106">[out] Um ponteiro para um `mdMethodDef` token que referencia os metadados para essa função.</span><span class="sxs-lookup"><span data-stu-id="c61a2-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c61a2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c61a2-107">Requirements</span></span>  
 <span data-ttu-id="c61a2-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61a2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c61a2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c61a2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c61a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c61a2-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>