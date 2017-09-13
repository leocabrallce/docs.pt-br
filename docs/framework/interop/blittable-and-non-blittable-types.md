---
title: "Tipos blittable e não blittable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: 23
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3fa97ee1df14b5e08faa944265675264c0b6d95a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="c23a5-102">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="c23a5-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="c23a5-103">A maioria dos tipos de dados tem uma representação comum na memória gerenciada e não gerenciada e não exige manipulação especial pelo marshaler de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="c23a5-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="c23a5-104">Esses tipos são chamados *tipos blittable* porque não exigem conversão quando são passados entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c23a5-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c23a5-105">Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos blittable.</span><span class="sxs-lookup"><span data-stu-id="c23a5-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="c23a5-106">A invocação de plataforma não dá suporte a estruturas não blittable como tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="c23a5-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="c23a5-107">Os seguintes tipos do namespace <xref:System> são tipos blittable:</span><span class="sxs-lookup"><span data-stu-id="c23a5-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=fullName>  
  
-   <xref:System.SByte?displayProperty=fullName>  
  
-   <xref:System.Int16?displayProperty=fullName>  
  
-   <xref:System.UInt16?displayProperty=fullName>  
  
-   <xref:System.Int32?displayProperty=fullName>  
  
-   <xref:System.UInt32?displayProperty=fullName>  
  
-   <xref:System.Int64?displayProperty=fullName>  
  
-   <xref:System.UInt64?displayProperty=fullName>  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Single?displayProperty=fullName>  
  
-   <xref:System.Double?displayProperty=fullName>  
  
 <span data-ttu-id="c23a5-108">Os seguintes tipos complexos também são tipos blittable:</span><span class="sxs-lookup"><span data-stu-id="c23a5-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="c23a5-109">Matrizes unidimensionais de tipos blittable, como uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="c23a5-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="c23a5-110">No entanto, um tipo que contém uma matriz variável de tipos blittable não é blittable em si.</span><span class="sxs-lookup"><span data-stu-id="c23a5-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="c23a5-111">Tipos de valor formatados que contêm somente tipos blittable (e classes, se elas tiverem o marshaling realizado como tipos formatados).</span><span class="sxs-lookup"><span data-stu-id="c23a5-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="c23a5-112">Para obter mais informações sobre os tipos de valor formatados, consulte [Marshaling padrão para tipos de valor](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span><span class="sxs-lookup"><span data-stu-id="c23a5-112">For more information about formatted value types, see [Default Marshaling for Value Types](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span></span>  
  
 <span data-ttu-id="c23a5-113">Referências de objeto não são blittable.</span><span class="sxs-lookup"><span data-stu-id="c23a5-113">Object references are not blittable.</span></span> <span data-ttu-id="c23a5-114">Isso inclui uma matriz de referências a objetos que são blittable por si mesmos.</span><span class="sxs-lookup"><span data-stu-id="c23a5-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="c23a5-115">Por exemplo, é possível definir uma estrutura blittable, mas não é possível definir um tipo blittable que contém uma matriz de referências a essas estruturas.</span><span class="sxs-lookup"><span data-stu-id="c23a5-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="c23a5-116">Como uma otimização, as matrizes de tipos blittable e as classes que contêm somente membros blittable são [fixadas](../../../docs/framework/interop/copying-and-pinning.md), em vez de copiadas durante o marshaling.</span><span class="sxs-lookup"><span data-stu-id="c23a5-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="c23a5-117">Esses tipos podem parecer como se tivessem o marshaling realizado como parâmetros de Entrada/Saída quando o chamador e o receptor estão no mesmo apartment.</span><span class="sxs-lookup"><span data-stu-id="c23a5-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="c23a5-118">No entanto, esses tipos, na verdade, têm o marshaling realizado como parâmetros de Entrada e é necessário aplicar os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> de você desejar realizar marshaling do argumento como um parâmetro de Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="c23a5-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="c23a5-119">Alguns tipos de dados gerenciados exigem uma representação diferente em um ambiente não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c23a5-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="c23a5-120">Esses tipos de dados não blittable devem ser convertidos em um formato que pode ter o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="c23a5-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="c23a5-121">Por exemplo, cadeias de caracteres gerenciadas não são tipos blittable porque devem ser convertidas em objetos de cadeia de caracteres antes que possam ter o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="c23a5-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="c23a5-122">A tabela a seguir lista tipos não blittable do namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="c23a5-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="c23a5-123">[Representantes](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), que são estruturas de dados que se referem a um método estático ou a uma instância de classe, também não são blittable.</span><span class="sxs-lookup"><span data-stu-id="c23a5-123">[Delegates](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="c23a5-124">Tipo não bittable</span><span class="sxs-lookup"><span data-stu-id="c23a5-124">Non-blittable type</span></span>|<span data-ttu-id="c23a5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c23a5-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="c23a5-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="c23a5-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="c23a5-127">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c23a5-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="c23a5-128">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="c23a5-128">System.Boolean</span></span>](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|<span data-ttu-id="c23a5-129">Converte em um valor de 1, 2 ou 4 bytes com `true` como 1 ou -1.</span><span class="sxs-lookup"><span data-stu-id="c23a5-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|[<span data-ttu-id="c23a5-130">System.Char</span><span class="sxs-lookup"><span data-stu-id="c23a5-130">System.Char</span></span>](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|<span data-ttu-id="c23a5-131">Converte em um caractere Unicode ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="c23a5-131">Converts to a Unicode or ANSI character.</span></span>|  
|[<span data-ttu-id="c23a5-132">System.Class</span><span class="sxs-lookup"><span data-stu-id="c23a5-132">System.Class</span></span>](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|<span data-ttu-id="c23a5-133">Converte em uma interface de classe.</span><span class="sxs-lookup"><span data-stu-id="c23a5-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="c23a5-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="c23a5-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="c23a5-135">Converte em uma variante ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="c23a5-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="c23a5-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="c23a5-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="c23a5-137">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c23a5-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="c23a5-138">System.String</span><span class="sxs-lookup"><span data-stu-id="c23a5-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="c23a5-139">Converte em uma cadeia de caracteres que termina em uma referência nula ou em um BSTR.</span><span class="sxs-lookup"><span data-stu-id="c23a5-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|[<span data-ttu-id="c23a5-140">System.Valuetype</span><span class="sxs-lookup"><span data-stu-id="c23a5-140">System.Valuetype</span></span>](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|<span data-ttu-id="c23a5-141">Converte em uma estrutura com um layout de memória fixo.</span><span class="sxs-lookup"><span data-stu-id="c23a5-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="c23a5-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="c23a5-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="c23a5-143">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c23a5-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="c23a5-144">Há suporte para tipos de objeto e de classe apenas na interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="c23a5-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="c23a5-145">Para tipos correspondentes no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++, consulte a [Visão geral da biblioteca de classes](../../../docs/standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c23a5-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23a5-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c23a5-146">See Also</span></span>  
 [<span data-ttu-id="c23a5-147">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="c23a5-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
