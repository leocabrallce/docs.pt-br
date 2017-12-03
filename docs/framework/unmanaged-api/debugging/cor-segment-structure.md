---
title: Estrutura COR_SEGMENT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc7a749f92149d7f0f5725aec6d90d72e0582c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="0c2df-102">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="0c2df-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="0c2df-103">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c2df-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c2df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c2df-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="0c2df-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0c2df-105">Members</span></span>  
  
|<span data-ttu-id="0c2df-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0c2df-106">Member</span></span>|<span data-ttu-id="0c2df-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c2df-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="0c2df-108">O endereço inicial da região de memória.</span><span class="sxs-lookup"><span data-stu-id="0c2df-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="0c2df-109">O endereço final da região de memória.</span><span class="sxs-lookup"><span data-stu-id="0c2df-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="0c2df-110">Um [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) membro de enumeração que indica a geração da região de memória.</span><span class="sxs-lookup"><span data-stu-id="0c2df-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="0c2df-111">O número de heap no qual reside a região de memória.</span><span class="sxs-lookup"><span data-stu-id="0c2df-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="0c2df-112">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0c2df-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c2df-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c2df-113">Remarks</span></span>  
 <span data-ttu-id="0c2df-114">O `COR_SEGMENTS` estrutura representa uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c2df-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="0c2df-115">`COR_SEGMENTS`objetos são membros de [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de coleção, que é preenchido com a chamada a[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0c2df-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="0c2df-116">O `heap` campo é o número de processadores, que corresponde ao heap está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="0c2df-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="0c2df-117">Para Coletores de lixo de estação de trabalho, seu valor é sempre zero, como estações de trabalho têm apenas um heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0c2df-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="0c2df-118">Para Coletores de lixo do servidor, seu valor corresponde ao processador de que heap está associado.</span><span class="sxs-lookup"><span data-stu-id="0c2df-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="0c2df-119">Observe que pode haver mais ou menos a coleta de lixo heaps que o número de processadores reais devido a detalhes de implementação do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="0c2df-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c2df-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c2df-120">Requirements</span></span>  
 <span data-ttu-id="0c2df-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c2df-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c2df-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c2df-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c2df-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c2df-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c2df-124">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c2df-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c2df-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c2df-125">See Also</span></span>  
 [<span data-ttu-id="0c2df-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="0c2df-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="0c2df-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="0c2df-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)