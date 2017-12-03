---
title: "Exemplos de sintaxe de expressão de consulta: projeção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 83d4f1e68938d4aa7330fbcacb40c44b3c06e400
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="0bc35-102">Exemplos de sintaxe de expressão de consulta: projeção</span><span class="sxs-lookup"><span data-stu-id="0bc35-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="0bc35-103">Os exemplos neste tópico demonstram como usar o `Select` método e o `From … From …` palavras-chave para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) usando sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="0bc35-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="0bc35-104">`From … From …` é o equivalente baseado em consulta do método `SelectMany`.</span><span class="sxs-lookup"><span data-stu-id="0bc35-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="0bc35-105">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0bc35-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0bc35-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="0bc35-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="0bc35-107">Selecionar</span><span class="sxs-lookup"><span data-stu-id="0bc35-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="0bc35-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-108">Example</span></span>  
 <span data-ttu-id="0bc35-109">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Select%2A> para retornar todas as linhas da tabela de `Product` e exibir os nomes de produto.</span><span class="sxs-lookup"><span data-stu-id="0bc35-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="0bc35-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-110">Example</span></span>  
 <span data-ttu-id="0bc35-111">O exemplo a seguir usa <xref:System.Linq.Enumerable.Select%2A> para retornar somente uma sequência de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="0bc35-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="0bc35-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-112">Example</span></span>  
 <span data-ttu-id="0bc35-113">O exemplo a seguir usa o método <xref:System.Linq.Queryable.Select%2A> para projetar as propriedades `Product.Name` e `Product.ProductID` em uma sequência de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="0bc35-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="0bc35-114">De...</span><span class="sxs-lookup"><span data-stu-id="0bc35-114">From …</span></span> <span data-ttu-id="0bc35-115">De...</span><span class="sxs-lookup"><span data-stu-id="0bc35-115">From …</span></span> <span data-ttu-id="0bc35-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="0bc35-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="0bc35-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-117">Example</span></span>  
 <span data-ttu-id="0bc35-118">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde `TotalDue` é menor que 500,00.</span><span class="sxs-lookup"><span data-stu-id="0bc35-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="0bc35-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-119">Example</span></span>  
 <span data-ttu-id="0bc35-120">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos feitos em 1º de outubro de 2002 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="0bc35-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="0bc35-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc35-121">Example</span></span>  
 <span data-ttu-id="0bc35-122">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde o total do pedido é maior que 10000,00 e usa a atribuição `From` para evitar solicitar o total duas vezes.</span><span class="sxs-lookup"><span data-stu-id="0bc35-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="0bc35-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bc35-123">See Also</span></span>  
 [<span data-ttu-id="0bc35-124">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0bc35-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)