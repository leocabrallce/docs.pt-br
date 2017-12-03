---
title: "Método ICLRRuntimeInfo::IsStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsStarted
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6bcaf6e0d10bd935e7ba4a2bb79941be1af6950
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="9bc55-102">Método ICLRRuntimeInfo::IsStarted</span><span class="sxs-lookup"><span data-stu-id="9bc55-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="9bc55-103">Indica se o tempo de execução foi iniciado (ou seja, se o [método Iclrruntimehost::](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) foi chamado e teve êxito).</span><span class="sxs-lookup"><span data-stu-id="9bc55-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bc55-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bc55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bc55-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="9bc55-106">[out] `true` se esse tempo de execução for iniciada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="9bc55-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="9bc55-107">[out] Retorna os sinalizadores que foram usados para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9bc55-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bc55-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9bc55-108">Return Value</span></span>  
 <span data-ttu-id="9bc55-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="9bc55-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9bc55-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bc55-110">HRESULT</span></span>|<span data-ttu-id="9bc55-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bc55-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bc55-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bc55-112">S_OK</span></span>|<span data-ttu-id="9bc55-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="9bc55-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9bc55-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9bc55-114">E_NOTIMPL</span></span>|<span data-ttu-id="9bc55-115">A versão de runtime (CLR) de linguagem comum é anterior à versão do CLR no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bc55-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bc55-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bc55-116">Remarks</span></span>  
 <span data-ttu-id="9bc55-117">Esse método funciona com CLR versões anteriores à versão de CLR no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bc55-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc55-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bc55-118">Requirements</span></span>  
 <span data-ttu-id="9bc55-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bc55-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc55-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9bc55-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9bc55-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9bc55-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bc55-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc55-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc55-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bc55-123">See Also</span></span>  
 [<span data-ttu-id="9bc55-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="9bc55-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="9bc55-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9bc55-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9bc55-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9bc55-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)