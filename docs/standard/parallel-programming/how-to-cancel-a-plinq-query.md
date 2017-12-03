---
title: Como cancelar uma consulta PLINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="e6922-102">Como cancelar uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="e6922-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="e6922-103">Os exemplos a seguir mostram dois modos para cancelar uma consulta PLINQ.</span><span class="sxs-lookup"><span data-stu-id="e6922-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="e6922-104">O primeiro exemplo mostra como cancelar uma consulta que consiste principalmente a passagem de dados.</span><span class="sxs-lookup"><span data-stu-id="e6922-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="e6922-105">O segundo exemplo mostra como cancelar uma consulta que contém uma função de usuário é cara.</span><span class="sxs-lookup"><span data-stu-id="e6922-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6922-106">Quando "Apenas meu código" estiver habilitado, o Visual Studio quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="e6922-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e6922-107">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="e6922-107">This error is benign.</span></span> <span data-ttu-id="e6922-108">Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6922-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="e6922-109">Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.</span><span class="sxs-lookup"><span data-stu-id="e6922-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="e6922-110">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="e6922-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e6922-111">Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e6922-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6922-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6922-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="e6922-113">A estrutura do PLINQ não será revertida para um único <xref:System.OperationCanceledException> em uma <xref:System.AggregateException?displayProperty=nameWithType>; o <xref:System.OperationCanceledException> devem ser tratados em um bloco catch separado.</span><span class="sxs-lookup"><span data-stu-id="e6922-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="e6922-114">Se um ou mais representantes de usuário gera um OperationCanceledException(externalCT) (usando externo <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), mas nenhuma outra exceção e a consulta foi definido como `AsParallel().WithCancellation(externalCT)`, em seguida, PLINQ emitirá um único <xref:System.OperationCanceledException> (externalCT) em vez de um <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6922-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6922-115">No entanto, se um usuário delegar lança um <xref:System.OperationCanceledException>e outro representante gerará outro tipo de exceção, as duas exceções serão transferidas para um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e6922-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="e6922-116">A orientação geral sobre o cancelamento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e6922-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="e6922-117">Se você executar o cancelamento de usuário delegado deve informar o PLINQ sobre externo <xref:System.Threading.CancellationToken> e lançar um <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="e6922-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="e6922-118">Se o cancelamento ocorrerá e nenhum outras exceções são geradas, em seguida, você deve tratar uma <xref:System.OperationCanceledException> em vez de um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e6922-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6922-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6922-119">Example</span></span>  
 <span data-ttu-id="e6922-120">O exemplo a seguir mostra como tratar o cancelamento quando você tem uma função de computação dispendiosa no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6922-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="e6922-121">Quando você processa o cancelamento no código do usuário, você não precisa usar <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> na definição de consulta.</span><span class="sxs-lookup"><span data-stu-id="e6922-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="e6922-122">No entanto, é recomendável que você faça isso porque <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> não tem nenhum efeito no desempenho da consulta e permite o cancelamento ser tratada pelo código do usuário e de operadores de consulta.</span><span class="sxs-lookup"><span data-stu-id="e6922-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="e6922-123">Para garantir a capacidade de resposta do sistema, é recomendável que você verificar o cancelamento em torno de uma vez por milissegundo; No entanto, qualquer período de até 10 milissegundos é considerado aceitável.</span><span class="sxs-lookup"><span data-stu-id="e6922-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="e6922-124">Essa frequência não deve ter um impacto negativo no desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="e6922-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="e6922-125">Quando um enumerador é descartado, por exemplo quando código quebra fora de um loop foreach (para cada um no Visual Basic) que estiver iterando sobre resultados de consulta, em seguida, a consulta foi cancelada, mas nenhuma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="e6922-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6922-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6922-126">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="e6922-127">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="e6922-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="e6922-128">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="e6922-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)