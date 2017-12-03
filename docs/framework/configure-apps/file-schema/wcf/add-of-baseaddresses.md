---
title: '&lt;adicionar&gt; &lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="d4db2-102">&lt;adicionar&gt; &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="d4db2-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="d4db2-103">Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="d4db2-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="d4db2-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d4db2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4db2-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="d4db2-105">\<client></span></span>  
<span data-ttu-id="d4db2-106">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="d4db2-106">\<endpoint></span></span>  
<span data-ttu-id="d4db2-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="d4db2-107">\<host></span></span>  
<span data-ttu-id="d4db2-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d4db2-108">\<baseAddresses></span></span>  
<span data-ttu-id="d4db2-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="d4db2-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4db2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4db2-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="d4db2-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="d4db2-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4db2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d4db2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d4db2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d4db2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4db2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d4db2-114">Attributes</span></span>  
  
|<span data-ttu-id="d4db2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d4db2-115">Attribute</span></span>|<span data-ttu-id="d4db2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4db2-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="d4db2-117">Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="d4db2-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4db2-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d4db2-118">Child Elements</span></span>  
 <span data-ttu-id="d4db2-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d4db2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4db2-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d4db2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d4db2-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d4db2-121">Element</span></span>|<span data-ttu-id="d4db2-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4db2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4db2-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d4db2-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="d4db2-124">Uma coleção de `baseAddress` elementos.</span><span class="sxs-lookup"><span data-stu-id="d4db2-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4db2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4db2-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="d4db2-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d4db2-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)