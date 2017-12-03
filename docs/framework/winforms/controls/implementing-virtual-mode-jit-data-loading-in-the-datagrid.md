---
title: Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bddac01a0d85ae985b54587619bcac6de5f966f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="88bb7-102">Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-102">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="88bb7-103">Um motivo para implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle é recuperar os dados conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="88bb7-103">One reason to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control is to retrieve data only as it is needed.</span></span> <span data-ttu-id="88bb7-104">Isso é chamado de *carregamento de dados Just-In-Time*.</span><span class="sxs-lookup"><span data-stu-id="88bb7-104">This is called *just-in-time data loading*.</span></span>  
  
 <span data-ttu-id="88bb7-105">Se estiver trabalhando com uma tabela muito grande em um banco de dados remoto, por exemplo, talvez você queira evitar atrasos de inicialização recuperando somente os dados necessários para exibição e recuperando dados adicionais somente quando o usuário rolar novas linhas para a área de exibição.</span><span class="sxs-lookup"><span data-stu-id="88bb7-105">If you are working with a very large table in a remote database, for example, you might want to avoid startup delays by retrieving only the data that is necessary for display and retrieving additional data only when the user scrolls new rows into view.</span></span> <span data-ttu-id="88bb7-106">Se os computadores cliente que estão executando seu aplicativo tiverem uma quantidade limitada de memória disponível para armazenar dados, você também pode querer descartar dados não utilizados quando recuperar novos valores do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-106">If the client computers running your application have a limited amount of memory available for storing data, you might also want to discard unused data when retrieving new values from the database.</span></span>  
  
 <span data-ttu-id="88bb7-107">As seções a seguir descrevem como usar um <xref:System.Windows.Forms.DataGridView> controle com um cache just-in-time.</span><span class="sxs-lookup"><span data-stu-id="88bb7-107">The following sections describe how to use a <xref:System.Windows.Forms.DataGridView> control with a just-in-time cache.</span></span>  
  
 <span data-ttu-id="88bb7-108">Para copiar o código neste tópico como uma única listagem, consulte [Como implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="88bb7-108">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="the-form"></a><span data-ttu-id="88bb7-109">O formulário</span><span class="sxs-lookup"><span data-stu-id="88bb7-109">The Form</span></span>  
 <span data-ttu-id="88bb7-110">O exemplo de código a seguir define um formulário que contém somente leitura <xref:System.Windows.Forms.DataGridView> controle interage com um `Cache` objeto por meio de um <xref:System.Windows.Forms.DataGridView.CellValueNeeded> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="88bb7-110">The following code example defines a form containing a read-only <xref:System.Windows.Forms.DataGridView> control that interacts with a `Cache` object through a <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event handler.</span></span> <span data-ttu-id="88bb7-111">O objeto `Cache` gerencia os valores armazenados localmente e usa um objeto `DataRetriever` para recuperar valores da tabela Orders do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="88bb7-111">The `Cache` object manages the locally stored values and uses a `DataRetriever` object to retrieve values from the Orders table of the sample Northwind database.</span></span> <span data-ttu-id="88bb7-112">O `DataRetriever` objeto que implementa o `IDataPageRetriever` interface necessário para o `Cache` classe, também é usado para inicializar o <xref:System.Windows.Forms.DataGridView> controlar linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="88bb7-112">The `DataRetriever` object, which implements the `IDataPageRetriever` interface required by the `Cache` class, is also used to initialize the <xref:System.Windows.Forms.DataGridView> control rows and columns.</span></span>  
  
 <span data-ttu-id="88bb7-113">Os tipos `IDataPageRetriever`, `DataRetriever` e `Cache` são descritos mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="88bb7-113">The `IDataPageRetriever`, `DataRetriever`, and `Cache` types are described later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88bb7-114">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88bb7-114">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="88bb7-115">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-115">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="88bb7-116">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="88bb7-116">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a><span data-ttu-id="88bb7-117">A Interface IDataPageRetriever</span><span class="sxs-lookup"><span data-stu-id="88bb7-117">The IDataPageRetriever Interface</span></span>  
 <span data-ttu-id="88bb7-118">O exemplo de código a seguir define a interface `IDataPageRetriever`, que é implementada pela classe `DataRetriever`.</span><span class="sxs-lookup"><span data-stu-id="88bb7-118">The following code example defines the `IDataPageRetriever` interface, which is implemented by the `DataRetriever` class.</span></span> <span data-ttu-id="88bb7-119">O único método declarado nessa interface é o método `SupplyPageOfData`, que requer um índice de linhas inicial e uma contagem do número de linhas em uma única página de dados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-119">The only method declared in this interface is the `SupplyPageOfData` method, which requires an initial row index and a count of the number of rows in a single page of data.</span></span> <span data-ttu-id="88bb7-120">Esses valores são usados pelo implementador para recuperar um subconjunto de dados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-120">These values are used by the implementer to retrieve a subset of data from a data source.</span></span>  
  
 <span data-ttu-id="88bb7-121">Um objeto `Cache` usa uma implementação dessa interface durante a construção para carregar duas páginas iniciais de dados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-121">A `Cache` object uses an implementation of this interface during construction to load two initial pages of data.</span></span> <span data-ttu-id="88bb7-122">Sempre que um valor fora do cache é necessário, o cache descarta uma dessas páginas e solicita uma nova página que contém o valor do `IDataPageRetriever`.</span><span class="sxs-lookup"><span data-stu-id="88bb7-122">Whenever an uncached value is needed, the cache discards one of these pages and requests a new page containing the value from the `IDataPageRetriever`.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a><span data-ttu-id="88bb7-123">A classe DataRetriever</span><span class="sxs-lookup"><span data-stu-id="88bb7-123">The DataRetriever Class</span></span>  
 <span data-ttu-id="88bb7-124">O exemplo de código a seguir define a classe `DataRetriever`, que implementa a interface `IDataPageRetriever` para recuperar páginas de dados de um servidor.</span><span class="sxs-lookup"><span data-stu-id="88bb7-124">The following code example defines the `DataRetriever` class, which implements the `IDataPageRetriever` interface to retrieve pages of data from a server.</span></span> <span data-ttu-id="88bb7-125">O `DataRetriever` também fornece uma classe `Columns` e `RowCount` propriedades, que o <xref:System.Windows.Forms.DataGridView> controle usa para criar as colunas necessárias e adicionar o número de linhas vazias apropriado a <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="88bb7-125">The `DataRetriever` class also provides `Columns` and `RowCount` properties, which the <xref:System.Windows.Forms.DataGridView> control uses to create the necessary columns and to add the appropriate number of empty rows to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="88bb7-126">Adicionar as linhas vazias é necessário para que o controle se comporte como se contivesse todos os dados na tabela.</span><span class="sxs-lookup"><span data-stu-id="88bb7-126">Adding the empty rows is necessary so that the control will behave as though it contains all the data in the table.</span></span> <span data-ttu-id="88bb7-127">Isso significa que a caixa de rolagem na barra de rolagem terá o tamanho apropriado e o usuário será capaz de acessar qualquer linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="88bb7-127">This means that the scroll box in the scroll bar will have the appropriate size, and the user will be able to access any row in the table.</span></span> <span data-ttu-id="88bb7-128">As linhas são preenchidas através de <xref:System.Windows.Forms.DataGridView.CellValueNeeded> manipulador de eventos somente quando eles são rolados para a exibição.</span><span class="sxs-lookup"><span data-stu-id="88bb7-128">The rows are filled by the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event handler only when they are scrolled into view.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a><span data-ttu-id="88bb7-129">A classe Cache</span><span class="sxs-lookup"><span data-stu-id="88bb7-129">The Cache Class</span></span>  
 <span data-ttu-id="88bb7-130">O exemplo de código a seguir define a classe `Cache`, que gerencia duas páginas de dados preenchidas por meio de uma implementação de `IDataPageRetriever`.</span><span class="sxs-lookup"><span data-stu-id="88bb7-130">The following code example defines the `Cache` class, which manages two pages of data populated through an `IDataPageRetriever` implementation.</span></span> <span data-ttu-id="88bb7-131">O `Cache` classe define uma interna `DataPage` estrutura, que contém um <xref:System.Data.DataTable> para armazenar os valores em um único cache página e que calcula a linha de índices que representam os limites superiores e inferiores da página.</span><span class="sxs-lookup"><span data-stu-id="88bb7-131">The `Cache` class defines an inner `DataPage` structure, which contains a <xref:System.Data.DataTable> to store the values in a single cache page and which calculates the row indexes that represent the upper and lower boundaries of the page.</span></span>  
  
 <span data-ttu-id="88bb7-132">A classe `Cache` carrega duas páginas de dados no momento da construção.</span><span class="sxs-lookup"><span data-stu-id="88bb7-132">The `Cache` class loads two pages of data at construction time.</span></span> <span data-ttu-id="88bb7-133">Sempre que o <xref:System.Windows.Forms.DataGridView.CellValueNeeded> evento solicita um valor, o `Cache` objeto determina se o valor estiver disponível em um dos seus dois páginas e, em caso afirmativo, retorna.</span><span class="sxs-lookup"><span data-stu-id="88bb7-133">Whenever the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event requests a value, the `Cache` object determines if the value is available in one of its two pages and, if so, returns it.</span></span> <span data-ttu-id="88bb7-134">Se o valor não estiver disponível localmente, o objeto `Cache` determinará qual das duas páginas está mais distante das linhas exibidas atualmente e substituirá a página por uma nova, que contém o valor solicitado que, então, é retornado.</span><span class="sxs-lookup"><span data-stu-id="88bb7-134">If the value is not available locally, the `Cache` object determines which of its two pages is farthest from the currently displayed rows and replaces the page with a new one containing the requested value, which it then returns.</span></span>  
  
 <span data-ttu-id="88bb7-135">Supondo que o número de linhas em uma página de dados seja igual ao número de linhas que podem ser exibidas na tela de uma só vez, esse modelo permite que os usuários que estão percorrendo a tabela por paginação retornem para a página exibida mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="88bb7-135">Assuming that the number of rows in a data page is the same as the number of rows that can be displayed on screen at once, this model allows users paging through the table to efficiently return to the most recently viewed page.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a><span data-ttu-id="88bb7-136">Considerações adicionais</span><span class="sxs-lookup"><span data-stu-id="88bb7-136">Additional Considerations</span></span>  
 <span data-ttu-id="88bb7-137">Os exemplos de código anteriores são fornecidos como uma demonstração de carregamento de dados Just-In-Time.</span><span class="sxs-lookup"><span data-stu-id="88bb7-137">The previous code examples are provided as a demonstration of just-in-time data loading.</span></span> <span data-ttu-id="88bb7-138">Você precisará modificar o código de acordo com suas necessidades alcançar a máxima eficiência.</span><span class="sxs-lookup"><span data-stu-id="88bb7-138">You will need to modify the code for your own needs to achieve maximum efficiency.</span></span> <span data-ttu-id="88bb7-139">No mínimo, você precisará escolher um valor apropriado para o número de linhas por página de dados no cache.</span><span class="sxs-lookup"><span data-stu-id="88bb7-139">At minimum, you will need to choose an appropriate value for the number of rows per page of data in the cache.</span></span> <span data-ttu-id="88bb7-140">Esse valor é passado para o construtor `Cache`.</span><span class="sxs-lookup"><span data-stu-id="88bb7-140">This value is passed into the `Cache` constructor.</span></span> <span data-ttu-id="88bb7-141">O número de linhas por página deve ser não menor que o número de linhas que podem ser exibidos simultaneamente no seu <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="88bb7-141">The number of rows per page should be no less than the number of rows that can be displayed simultaneously in your <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="88bb7-142">Para obter melhores resultados, você precisará realizar testes de desempenho e testes de usabilidade para determinar os requisitos do sistema e de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="88bb7-142">For best results, you will need to conduct performance testing and usability testing to determine the requirements of your system and your users.</span></span> <span data-ttu-id="88bb7-143">Os diversos fatores que você precisará levar em consideração incluem a quantidade de memória nas máquinas cliente que executam seu aplicativo, a largura de banda disponível da conexão de rede usada e a latência do servidor usado.</span><span class="sxs-lookup"><span data-stu-id="88bb7-143">Several factors that you will need to take into consideration include the amount of memory in the client machines running your application, the available bandwidth of the network connection used, and the latency of the server used.</span></span> <span data-ttu-id="88bb7-144">A largura de banda e a latência devem ser determinadas em momentos de pico.</span><span class="sxs-lookup"><span data-stu-id="88bb7-144">The bandwidth and latency should be determined at times of peak usage.</span></span>  
  
 <span data-ttu-id="88bb7-145">Para melhorar o desempenho de rolagem do seu aplicativo, você pode aumentar a quantidade de dados armazenados localmente.</span><span class="sxs-lookup"><span data-stu-id="88bb7-145">To improve the scrolling performance of your application, you can increase the amount of data stored locally.</span></span> <span data-ttu-id="88bb7-146">Para melhorar o tempo de inicialização, no entanto, você deve evitar o carregamento de muitos dados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="88bb7-146">To improve startup time, however, you must avoid loading too much data initially.</span></span> <span data-ttu-id="88bb7-147">Talvez você queira modificar a classe `Cache` para aumentar o número de páginas de dados que ela pode armazenar.</span><span class="sxs-lookup"><span data-stu-id="88bb7-147">You may want to modify the `Cache` class to increase the number of data pages it can store.</span></span> <span data-ttu-id="88bb7-148">Usar mais páginas de dados pode melhorar a eficiência de rolagem, mas você precisará determinar o número ideal de linhas em uma página de dados, dependendo da largura de banda disponível e da latência do servidor.</span><span class="sxs-lookup"><span data-stu-id="88bb7-148">Using more data pages can improve scrolling efficiency, but you will need to determine the ideal number of rows in a data page, depending on the available bandwidth and the server latency.</span></span> <span data-ttu-id="88bb7-149">Com páginas menores, o servidor será acessado com mais frequência, mas levará menos tempo para retornar os dados solicitados.</span><span class="sxs-lookup"><span data-stu-id="88bb7-149">With smaller pages, the server will be accessed more frequently, but will take less time to return the requested data.</span></span> <span data-ttu-id="88bb7-150">Se a latência for mais importante que a largura de banda, talvez você queira usar páginas de dados maiores.</span><span class="sxs-lookup"><span data-stu-id="88bb7-150">If latency is more of an issue than bandwidth, you may want to use larger data pages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bb7-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88bb7-151">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [<span data-ttu-id="88bb7-152">Ajuste de desempenho no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-152">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="88bb7-153">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-153">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="88bb7-154">Modo virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-154">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="88bb7-155">Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-155">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [<span data-ttu-id="88bb7-156">Como implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb7-156">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)