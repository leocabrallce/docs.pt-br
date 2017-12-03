---
title: "Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="cfd4f-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="cfd4f-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="cfd4f-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="cfd4f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="cfd4f-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento de thread e windows.</span><span class="sxs-lookup"><span data-stu-id="cfd4f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd4f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfd4f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfd4f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfd4f-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="cfd4f-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cfd4f-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="cfd4f-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="cfd4f-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="cfd4f-109">Um ponteiro para um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="cfd4f-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="cfd4f-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="cfd4f-110">ppForwarder</span></span>  
 <span data-ttu-id="cfd4f-111">Um ponteiro para o endereço de um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="cfd4f-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd4f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfd4f-112">Requirements</span></span>  
 <span data-ttu-id="cfd4f-113">**Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd4f-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd4f-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="cfd4f-114">**DLL:**</span></span>  
  
 <span data-ttu-id="cfd4f-115">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="cfd4f-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="cfd4f-116">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="cfd4f-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="cfd4f-117">**Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd4f-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd4f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfd4f-118">See Also</span></span>  
 [<span data-ttu-id="cfd4f-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="cfd4f-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)