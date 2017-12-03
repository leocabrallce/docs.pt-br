---
title: "Como associar a um serviço Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d1b81949d6d91420c828564debd311af47dfdfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="9bc82-102">Como associar a um serviço Web</span><span class="sxs-lookup"><span data-stu-id="9bc82-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="9bc82-103">Este exemplo mostra como associar a objetos retornados por chamadas de método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="9bc82-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc82-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bc82-104">Example</span></span>  
 <span data-ttu-id="9bc82-105">Este exemplo usa o [serviço de conteúdo de sistema de publicação MSDN/TechNet (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) para recuperar a lista de idiomas com suporte de um documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9bc82-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="9bc82-106">Antes de chamar um serviço Web, é necessário criar uma referência a ele.</span><span class="sxs-lookup"><span data-stu-id="9bc82-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="9bc82-107">Para criar uma referência Web ao serviço MTPS usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], siga as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="9bc82-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="9bc82-108">Abra o projeto no [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bc82-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="9bc82-109">No menu **Projeto**, clique em **Adicionar referência Web**.</span><span class="sxs-lookup"><span data-stu-id="9bc82-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="9bc82-110">Na caixa de diálogo, defina o **URL** como [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="9bc82-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="9bc82-111">Pressione **Ir** e, em seguida, **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="9bc82-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="9bc82-112">Em seguida, chame o método de serviço Web e defina o <xref:System.Windows.FrameworkElement.DataContext%2A> do controle apropriado ou da janela para o objeto retornado.</span><span class="sxs-lookup"><span data-stu-id="9bc82-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="9bc82-113">O método **GetContent** do serviço MTPS utiliza uma referência para o objeto **getContentRequest**.</span><span class="sxs-lookup"><span data-stu-id="9bc82-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="9bc82-114">Portanto, o exemplo a seguir primeiro define um objeto de solicitação:</span><span class="sxs-lookup"><span data-stu-id="9bc82-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="9bc82-115">Após o <xref:System.Windows.FrameworkElement.DataContext%2A> tiver sido definido, você pode criar associações com as propriedades do objeto que o <xref:System.Windows.FrameworkElement.DataContext%2A> foi definido como.</span><span class="sxs-lookup"><span data-stu-id="9bc82-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="9bc82-116">Neste exemplo, o <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como o **getContentResponse** objeto retornado pelo **GetContent** método.</span><span class="sxs-lookup"><span data-stu-id="9bc82-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="9bc82-117">No exemplo a seguir, o <xref:System.Windows.Controls.ItemsControl> associa e exibe o **localidade** valores de **availableVersionsAndLocales** de **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="9bc82-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="9bc82-118">Para obter informações sobre a estrutura de **getContentResponse**, consulte a [Documentação do serviço de conteúdo](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="9bc82-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc82-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bc82-119">See Also</span></span>  
 [<span data-ttu-id="9bc82-120">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="9bc82-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9bc82-121">Visão geral das origens da associação</span><span class="sxs-lookup"><span data-stu-id="9bc82-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="9bc82-122">Disponibilizar dados para associação em XAML</span><span class="sxs-lookup"><span data-stu-id="9bc82-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)