---
title: '&lt;appDomainManagerAssembly&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e07b7bd18f19439f64ed8eaef5bda3bad5cef77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="814a7-102">&lt;appDomainManagerAssembly&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="814a7-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="814a7-103">Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="814a7-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="814a7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="814a7-104">\<configuration></span></span>  
<span data-ttu-id="814a7-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="814a7-105">\<runtime></span></span>  
<span data-ttu-id="814a7-106">\<appDomainManagerAssembly ></span><span class="sxs-lookup"><span data-stu-id="814a7-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814a7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="814a7-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="814a7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="814a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="814a7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="814a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="814a7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="814a7-110">Attributes</span></span>  
  
|<span data-ttu-id="814a7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="814a7-111">Attribute</span></span>|<span data-ttu-id="814a7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="814a7-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="814a7-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="814a7-113">Required attribute.</span></span> <span data-ttu-id="814a7-114">Especifica o nome para exibição do assembly que fornece o Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="814a7-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="814a7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="814a7-115">Child Elements</span></span>  
 <span data-ttu-id="814a7-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="814a7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="814a7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="814a7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="814a7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="814a7-118">Element</span></span>|<span data-ttu-id="814a7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="814a7-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="814a7-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="814a7-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="814a7-121">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="814a7-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="814a7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="814a7-122">Remarks</span></span>  
 <span data-ttu-id="814a7-123">Para especificar o tipo de Gerenciador de domínio de aplicativo, você deve especificar ambos os esse elemento e o [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="814a7-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="814a7-124">Se qualquer um desses elementos não for especificado, a outra será ignorada.</span><span class="sxs-lookup"><span data-stu-id="814a7-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="814a7-125">Quando o domínio de aplicativo padrão é carregado, <xref:System.TypeLoadException> é gerada se o assembly especificado não existe ou se o assembly não tem o tipo especificado pelo [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elemento; e o processo não será iniciado.</span><span class="sxs-lookup"><span data-stu-id="814a7-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="814a7-126">Se o assembly é encontrado, mas não coincide com as informações de versão, uma <xref:System.IO.FileLoadException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="814a7-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="814a7-127">Quando você especifica o tipo de Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="814a7-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="814a7-128">Use o <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> e <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriedades para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="814a7-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="814a7-129">Especificar o tipo de Gerenciador de domínio de aplicativo requer que o aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="814a7-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="814a7-130">(Por exemplo, um aplicativo em execução na área de trabalho tem confiança total). Se o aplicativo não tem a confiança total, um <xref:System.TypeLoadException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="814a7-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="814a7-131">Para o formato do nome de exibição do assembly, consulte o <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="814a7-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="814a7-132">Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e posterior.</span><span class="sxs-lookup"><span data-stu-id="814a7-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="814a7-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="814a7-133">Example</span></span>  
 <span data-ttu-id="814a7-134">O exemplo a seguir mostra como especificar que o Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão de um processo é o `MyMgr` digite o `AdMgrExample` assembly.</span><span class="sxs-lookup"><span data-stu-id="814a7-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="814a7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="814a7-135">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="814a7-136">\<appDomainManagerType > elemento</span><span class="sxs-lookup"><span data-stu-id="814a7-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [<span data-ttu-id="814a7-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="814a7-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="814a7-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="814a7-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="814a7-139">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="814a7-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)