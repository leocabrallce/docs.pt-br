---
title: "Método ICorDebugAppDomain::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="3c0f8-102">Método ICorDebugAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="3c0f8-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="3c0f8-103">Obtém o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c0f8-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c0f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c0f8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3c0f8-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="3c0f8-107">Defina esse valor como zero para colocar esse método no modo de consulta.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3c0f8-108">[out] Um ponteiro para o tamanho do nome ou o número de caracteres de fato retornadas em `szName`.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="3c0f8-109">No modo de consulta, esse valor permite que o chamador saiba grande como um buffer para alocar para o nome.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="3c0f8-110">[out] Uma matriz que armazena o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c0f8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c0f8-111">Remarks</span></span>  
 <span data-ttu-id="3c0f8-112">Um depurador chama o `GetName` método uma vez para obter o tamanho de um buffer necessário para o nome.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="3c0f8-113">O depurador aloca o buffer e, em seguida, chama o método uma segunda vez para preencher o buffer.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="3c0f8-114">A primeira chamada para obter o tamanho do nome é conhecida como *o modo de consulta*.</span><span class="sxs-lookup"><span data-stu-id="3c0f8-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0f8-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c0f8-115">Requirements</span></span>  
 <span data-ttu-id="3c0f8-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0f8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0f8-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c0f8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c0f8-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c0f8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c0f8-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0f8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>