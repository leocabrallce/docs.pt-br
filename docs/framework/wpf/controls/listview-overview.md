---
title: "Visão geral de ListView"
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
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62144217199a62da3e41bf381162c94c91d00e72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="listview-overview"></a>Visão geral de ListView
O <xref:System.Windows.Controls.ListView> controle fornece a infraestrutura para exibir um conjunto de itens de dados em diferentes layouts ou modos de exibição. Por exemplo, talvez um usuário queira exibir itens de dados em uma tabela e classificar suas colunas.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>O que é uma ListView?  
 O <xref:System.Windows.Controls.ListView> controle é um <xref:System.Windows.Controls.ItemsControl> que é derivado de <xref:System.Windows.Controls.ListBox>. Normalmente, seus itens são membros de um conjunto de dados e são representados como <xref:System.Windows.Controls.ListViewItem> objetos. Um <xref:System.Windows.Controls.ListViewItem> é um <xref:System.Windows.Controls.ContentControl> e pode conter apenas um único elemento filho. No entanto, esse elemento filho pode ser qualquer elemento visual.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Definindo um modo de exibição para um ListView  
 Para especificar um modo de exibição do conteúdo de um <xref:System.Windows.Controls.ListView> controle, defina o <xref:System.Windows.Controls.ListView.View%2A> propriedade. Um modo de exibição que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece é <xref:System.Windows.Controls.GridView>, que exibe uma coleção de itens de dados em uma tabela que tenha colunas personalizáveis.  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.GridView> para um <xref:System.Windows.Controls.ListView> controle que exibe informações de funcionários.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra como os dados são exibidos no exemplo anterior.  
  
 ![ListView com saída de GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Você pode criar um modo de exibição personalizado definindo uma classe que herda de <xref:System.Windows.Controls.ViewBase> classe. O <xref:System.Windows.Controls.ViewBase> classe fornece a infraestrutura que você precisa criar uma exibição personalizada. Para obter mais informações sobre como criar uma exibição personalizada, consulte [Criar um modo de exibição personalizado para um ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Associando dados a um ListView  
 Use o <xref:System.Windows.Controls.ItemsControl.Items%2A> e <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedades para especificar itens para um <xref:System.Windows.Controls.ListView> controle. O exemplo a seguir define o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade em uma coleção de dados que é chamada `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Em um <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> associam objetos para campos de dados especificado. O exemplo a seguir associa um <xref:System.Windows.Controls.GridViewColumn> objeto para um campo de dados especificando um <xref:System.Windows.Data.Binding> para o <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Você também pode especificar um <xref:System.Windows.Data.Binding> como parte de um <xref:System.Windows.DataTemplate> definição que você usa para estilizar as células em uma coluna. No exemplo a seguir, o <xref:System.Windows.DataTemplate> que é identificado com um <xref:System.Windows.ResourceKey> define o <xref:System.Windows.Data.Binding> para um <xref:System.Windows.Controls.GridViewColumn>. Observe que esse exemplo define o <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> porque isso substitui a associação especificada pelo <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Estilizando uma ListView que implemente um GridView  
 O <xref:System.Windows.Controls.ListView> controle contém <xref:System.Windows.Controls.ListViewItem> objetos que representam os itens de dados que são exibidos. Você pode usar as propriedades a seguir para definir o conteúdo e estilo de itens de dados:  
  
-   Sobre o <xref:System.Windows.Controls.ListView> controlar, use o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, e <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> propriedades.  
  
-   Sobre o <xref:System.Windows.Controls.ListViewItem> controlar, use o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> e <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> propriedades.  
  
 Para evitar problemas de alinhamento entre as células de uma <xref:System.Windows.Controls.GridView>, não use o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para definir propriedades ou adicionar conteúdo que afeta a largura de um item em uma <xref:System.Windows.Controls.ListView>. Por exemplo, um problema de alinhamento pode ocorrer quando você define o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Para especificar propriedades ou definir o conteúdo que afeta a largura de itens em uma <xref:System.Windows.Controls.GridView>, use as propriedades do <xref:System.Windows.Controls.GridView> e suas classes relacionadas, como <xref:System.Windows.Controls.GridViewColumn>.  
  
 Para obter mais informações sobre como usar <xref:System.Windows.Controls.GridView> e suas classes de suporte, consulte [visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Se você definir um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para um <xref:System.Windows.Controls.ListView> de controle e também definir um <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, você deve incluir um <xref:System.Windows.Controls.ContentPresenter> no estilo na ordem para o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> funcione corretamente.  
  
 Não use o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> e <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriedades <xref:System.Windows.Controls.ListView> conteúdo que é exibido usando um <xref:System.Windows.Controls.GridView>. Para especificar o alinhamento do conteúdo em uma coluna de uma <xref:System.Windows.Controls.GridView>, definir um <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Compartilhando o mesmo modo de exibição  
 Dois <xref:System.Windows.Controls.ListView> controles não podem compartilhar o mesmo modo de exibição ao mesmo tempo. Se você tentar usar o mesmo modo de exibição com mais de um <xref:System.Windows.Controls.ListView> controlar, ocorre uma exceção.  
  
 Para especificar um modo de exibição que pode ser usado simultaneamente por mais de um <xref:System.Windows.Controls.ListView>, use modelos ou estilos. Para obter um exemplo de como definir modos de exibição como <xref:System.Windows.FrameworkElement.Resources%2A>, consulte [ListView com exemplo de vários modos de exibição](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Criando um modo de exibição personalizada  
 Exibições personalizadas como <xref:System.Windows.Controls.GridView> derivam o <xref:System.Windows.Controls.ViewBase> abstrato de classe, que fornece as ferramentas para exibir itens de dados que são representados como <xref:System.Windows.Controls.ListViewItem> objetos.  
  
 Para obter um exemplo de um modo de exibição personalizado, consulte [ListView com várias exibições de exemplo](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Controles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
