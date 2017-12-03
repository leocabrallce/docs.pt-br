---
title: "Método ICorDebugInstanceFieldSymbol::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 364144dcef21e7e9c058cb0317970a273aa8ecac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="b9b41-102">Método ICorDebugInstanceFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="b9b41-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="b9b41-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="b9b41-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9b41-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9b41-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9b41-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="b9b41-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="b9b41-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9b41-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9b41-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9b41-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b9b41-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b41-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9b41-109">Requirements</span></span>  
 <span data-ttu-id="b9b41-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b41-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b41-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9b41-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9b41-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9b41-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b41-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b41-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b41-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9b41-114">See Also</span></span>  
 [<span data-ttu-id="b9b41-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b9b41-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="b9b41-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="b9b41-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)