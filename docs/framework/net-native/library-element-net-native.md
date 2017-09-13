---
title: Elemento &lt;Library&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4006b18e91b79d5f31649a0a15a18b9f7f28c38e
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltlibrarygt-element-net-native"></a><span data-ttu-id="6637f-102">Elemento &lt;Library&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="6637f-102">&lt;Library&gt; Element (.NET Native)</span></span>
<span data-ttu-id="6637f-103">Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6637f-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="6637f-104">Elemento \<Directives></span><span class="sxs-lookup"><span data-stu-id="6637f-104">\<Directives> Element</span></span>  
<span data-ttu-id="6637f-105">Elemento \<Library></span><span class="sxs-lookup"><span data-stu-id="6637f-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6637f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6637f-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6637f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6637f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6637f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6637f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6637f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6637f-109">Attributes</span></span>  
  
|<span data-ttu-id="6637f-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="6637f-110">Attribute</span></span>|<span data-ttu-id="6637f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6637f-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="6637f-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6637f-112">Required attribute.</span></span> <span data-ttu-id="6637f-113">Especifica o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="6637f-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="6637f-114">Elementos filhos deste elemento `<Library>` define a política de reflexão do tempo de execução para tipos e membros de tipo encontrados neste assembly.</span><span class="sxs-lookup"><span data-stu-id="6637f-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6637f-115">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="6637f-115">Name attribute</span></span>  
  
|<span data-ttu-id="6637f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="6637f-116">Value</span></span>|<span data-ttu-id="6637f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6637f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6637f-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="6637f-118">*assembly_name*</span></span>|<span data-ttu-id="6637f-119">O nome simples do assembly, sem a extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="6637f-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="6637f-120">Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6637f-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName> property.</span></span> <span data-ttu-id="6637f-121">Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions".</span><span class="sxs-lookup"><span data-stu-id="6637f-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="6637f-122">Consulte a seção Comentários para ver uma forma especial de *assembly_name* que dá suporte à inclusão condicional de metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="6637f-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6637f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6637f-123">Child Elements</span></span>  
  
|<span data-ttu-id="6637f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6637f-124">Element</span></span>|<span data-ttu-id="6637f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6637f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6637f-126">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="6637f-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="6637f-127">Aplica a política a todos os tipos em um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="6637f-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="6637f-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="6637f-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="6637f-129">Aplica a política a todos os tipos em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="6637f-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="6637f-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="6637f-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6637f-131">Aplica a política a um tipo específico, como uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="6637f-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="6637f-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="6637f-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="6637f-133">Aplica a política a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="6637f-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="6637f-134">Por exemplo, um elemento [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) pode ser usado para definir a política para um tipo `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="6637f-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6637f-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6637f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6637f-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="6637f-136">Element</span></span>|<span data-ttu-id="6637f-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="6637f-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6637f-138">\<Directives></span><span class="sxs-lookup"><span data-stu-id="6637f-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="6637f-139">O elemento raiz de um arquivo de diretivas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6637f-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6637f-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="6637f-140">Remarks</span></span>  
 <span data-ttu-id="6637f-141">O elemento [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) pode conter zero, um ou mais elementos `<Library>`.</span><span class="sxs-lookup"><span data-stu-id="6637f-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="6637f-142">O elemento `<Library>` serve como um contêiner para definir os elementos do programa cujos metadados são necessária no tempo de execução. Este elemento não expressa política.</span><span class="sxs-lookup"><span data-stu-id="6637f-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="6637f-143">No tempo de compilação, as ferramentas do compilador pesquisam somente a biblioteca designada pelo elemento `<Library>` para os elementos do programa identificados por seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="6637f-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="6637f-144">Em contraste, as ferramentas do compilador pesquisam todas as bibliotecas, incluindo as bibliotecas principais do .NET Framework, por elementos de programa identificados por elementos filhos do elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6637f-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="6637f-145">As diretivas `<Library>` podem ser utilizadas condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="6637f-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="6637f-146">Se o nome do elemento `<Library>` começa e termina com um asterisco (*), a diretiva `<Library>` terá efeito somente se o assembly especificado entre os asteriscos for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6637f-146">If the name of the `<Library>` element starts and ends with an asterisk (*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="6637f-147">Por exemplo, a diretiva de tempo de execução a seguir se aplica somente se o assembly Utillities.dll for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6637f-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6637f-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6637f-148">See Also</span></span>  
 <span data-ttu-id="6637f-149">[Elemento \<Application>](../../../docs/framework/net-native/application-element-net-native.md) </span><span class="sxs-lookup"><span data-stu-id="6637f-149">[\<Application> Element](../../../docs/framework/net-native/application-element-net-native.md) </span></span>  
 <span data-ttu-id="6637f-150">[\<Elemento Directives>](../../../docs/framework/net-native/directives-element-net-native.md) </span><span class="sxs-lookup"><span data-stu-id="6637f-150">[\<Directives> Element](../../../docs/framework/net-native/directives-element-net-native.md) </span></span>  
 <span data-ttu-id="6637f-151">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6637f-151">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 [<span data-ttu-id="6637f-152">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6637f-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
