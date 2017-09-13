---
title: "Reflexão e .NET Nativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f6ec8d0a93354fcea17b27321d59174f2e53a47f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="reflection-and-net-native"></a><span data-ttu-id="a5e2e-102">Reflexão e .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="a5e2e-102">Reflection and .NET Native</span></span>
<span data-ttu-id="a5e2e-103">No .NET Framework, o desenvolvimento gerenciado oferece suporte à metaprogramação por meio da API de reflexão.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="a5e2e-104">A reflexão permite inspecionar objetos em um aplicativo, chamar métodos em objetos descobertos por meio de inspeção, gerar novos tipos no tempo de execução e oferece suporte a muitos outros cenários de código dinâmico.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="a5e2e-105">Ele também oferece suporte à serialização e desserialização, o que permite que os valores do campo do objeto sejam mantidos e restaurados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="a5e2e-106">Todos esses cenários exigem o compilador do .NET Framework JIT (just-in-time) para gerar código nativo com base em metadados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="a5e2e-107">O tempo de execução do [!INCLUDE[net_native](../../../includes/net-native-md.md)] não inclui um compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-107">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="a5e2e-108">Como resultado, todo o código nativo necessário deve ser gerado com antecedência.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="a5e2e-109">Um conjunto de heurística é usado para determinar qual código deve ser gerado, mas esses heurística não pode abranger todos os cenários de metaprogramação possíveis.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="a5e2e-110">Portanto, você deve fornecer dicas para esses cenários metaprogramação usando [diretivas de tempo de execução](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a5e2e-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="a5e2e-111">Se o código de implementação ou de metadados necessário não está disponível em tempo de execução, seu aplicativo gerará uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ou [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a5e2e-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="a5e2e-112">Estão disponíveis duas soluções de problemas que gerarão a entrada apropriada para seu arquivo de diretivas de tempo de execução, a qual elimina a exceção:</span><span class="sxs-lookup"><span data-stu-id="a5e2e-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
-   <span data-ttu-id="a5e2e-113">A [solução de problemas MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) para tipos.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-113">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
-   <span data-ttu-id="a5e2e-114">A [solução de problemas MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) para métodos.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-114">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5e2e-115">Para obter uma visão geral do processo de compilação do .NET Native que fornece informações de contexto sobre a necessidade de ter um arquivo das diretivas de tempo de execução, consulte [.NET Native e compilação](../../../docs/framework/net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="a5e2e-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="a5e2e-116">Além disso, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] não permite refletir sobre membros particulares da biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-116">In addition, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="a5e2e-117">Por exemplo, uma chamada para a propriedade <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=fullName> para recuperar os campos de um tipo de biblioteca de classes do .NET Framework retorna somente campos públicos ou protegidos.</span><span class="sxs-lookup"><span data-stu-id="a5e2e-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=fullName> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="a5e2e-118">Os tópicos a seguir fornecem a documentação conceitual e de referência necessária para oferecer suporte à reflexão e serialização nos seus aplicativos:</span><span class="sxs-lookup"><span data-stu-id="a5e2e-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
-   [<span data-ttu-id="a5e2e-119">APIs que dependem de reflexão</span><span class="sxs-lookup"><span data-stu-id="a5e2e-119">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [<span data-ttu-id="a5e2e-120">Referência da API de reflexão</span><span class="sxs-lookup"><span data-stu-id="a5e2e-120">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [<span data-ttu-id="a5e2e-121">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a5e2e-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5e2e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5e2e-122">See Also</span></span>  
 <span data-ttu-id="a5e2e-123">[Compilação de aplicativos com o .NET Native](../../../docs/framework/net-native/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5e2e-123">[Compiling Apps with .NET Native](../../../docs/framework/net-native/index.md) </span></span>  
 [<span data-ttu-id="a5e2e-124">.NET Native e compilação</span><span class="sxs-lookup"><span data-stu-id="a5e2e-124">.NET Native and Compilation</span></span>](../../../docs/framework/net-native/net-native-and-compilation.md)
