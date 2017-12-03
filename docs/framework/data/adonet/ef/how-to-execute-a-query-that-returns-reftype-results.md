---
title: 'Como: Executar uma consulta que retorna resultados de RefType'
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
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4e5bb3a3f6cba2cbc9799825e7f608f4c0e636f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="dcb58-102">Como: Executar uma consulta que retorna resultados de RefType</span><span class="sxs-lookup"><span data-stu-id="dcb58-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="dcb58-103">Este tópico mostra como executar um comando em um modelo conceitual usando um objeto de <xref:System.Data.EntityClient.EntityCommand> , e como recuperar <xref:System.Data.Metadata.Edm.RefType> resultados usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dcb58-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="dcb58-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb58-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="dcb58-105">Adicionar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcb58-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="dcb58-106">Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="dcb58-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="dcb58-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="dcb58-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="dcb58-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb58-108">Example</span></span>  
 <span data-ttu-id="dcb58-109">Este exemplo executa uma consulta que retorna resultados de <xref:System.Data.Metadata.Edm.RefType> .</span><span class="sxs-lookup"><span data-stu-id="dcb58-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="dcb58-110">Se você passar a seguinte consulta como um argumento a função de `ExectueRefTypeQuery` , a função retorna uma referência para a entidade:</span><span class="sxs-lookup"><span data-stu-id="dcb58-110">If you pass the following query as an argument to the `ExectueRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="dcb58-111">Se você passar uma consulta parametrizada, como o exemplo a seguir, adicione os objetos de <xref:System.Data.EntityClient.EntityParameter> à propriedade de <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> no objeto de <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="dcb58-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="dcb58-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb58-112">See Also</span></span>  
 [<span data-ttu-id="dcb58-113">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="dcb58-113">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="dcb58-114">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="dcb58-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)