---
title: Aplicativos de n camadas e remoto com LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="5fb45-102">Aplicativos de n camadas e remoto com LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5fb45-102">N-Tier and Remote Applications with LINQ to SQL</span></span>
<span data-ttu-id="5fb45-103">Você pode criar aplicativos de n camadas ou multicamadas que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5fb45-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="5fb45-104">Normalmente, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contexto de dados, classes de entidade e lógica de construção de consulta estão localizados na camada intermediária, como a camada de acesso a dados (DAL).</span><span class="sxs-lookup"><span data-stu-id="5fb45-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="5fb45-105">A lógica comercial e todos os dados não persistentes podem ser completamente implementados em classes e métodos parciais nas entidades e de contexto de dados, ou pode ser implementado em classes separados.</span><span class="sxs-lookup"><span data-stu-id="5fb45-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>  
  
 <span data-ttu-id="5fb45-106">O cliente ou a camada de apresentação chamam métodos na interface remoto de camada intermediária, e o DAL na camada executará as consultas ou procedimentos armazenados que são mapeados para os métodos de <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="5fb45-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="5fb45-107">A camada intermediária retorna os dados para clientes geralmente como representações de XML de entidades ou objetos de proxy.</span><span class="sxs-lookup"><span data-stu-id="5fb45-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>  
  
 <span data-ttu-id="5fb45-108">Na camada intermediária, as entidades são criadas pelo contexto de dados, que acompanha seu estado, e gerencia a carga de exceção e o envio de alterações ao base de dados.</span><span class="sxs-lookup"><span data-stu-id="5fb45-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="5fb45-109">Essas entidades são anexados” a “ `DataContext`.</span><span class="sxs-lookup"><span data-stu-id="5fb45-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="5fb45-110">No entanto, depois que as entidades são enviadas a outra camada com a serialização, ficam destacadas, que significa que `DataContext` já não estiver controlando seu estado.</span><span class="sxs-lookup"><span data-stu-id="5fb45-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="5fb45-111">As entidades que o cliente envia novamente para atualizações devem ser reatadas ao contexto de dados antes que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode enviar as alterações para o base de dados.</span><span class="sxs-lookup"><span data-stu-id="5fb45-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="5fb45-112">O cliente é responsável por fornecer valores originais e/ou os carimbos de data/hora de volta a camada intermediária se esses são necessários para concorrência otimista verificações.</span><span class="sxs-lookup"><span data-stu-id="5fb45-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>  
  
 <span data-ttu-id="5fb45-113">Em aplicativos ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gerencia a maioria da complexidade.</span><span class="sxs-lookup"><span data-stu-id="5fb45-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="5fb45-114">Para obter mais informações, consulte [NIB: Visão geral do controle de servidor Web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="5fb45-114">For more information, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="5fb45-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="5fb45-115">Additional Resources</span></span>  
 <span data-ttu-id="5fb45-116">Para obter mais informações sobre como implementar aplicativos de n camadas que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="5fb45-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>  
  
-   [<span data-ttu-id="5fb45-117">LINQ to SQL de N camadas com o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5fb45-117">LINQ to SQL N-Tier with ASP.NET</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [<span data-ttu-id="5fb45-118">LINQ to SQL de N camadas com serviços Web</span><span class="sxs-lookup"><span data-stu-id="5fb45-118">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [<span data-ttu-id="5fb45-119">LINQ to SQL com aplicativos cliente-servidor estreitamente ligado</span><span class="sxs-lookup"><span data-stu-id="5fb45-119">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [<span data-ttu-id="5fb45-120">Implementando lógica de negócios de N camadas</span><span class="sxs-lookup"><span data-stu-id="5fb45-120">Implementing N-Tier Business Logic</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [<span data-ttu-id="5fb45-121">Recuperação de dados e operações de comida RUMINADA em aplicativos de N camadas (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="5fb45-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 <span data-ttu-id="5fb45-122">Para obter mais informações sobre aplicativos de n camadas que usam conjuntos de dados ADO.NET, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span><span class="sxs-lookup"><span data-stu-id="5fb45-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb45-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb45-123">See Also</span></span>  
 [<span data-ttu-id="5fb45-124">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="5fb45-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)