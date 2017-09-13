---
title: MDA nonComVisibleBaseClass
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
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7f6da0e4a2046ac80a35894383f732eb266b8459
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="5eadd-102">MDA nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="5eadd-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="5eadd-103">O MDA (Assistente de Depuração Gerenciado) de `nonComVisibleBaseClass` é ativado quando uma chamada `QueryInterface` é feita por código não gerenciado ou nativo no CCW (COM Callable Wrapper) de uma classe gerenciada visível em COM derivada de uma classe base que não é visível em COM.</span><span class="sxs-lookup"><span data-stu-id="5eadd-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="5eadd-104">A chamada `QueryInterface` faz com que o MDA seja ativado apenas em casos nos quais a chamada solicita a interface de classe ou o `IDispatch` padrão da classe gerenciada visível em COM.</span><span class="sxs-lookup"><span data-stu-id="5eadd-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="5eadd-105">O MDA não é ativado quando o `QueryInterface` é para uma interface explícita que tem o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> aplicado e é implementado explicitamente pela classe visível em COM.</span><span class="sxs-lookup"><span data-stu-id="5eadd-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5eadd-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="5eadd-106">Symptoms</span></span>  
 <span data-ttu-id="5eadd-107">Uma chamada `QueryInterface` feita por meio do código nativo que está falhando com um HRESULT COR_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="5eadd-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="5eadd-108">O HRESULT pode ser devido ao tempo de execução não permitir chamadas `QueryInterface` que causariam a ativação desse MDA.</span><span class="sxs-lookup"><span data-stu-id="5eadd-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5eadd-109">Causa</span><span class="sxs-lookup"><span data-stu-id="5eadd-109">Cause</span></span>  
 <span data-ttu-id="5eadd-110">O tempo de execução não pode permitir chamadas `QueryInterface` para a interface de classe ou a interface `IDispatch` padrão de uma classe visível em COM que deriva de uma classe não visível em COM devido a possíveis problemas de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="5eadd-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="5eadd-111">Por exemplo, se os membros públicos foram adicionados à a classe base que não é visível em COM, os clientes COM existentes usando a classe derivada podem ser interrompidos porque a vtable da classe derivada, que contém os membros da classe base, seria modificada por uma alteração desse tipo.</span><span class="sxs-lookup"><span data-stu-id="5eadd-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="5eadd-112">Interfaces explícitas expostas a COM não têm esse problema porque elas não incluem os membros base das interfaces na vtable.</span><span class="sxs-lookup"><span data-stu-id="5eadd-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5eadd-113">Resolução</span><span class="sxs-lookup"><span data-stu-id="5eadd-113">Resolution</span></span>  
 <span data-ttu-id="5eadd-114">Não expor a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="5eadd-114">Do not expose the class interface.</span></span> <span data-ttu-id="5eadd-115">Definir uma interface explícita e aplicar o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="5eadd-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5eadd-116">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5eadd-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="5eadd-117">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="5eadd-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5eadd-118">Saída</span><span class="sxs-lookup"><span data-stu-id="5eadd-118">Output</span></span>  
 <span data-ttu-id="5eadd-119">A seguir está um exemplo de mensagem para uma chamada `QueryInterface` em uma classe visível em COM `Derived` que deriva de uma classe não visível em COM `Base`.</span><span class="sxs-lookup"><span data-stu-id="5eadd-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="5eadd-120">Configuração</span><span class="sxs-lookup"><span data-stu-id="5eadd-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eadd-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eadd-121">See Also</span></span>  
 <span data-ttu-id="5eadd-122"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="5eadd-122"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="5eadd-123">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="5eadd-123">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="5eadd-124">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5eadd-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
