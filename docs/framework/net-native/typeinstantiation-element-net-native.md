---
title: Elemento &lt;TypeInstantiation&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b4b0a295e5d788eb50ba39227ac6971ea057ec1e
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="lttypeinstantiationgt-element-net-native"></a><span data-ttu-id="ac962-102">Elemento &lt;TypeInstantiation&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="ac962-102">&lt;TypeInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="ac962-103">Aplica a política de reflexão de tempo de execução a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="ac962-103">Applies runtime reflection policy to a constructed generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac962-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac962-104">Syntax</span></span>  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
                   DataContractSerializer="policy_setting"  
                   DataContractJsonSerializer="policy_setting"  
                   XmlSerializer="policy_setting"  
                   MarshalObject="policy_setting"  
                   MarshalDelegate="policy_setting"  
                   MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac962-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac962-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ac962-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac962-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac962-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac962-107">Attributes</span></span>  
  
|<span data-ttu-id="ac962-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac962-108">Attribute</span></span>|<span data-ttu-id="ac962-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="ac962-109">Attribute type</span></span>|<span data-ttu-id="ac962-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ac962-111">Geral</span><span class="sxs-lookup"><span data-stu-id="ac962-111">General</span></span>|<span data-ttu-id="ac962-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ac962-112">Required attribute.</span></span> <span data-ttu-id="ac962-113">Especifica o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-113">Specifies the type name.</span></span>|  
|`Arguments`|<span data-ttu-id="ac962-114">Geral</span><span class="sxs-lookup"><span data-stu-id="ac962-114">General</span></span>|<span data-ttu-id="ac962-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ac962-115">Required attribute.</span></span> <span data-ttu-id="ac962-116">Especifica os argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="ac962-116">Specifies the generic type arguments.</span></span> <span data-ttu-id="ac962-117">Se houver vários parâmetros, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ac962-117">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Activate`|<span data-ttu-id="ac962-118">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ac962-118">Reflection</span></span>|<span data-ttu-id="ac962-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-119">Optional attribute.</span></span> <span data-ttu-id="ac962-120">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="ac962-120">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="ac962-121">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ac962-121">Reflection</span></span>|<span data-ttu-id="ac962-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-122">Optional attribute.</span></span> <span data-ttu-id="ac962-123">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac962-123">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="ac962-124">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ac962-124">Reflection</span></span>|<span data-ttu-id="ac962-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-125">Optional attribute.</span></span> <span data-ttu-id="ac962-126">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="ac962-126">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="ac962-127">Serialização</span><span class="sxs-lookup"><span data-stu-id="ac962-127">Serialization</span></span>|<span data-ttu-id="ac962-128">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-128">Optional attribute.</span></span> <span data-ttu-id="ac962-129">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="ac962-129">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="ac962-130">Serialização</span><span class="sxs-lookup"><span data-stu-id="ac962-130">Serialization</span></span>|<span data-ttu-id="ac962-131">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-131">Optional attribute.</span></span> <span data-ttu-id="ac962-132">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ac962-132">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="ac962-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="ac962-133">Serialization</span></span>|<span data-ttu-id="ac962-134">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-134">Optional attribute.</span></span> <span data-ttu-id="ac962-135">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ac962-135">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="ac962-136">Serialização</span><span class="sxs-lookup"><span data-stu-id="ac962-136">Serialization</span></span>|<span data-ttu-id="ac962-137">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-137">Optional attribute.</span></span> <span data-ttu-id="ac962-138">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ac962-138">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="ac962-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ac962-139">Interop</span></span>|<span data-ttu-id="ac962-140">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-140">Optional attribute.</span></span> <span data-ttu-id="ac962-141">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="ac962-141">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="ac962-142">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ac962-142">Interop</span></span>|<span data-ttu-id="ac962-143">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-143">Optional attribute.</span></span> <span data-ttu-id="ac962-144">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="ac962-144">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="ac962-145">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ac962-145">Interop</span></span>|<span data-ttu-id="ac962-146">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac962-146">Optional attribute.</span></span> <span data-ttu-id="ac962-147">Controla a política de estruturas de marshaling para código nativo.</span><span class="sxs-lookup"><span data-stu-id="ac962-147">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ac962-148">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="ac962-148">Name attribute</span></span>  
  
|<span data-ttu-id="ac962-149">Valor</span><span class="sxs-lookup"><span data-stu-id="ac962-149">Value</span></span>|<span data-ttu-id="ac962-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac962-151">*type_name*</span><span class="sxs-lookup"><span data-stu-id="ac962-151">*type_name*</span></span>|<span data-ttu-id="ac962-152">O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-152">The type name.</span></span> <span data-ttu-id="ac962-153">Se este elemento `<TypeInstantiation>` for o filho de um elemento [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), de um elemento [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou de outro elemento `<TypeInstantiation>`, o *type_name* poderá incluir o nome do tipo sem seu namespace.</span><span class="sxs-lookup"><span data-stu-id="ac962-153">If this `<TypeInstantiation>` element is the child of a [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) element, a [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element, or another `<TypeInstantiation>` element, *type_name* can specify the name of the type without its namespace.</span></span> <span data-ttu-id="ac962-154">Caso contrário, o *type_name* deverá incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="ac962-154">Otherwise, *type_name* must include the fully qualified type name.</span></span> <span data-ttu-id="ac962-155">O nome do tipo não decorado.</span><span class="sxs-lookup"><span data-stu-id="ac962-155">The type name isn't decorated.</span></span> <span data-ttu-id="ac962-156">Por exemplo, para um objeto <xref:System.Collections.Generic.List%601?displayProperty=fullName>, o elemento `<TypeInstantiation>` poderá aparecer da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac962-156">For example, for a <xref:System.Collections.Generic.List%601?displayProperty=fullName> object, the `<TypeInstantiation>` element might appear as follows:</span></span><br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ac962-157">Atributo de argumentos</span><span class="sxs-lookup"><span data-stu-id="ac962-157">Arguments attribute</span></span>  
  
|<span data-ttu-id="ac962-158">Valor</span><span class="sxs-lookup"><span data-stu-id="ac962-158">Value</span></span>|<span data-ttu-id="ac962-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac962-160">*type_argument*</span><span class="sxs-lookup"><span data-stu-id="ac962-160">*type_argument*</span></span>|<span data-ttu-id="ac962-161">Especifica os argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="ac962-161">Specifies the generic type arguments.</span></span> <span data-ttu-id="ac962-162">Se houver vários parâmetros, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ac962-162">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ac962-163">Cada argumento deve conter o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="ac962-163">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ac962-164">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="ac962-164">All other attributes</span></span>  
  
|<span data-ttu-id="ac962-165">Valor</span><span class="sxs-lookup"><span data-stu-id="ac962-165">Value</span></span>|<span data-ttu-id="ac962-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac962-167">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ac962-167">*policy_setting*</span></span>|<span data-ttu-id="ac962-168">A configuração a ser aplicada a este tipo de política para o tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="ac962-168">The setting to apply to this policy type for the constructed generic type.</span></span> <span data-ttu-id="ac962-169">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="ac962-169">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ac962-170">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ac962-170">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac962-171">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac962-171">Child Elements</span></span>  
  
|<span data-ttu-id="ac962-172">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac962-172">Element</span></span>|<span data-ttu-id="ac962-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac962-174">\<Event></span><span class="sxs-lookup"><span data-stu-id="ac962-174">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)|<span data-ttu-id="ac962-175">Aplica a política de reflexão a um evento pertencente a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-175">Applies reflection policy to an event belonging to this type.</span></span>|  
|[<span data-ttu-id="ac962-176">\<Field></span><span class="sxs-lookup"><span data-stu-id="ac962-176">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)|<span data-ttu-id="ac962-177">Aplica a política de reflexão a um campo pertencente a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-177">Applies reflection policy to a field belonging to this type.</span></span>|  
|[<span data-ttu-id="ac962-178">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="ac962-178">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="ac962-179">Aplica a política a um tipo, se esta política tiver sido aplicada ao tipo representado pelo elemento `<TypeInstantiation>` recipiente.</span><span class="sxs-lookup"><span data-stu-id="ac962-179">Applies policy to a type, if that policy has been applied to the type represented by the containing `<TypeInstantiation>` element.</span></span>|  
|[<span data-ttu-id="ac962-180">\<Method></span><span class="sxs-lookup"><span data-stu-id="ac962-180">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="ac962-181">Aplica a política de reflexão a um método pertencente a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-181">Applies reflection policy to a method belonging to this type.</span></span>|  
|[<span data-ttu-id="ac962-182">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="ac962-182">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|<span data-ttu-id="ac962-183">Aplica a política de reflexão a um método construído genérico pertencente a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-183">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|  
|[<span data-ttu-id="ac962-184">\<Property></span><span class="sxs-lookup"><span data-stu-id="ac962-184">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)|<span data-ttu-id="ac962-185">Aplica a política de reflexão a uma propriedade pertencente a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="ac962-185">Applies reflection policy to a property belonging to this type.</span></span>|  
|[<span data-ttu-id="ac962-186">\<Type></span><span class="sxs-lookup"><span data-stu-id="ac962-186">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ac962-187">Aplica a política de reflexão a um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="ac962-187">Applies reflection policy to a nested type.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="ac962-188">Aplica a política de reflexão a um tipo genérico construído aninhado.</span><span class="sxs-lookup"><span data-stu-id="ac962-188">Applies reflection policy to a nested constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac962-189">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac962-189">Parent Elements</span></span>  
  
|<span data-ttu-id="ac962-190">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac962-190">Element</span></span>|<span data-ttu-id="ac962-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac962-191">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac962-192">\<Application></span><span class="sxs-lookup"><span data-stu-id="ac962-192">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="ac962-193">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac962-193">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|  
|[<span data-ttu-id="ac962-194">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="ac962-194">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="ac962-195">Aplica a política de reflexão para todos os tipos em um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="ac962-195">Applies reflection policy to all the types in a specified assembly.</span></span>|  
|[<span data-ttu-id="ac962-196">\<Library></span><span class="sxs-lookup"><span data-stu-id="ac962-196">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="ac962-197">Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac962-197">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|  
|[<span data-ttu-id="ac962-198">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="ac962-198">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="ac962-199">Aplica a política de reflexão a todos os tipos em um namespace.</span><span class="sxs-lookup"><span data-stu-id="ac962-199">Applies reflection policy to all the types in a namespace.</span></span>|  
|[<span data-ttu-id="ac962-200">\<Type></span><span class="sxs-lookup"><span data-stu-id="ac962-200">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ac962-201">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ac962-201">Applies reflection policy to a type and all its members.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="ac962-202">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ac962-202">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac962-203">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac962-203">Remarks</span></span>  
 <span data-ttu-id="ac962-204">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais.</span><span class="sxs-lookup"><span data-stu-id="ac962-204">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="ac962-205">No entanto, pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="ac962-205">However, at least one must be present.</span></span>  
  
 <span data-ttu-id="ac962-206">Se um elemento `<TypeInstantiation>` for o filho de um elemento [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) ou [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), ele substituirá as configurações de política definidas pelo elemento pai.</span><span class="sxs-lookup"><span data-stu-id="ac962-206">If a `<TypeInstantiation>` element is the child of an [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), element, it overrides the policy settings defined by the parent element.</span></span> <span data-ttu-id="ac962-207">Se um elemento [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) definir uma definição de tipo genérico correspondente, o elemento `<TypeInstantiation>` substituirá a política de reflexão em tempo de execução somente para instanciações do tipo genérico construído especificado.</span><span class="sxs-lookup"><span data-stu-id="ac962-207">If a [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element defines a corresponding generic type definition, the `<TypeInstantiation>` element overrides runtime reflection policy only for instantiations of the specified constructed generic type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac962-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac962-208">Example</span></span>  
 <span data-ttu-id="ac962-209">O exemplo a seguir usa uma reflexão para recuperar a definição de tipo genérico de um objeto <xref:System.Collections.Generic.Dictionary%602> construído.</span><span class="sxs-lookup"><span data-stu-id="ac962-209">The following example uses reflection to retrieve the generic type definition from a constructed <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="ac962-210">Ele também usa reflexão para exibir informações sobre objetos <xref:System.Type> que representam tipos genéricos construídos e definições de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="ac962-210">It also uses reflection to display information about <xref:System.Type> objects that represent constructed generic types and generic type definitions.</span></span> <span data-ttu-id="ac962-211">A variável `b` no exemplo é um controle [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).</span><span class="sxs-lookup"><span data-stu-id="ac962-211">The variable `b` in the example is a [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 <span data-ttu-id="ac962-212">[!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="ac962-212">[!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]</span></span>  
  
 <span data-ttu-id="ac962-213">Após a compilação com a cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)], o exemplo gera uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) na linha que chama o método <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ac962-213">After compilation with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain, the example throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception on the line that calls the <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="ac962-214">Para eliminar a exceção e fornecer os metadados necessários, adicione o seguinte elemento `<TypeInstantiation>` ao arquivo de diretivas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="ac962-214">You can eliminate the exception and provide the necessary metadata by adding the following `<TypeInstantiation>` element to the runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac962-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac962-215">See Also</span></span>  
 <span data-ttu-id="ac962-216">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ac962-216">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 <span data-ttu-id="ac962-217">[Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md) </span><span class="sxs-lookup"><span data-stu-id="ac962-217">[Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md) </span></span>  
 [<span data-ttu-id="ac962-218">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ac962-218">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
