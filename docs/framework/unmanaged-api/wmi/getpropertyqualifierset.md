---
title: "Função GetPropertyQualifierSet (referência de API não gerenciada)"
description: "A função GetPropertyQualifierSet recupera o qualificador definido para uma propriedade."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd8abdb34f37273e469bdf5fc659b261bb2b9304
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="a15eb-103">Função GetPropertyQualifierSet</span><span class="sxs-lookup"><span data-stu-id="a15eb-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="a15eb-104">Recupera o qualificador definido para uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="a15eb-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a15eb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a15eb-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="a15eb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a15eb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a15eb-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="a15eb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a15eb-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="a15eb-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="a15eb-109">[in] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a15eb-109">[in] The property  name.</span></span> <span data-ttu-id="a15eb-110">`wszProperty`deve apontar para um válida `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="a15eb-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="a15eb-111">[out] Recebe o ponteiro de interface que permite acessar os qualificadores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a15eb-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="a15eb-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="a15eb-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="a15eb-113">Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="a15eb-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a15eb-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a15eb-114">Return value</span></span>

<span data-ttu-id="a15eb-115">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="a15eb-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a15eb-116">Constante</span><span class="sxs-lookup"><span data-stu-id="a15eb-116">Constant</span></span>  |<span data-ttu-id="a15eb-117">Valor</span><span class="sxs-lookup"><span data-stu-id="a15eb-117">Value</span></span>  |<span data-ttu-id="a15eb-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a15eb-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a15eb-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a15eb-119">0x80041001</span></span> | <span data-ttu-id="a15eb-120">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="a15eb-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="a15eb-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a15eb-121">0x80041002</span></span> | <span data-ttu-id="a15eb-122">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="a15eb-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a15eb-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a15eb-123">0x80041006</span></span> | <span data-ttu-id="a15eb-124">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="a15eb-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a15eb-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a15eb-125">0x80041008</span></span> | <span data-ttu-id="a15eb-126">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="a15eb-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="a15eb-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="a15eb-127">0x80041030</span></span> | <span data-ttu-id="a15eb-128">A função tenta obter qualificadores de uma propriedade de sistema.</span><span class="sxs-lookup"><span data-stu-id="a15eb-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a15eb-129">0</span><span class="sxs-lookup"><span data-stu-id="a15eb-129">0</span></span> | <span data-ttu-id="a15eb-130">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a15eb-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a15eb-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a15eb-131">Remarks</span></span>

<span data-ttu-id="a15eb-132">Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="a15eb-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="a15eb-133">Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="a15eb-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="a15eb-134">Manipulação de método não está disponível para [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="a15eb-134">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="a15eb-135">Como cada método pode ter seus próprio qualificadores de [IWbemQualifierSet ponteiro](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permite que o chamador adicionar, editar ou excluir esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="a15eb-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="a15eb-136">Como as propriedades de sistema não ter nenhum qualificador, a função retorna `WBEM_E_SYSTEM_PROPERTY` se você tentar obter um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) ponteiro para uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="a15eb-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="a15eb-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a15eb-137">Requirements</span></span>  
<span data-ttu-id="a15eb-138">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a15eb-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15eb-139">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a15eb-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a15eb-140">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a15eb-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a15eb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a15eb-141">See also</span></span>  
[<span data-ttu-id="a15eb-142">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="a15eb-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)