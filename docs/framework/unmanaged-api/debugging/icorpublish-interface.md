---
title: Interface ICorPublish
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8eb3bd2da9529a681f7f3a09ef7eb78c776cc302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="bb121-102">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="bb121-102">ICorPublish Interface</span></span>
<span data-ttu-id="bb121-103">Serve como a interface geral para publicar informações sobre os processos e informações sobre os domínios de aplicativo nesses processos.</span><span class="sxs-lookup"><span data-stu-id="bb121-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb121-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bb121-104">Methods</span></span>  
  
|<span data-ttu-id="bb121-105">Método</span><span class="sxs-lookup"><span data-stu-id="bb121-105">Method</span></span>|<span data-ttu-id="bb121-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb121-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb121-107">Método EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="bb121-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="bb121-108">Obtém um [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instância que contém os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="bb121-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="bb121-109">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="bb121-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="bb121-110">Obtém um [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instância que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="bb121-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb121-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb121-111">Requirements</span></span>  
 <span data-ttu-id="bb121-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb121-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb121-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="bb121-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bb121-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb121-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb121-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb121-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb121-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb121-116">See Also</span></span>  
 [<span data-ttu-id="bb121-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="bb121-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bb121-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="bb121-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)