---
title: "Método ICLRPolicyManager::SetTimeoutAndAction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeoutAndAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a15454e1cea29e3c0025797633f22e9e18554347
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="77284-102">Método ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="77284-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="77284-103">Define um valor de tempo limite para a operação especificada e especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a operação.</span><span class="sxs-lookup"><span data-stu-id="77284-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77284-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77284-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77284-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77284-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="77284-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação para o qual definir o tempo limite e política `action`.</span><span class="sxs-lookup"><span data-stu-id="77284-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="77284-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="77284-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="77284-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="77284-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="77284-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="77284-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="77284-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="77284-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="77284-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="77284-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="77284-112">[in] O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="77284-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="77284-113">Um valor infinito causas `operation` nunca exceda o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="77284-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="77284-114">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, indicando que o CLR deve ser executada quando a ação da política `operation` ocorre.</span><span class="sxs-lookup"><span data-stu-id="77284-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77284-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="77284-115">Return Value</span></span>  
  
|<span data-ttu-id="77284-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77284-116">HRESULT</span></span>|<span data-ttu-id="77284-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="77284-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77284-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="77284-118">S_OK</span></span>|<span data-ttu-id="77284-119">`SetTimeoutAndAction`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="77284-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="77284-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77284-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77284-121">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="77284-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77284-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77284-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77284-123">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="77284-123">The call timed out.</span></span>|  
|<span data-ttu-id="77284-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77284-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77284-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="77284-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77284-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77284-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77284-127">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="77284-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77284-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77284-128">E_FAIL</span></span>|<span data-ttu-id="77284-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="77284-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77284-130">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="77284-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77284-131">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77284-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77284-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="77284-132">E_INVALIDARG</span></span>|<span data-ttu-id="77284-133">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `action`.</span><span class="sxs-lookup"><span data-stu-id="77284-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77284-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="77284-134">Remarks</span></span>  
 <span data-ttu-id="77284-135">`SetTimeoutAndAction`encapsula os recursos do [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) e [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) métodos e pode ser chamado em vez de sequenciais chamadas para esses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="77284-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77284-136">Nem todos os valores da política de ação podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="77284-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="77284-137">Consulte as seções de comentários dos tópicos para esses dois métodos para os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="77284-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77284-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77284-138">Requirements</span></span>  
 <span data-ttu-id="77284-139">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77284-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77284-140">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77284-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77284-141">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77284-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77284-142">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77284-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77284-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77284-143">See Also</span></span>  
 [<span data-ttu-id="77284-144">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="77284-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="77284-145">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="77284-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="77284-146">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="77284-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="77284-147">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="77284-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="77284-148">ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="77284-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)