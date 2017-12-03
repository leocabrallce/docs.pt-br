---
title: "Método IMetaDataImport::GetPropertyProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc3a1ce1d07bda50b2b578e7d20870324d60edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="6757e-102">Método IMetaDataImport::GetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="6757e-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="6757e-103">Obtém os metadados da propriedade representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="6757e-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6757e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6757e-104">Syntax</span></span>  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6757e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6757e-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="6757e-106">[in] Um token que representa a propriedade para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="6757e-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="6757e-107">[out] Um ponteiro para o token de TypeDef que representa o tipo que implementa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="6757e-108">[out] Um buffer para armazenar o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="6757e-109">[in] O tamanho em caracteres largos de `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="6757e-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="6757e-110">[out] O número de caracteres largos retornados em `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="6757e-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="6757e-111">[out] Um ponteiro para os sinalizadores de atributo aplicado à propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="6757e-112">Esse valor é um bitmask do [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="6757e-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="6757e-113">[out] Um ponteiro para a assinatura de metadados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="6757e-114">[out] O número de bytes retornados em `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="6757e-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="6757e-115">[out] Um sinalizador que especifica o tipo de constante que é o valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="6757e-116">Esse valor é da enumeração CorElementType.</span><span class="sxs-lookup"><span data-stu-id="6757e-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="6757e-117">[out] Um ponteiro para os bytes que armazena o valor padrão para essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="6757e-118">[out] O tamanho em caracteres largos de `ppDefaultValue`, se `pdwCPlusTypeFlag` é ELEMENT_TYPE_STRING; caso contrário, esse valor não é relevante.</span><span class="sxs-lookup"><span data-stu-id="6757e-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="6757e-119">Nesse caso, o comprimento de `ppDefaultValue` é inferido do tipo especificado pelo `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="6757e-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="6757e-120">[out] Um ponteiro para o token MethodDef que representa o método de acessador set da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="6757e-121">[out] Um ponteiro para o token MethodDef que representa o método de acessador get da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="6757e-122">[out] Uma matriz de MethodDef tokens que representam os outros métodos associados à propriedade.</span><span class="sxs-lookup"><span data-stu-id="6757e-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6757e-123">[in] O tamanho máximo da `rmdOtherMethod` matriz.</span><span class="sxs-lookup"><span data-stu-id="6757e-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="6757e-124">Se você não fornecer uma matriz grande o suficiente para manter todos os métodos, eles serão ignorados sem aviso.</span><span class="sxs-lookup"><span data-stu-id="6757e-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="6757e-125">[out] O número de tokens de MethodDef retornados em `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="6757e-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6757e-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6757e-126">Requirements</span></span>  
 <span data-ttu-id="6757e-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6757e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6757e-128">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6757e-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6757e-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6757e-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6757e-130">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6757e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6757e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6757e-131">See Also</span></span>  
 [<span data-ttu-id="6757e-132">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6757e-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6757e-133">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6757e-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)