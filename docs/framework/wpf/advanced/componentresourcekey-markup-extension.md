---
title: "Extensão de marcação ComponentResourceKey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7f959318c5991fea2df92ff8000e85345fb35ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="33ab1-102">Extensão de marcação ComponentResourceKey</span><span class="sxs-lookup"><span data-stu-id="33ab1-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="33ab1-103">Define e referencia chaves para recursos carregados de assemblies externos.</span><span class="sxs-lookup"><span data-stu-id="33ab1-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="33ab1-104">Isso permite que um recurso de pesquisa especifique um tipo de destino em um assembly, em vez de um dicionário de recurso explícito em um assembly ou em uma classe.</span><span class="sxs-lookup"><span data-stu-id="33ab1-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="33ab1-105">Uso do atributo XAML (configuração de chave, compacta)</span><span class="sxs-lookup"><span data-stu-id="33ab1-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="33ab1-106">Uso do atributo XAML (configuração de chave, detalhada)</span><span class="sxs-lookup"><span data-stu-id="33ab1-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="33ab1-107">Uso do atributo XAML (solicitação de recurso, compacta)</span><span class="sxs-lookup"><span data-stu-id="33ab1-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="33ab1-108">Uso do atributo XAML (solicitação de recurso, detalhada)</span><span class="sxs-lookup"><span data-stu-id="33ab1-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="33ab1-109">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="33ab1-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="33ab1-110">O nome do tipo [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] público definido no assembly de recurso.</span><span class="sxs-lookup"><span data-stu-id="33ab1-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="33ab1-111">A chave para o recurso.</span><span class="sxs-lookup"><span data-stu-id="33ab1-111">The key for the resource.</span></span> <span data-ttu-id="33ab1-112">Quando recursos forem pesquisados, `targetID` será análogo à [Diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) do recurso.</span><span class="sxs-lookup"><span data-stu-id="33ab1-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33ab1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="33ab1-113">Remarks</span></span>  
 <span data-ttu-id="33ab1-114">Como visto nos usos acima, um uso de extensão de marcação {`ComponentResourceKey`} é encontrado em dois locais:</span><span class="sxs-lookup"><span data-stu-id="33ab1-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="33ab1-115">A definição de uma chave em um dicionário de recursos de tema, conforme fornecido por um autor de controle.</span><span class="sxs-lookup"><span data-stu-id="33ab1-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="33ab1-116">Acessando um recurso de tema do assembly, quando você está remodelando o controle, mas deseja usar valores de propriedade que vêm dos recursos fornecidos pelos temas do controle.</span><span class="sxs-lookup"><span data-stu-id="33ab1-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="33ab1-117">Para fazer referência a recursos de componente que vêm de temas, geralmente é recomendável usar `{DynamicResource}`, em vez de `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="33ab1-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="33ab1-118">Isso é mostrado em usos.</span><span class="sxs-lookup"><span data-stu-id="33ab1-118">This is shown in the usages.</span></span> <span data-ttu-id="33ab1-119">`{DynamicResource}` é recomendado porque o tema em si pode ser alterado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="33ab1-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="33ab1-120">Se você desejar que o recurso do componente que mais se aproxima da intenção do autor do controle para dar suporte a um tema, habilite a referência de recurso do componente para que seja dinâmica também.</span><span class="sxs-lookup"><span data-stu-id="33ab1-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="33ab1-121">O <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifica um tipo que existe no assembly de destino onde o recurso é definido.</span><span class="sxs-lookup"><span data-stu-id="33ab1-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="33ab1-122">Um `ComponentResourceKey` pode ser definido e usado independentemente de saber exatamente onde o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> é definido, mas a hora deve resolver o tipo por meio de assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="33ab1-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="33ab1-123">Um uso comum para <xref:System.Windows.ComponentResourceKey> é definir chaves que são expostas como membros de uma classe.</span><span class="sxs-lookup"><span data-stu-id="33ab1-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="33ab1-124">Para este uso, você deve usar o <xref:System.Windows.ComponentResourceKey> construtor de classe, não a extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="33ab1-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="33ab1-125">Para obter mais informações, consulte <xref:System.Windows.ComponentResourceKey>, ou a seção "Definindo e referenciando chaves para recursos de tema" do tópico [visão geral de criação do controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="33ab1-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="33ab1-126">Para estabelecer chaves e referenciar recursos de chave, sintaxe do atributo normalmente é usada para a extensão de marcação `ComponentResourceKey`.</span><span class="sxs-lookup"><span data-stu-id="33ab1-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="33ab1-127">A sintaxe compacta mostrada depende do <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> assinatura de construtor e o uso de parâmetro posicional de uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="33ab1-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="33ab1-128">A ordem na qual o `targetTypeName` e o `targetID` são apresentados é importante.</span><span class="sxs-lookup"><span data-stu-id="33ab1-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="33ab1-129">A sintaxe detalhada depende de <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> construtor padrão e, em seguida, define o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> e <xref:System.Windows.ComponentResourceKey.ResourceId%2A> de maneira análoga à sintaxe de atributo verdadeira em um elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="33ab1-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="33ab1-130">Na sintaxe detalhada, a ordem na qual as propriedades são definidas não é importante.</span><span class="sxs-lookup"><span data-stu-id="33ab1-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="33ab1-131">O relacionamento e os mecanismos dessas duas alternativas (compacta e detalhada) é descrito em mais detalhes no tópico [Extensões de marcação e XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="33ab1-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="33ab1-132">Tecnicamente, o valor de `targetID` pode ser qualquer objeto, não precisa ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="33ab1-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="33ab1-133">No entanto, o uso mais comum no WPF é alinhar o valor `targetID` com formulários que são cadeias de caracteres e o ponto em que tais cadeias são válidas na [Gramática XamlName](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="33ab1-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="33ab1-134">`ComponentResourceKey` pode ser usado na sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="33ab1-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="33ab1-135">Nesse caso, especificando o valor de ambas as <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> e <xref:System.Windows.ComponentResourceKey.ResourceId%2A> propriedades é necessário para inicializar adequadamente a extensão.</span><span class="sxs-lookup"><span data-stu-id="33ab1-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="33ab1-136">No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação leitor, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.ComponentResourceKey> classe.</span><span class="sxs-lookup"><span data-stu-id="33ab1-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="33ab1-137">`ComponentResourceKey` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="33ab1-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="33ab1-138">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="33ab1-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="33ab1-139">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="33ab1-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="33ab1-140">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="33ab1-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ab1-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33ab1-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="33ab1-142">Visão geral da criação de controle</span><span class="sxs-lookup"><span data-stu-id="33ab1-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="33ab1-143">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="33ab1-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="33ab1-144">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="33ab1-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)