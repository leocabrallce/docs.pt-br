---
title: Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c80bd12db83284c30f637f48dfc09e7de22280b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="14011-102">Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="14011-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="14011-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="14011-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="14011-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="14011-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="14011-105">Você pode exibir dados em Windows Forms <xref:System.Windows.Forms.DataGrid> controle em tabelas e colunas criando <xref:System.Windows.Forms.DataGridTableStyle> objetos e adicioná-los para o <xref:System.Windows.Forms.GridTableStylesCollection> objeto, que é acessado por meio de <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14011-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating <xref:System.Windows.Forms.DataGridTableStyle> objects and adding them to the <xref:System.Windows.Forms.GridTableStylesCollection> object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.TableStyles%2A> property.</span></span> <span data-ttu-id="14011-106">Cada estilo de tabela exibe o conteúdo de qualquer tabela de dados é especificada no <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade o <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="14011-106">Each table style displays the contents of whatever data table is specified in the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle>.</span></span> <span data-ttu-id="14011-107">Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados.</span><span class="sxs-lookup"><span data-stu-id="14011-107">By default, a table style without column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="14011-108">Você pode restringir quais colunas da tabela aparecem adicionando <xref:System.Windows.Forms.DataGridColumnStyle> objetos para o <xref:System.Windows.Forms.GridColumnStylesCollection>, que é acessado por meio de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade de cada <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="14011-108">You can restrict which columns from the table appear by adding <xref:System.Windows.Forms.DataGridColumnStyle> objects to the <xref:System.Windows.Forms.GridColumnStylesCollection>, which is accessed through the <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> property of each <xref:System.Windows.Forms.DataGridTableStyle>.</span></span>  
  
 <span data-ttu-id="14011-109">Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="14011-109">The following procedures require a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="14011-110">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="14011-110">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="14011-111">Por padrão em [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], o <xref:System.Windows.Forms.DataGrid> controle não está no **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="14011-111">By default in [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox**.</span></span> <span data-ttu-id="14011-112">Para obter informações sobre como adicioná-lo, consulte [Como Adicionar Itens à Caixa de Ferramentas](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span><span class="sxs-lookup"><span data-stu-id="14011-112">For information about adding it, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14011-113">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="14011-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14011-114">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="14011-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14011-115">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="14011-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a><span data-ttu-id="14011-116">Para adicionar uma tabela ao controle DataGrid no designer</span><span class="sxs-lookup"><span data-stu-id="14011-116">To add a table to the DataGrid control in the designer</span></span>  
  
1.  <span data-ttu-id="14011-117">Para exibir os dados na tabela, você deve primeiro associar o <xref:System.Windows.Forms.DataGrid> controle a um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="14011-117">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="14011-118">Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados usando o designer](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="14011-118">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="14011-119">Selecione o <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade na janela Propriedades e, em seguida, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de a propriedade para exibir o **DataGridTableStyle Collection Editor**.</span><span class="sxs-lookup"><span data-stu-id="14011-119">Select the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.TableStyles%2A> property in the Properties window, and then click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the property to display the **DataGridTableStyle Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="14011-120">No editor de coleção, clique em **Adicionar** para inserir um estilo de tabela.</span><span class="sxs-lookup"><span data-stu-id="14011-120">In the collection editor, click **Add** to insert a table style.</span></span>  
  
4.  <span data-ttu-id="14011-121">Clique em **Okey** para fechar o editor de coleção e, em seguida, reabra-o clicando no botão de reticências ao lado de <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14011-121">Click **OK** to close the collection editor, and then reopen it by clicking the ellipsis button next to the <xref:System.Windows.Forms.DataGrid.TableStyles%2A> property.</span></span>  
  
     <span data-ttu-id="14011-122">Quando você reabrir o editor de coleção, nenhuma tabela de dados associada ao controle aparecerá na lista suspensa para o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade de estilo de tabela.</span><span class="sxs-lookup"><span data-stu-id="14011-122">When you reopen the collection editor, any data tables bound to the control will appear in the drop-down list for the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the table style.</span></span>  
  
5.  <span data-ttu-id="14011-123">Na caixa **Membros** do editor de coleção, clique no estilo de tabela.</span><span class="sxs-lookup"><span data-stu-id="14011-123">In the **Members** box of the collection editor, click the table style.</span></span>  
  
6.  <span data-ttu-id="14011-124">No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> valor para a tabela que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="14011-124">In the **Properties** box of the collection editor, select the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> value for the table you want to display.</span></span>  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a><span data-ttu-id="14011-125">Para adicionar uma coluna ao controle DataGrid no designer</span><span class="sxs-lookup"><span data-stu-id="14011-125">To add a column to the DataGrid control in the designer</span></span>  
  
1.  <span data-ttu-id="14011-126">Na caixa **Membros** do **Editor de Coleção DataGridTableStyle**, selecione o estilo de tabela adequado.</span><span class="sxs-lookup"><span data-stu-id="14011-126">In the **Members** box of the **DataGridTableStyle Collection Editor**, select the appropriate table style.</span></span> <span data-ttu-id="14011-127">No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção e, em seguida, clique no botão de reticências (![de tela de VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) ao lado da propriedade para exibir o **DataGridColumnStyle Collection Editor**.</span><span class="sxs-lookup"><span data-stu-id="14011-127">In the **Properties** box of the collection editor, select the <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, and then click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the property to display the **DataGridColumnStyle Collection Editor**.</span></span>  
  
2.  <span data-ttu-id="14011-128">No editor de coleção, clique em **Adicionar** para inserir um estilo de coluna ou clique na seta para baixo ao lado de **Adicionar** para especificar um tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="14011-128">In the collection editor, click **Add** to insert a column style or click the down arrow next to **Add** to specify a column type.</span></span>  
  
     <span data-ttu-id="14011-129">Na caixa suspensa, você pode selecionar o <xref:System.Windows.Forms.DataGridTextBoxColumn> ou <xref:System.Windows.Forms.DataGridBoolColumn> tipo.</span><span class="sxs-lookup"><span data-stu-id="14011-129">In the drop-down box, you can select either the <xref:System.Windows.Forms.DataGridTextBoxColumn> or <xref:System.Windows.Forms.DataGridBoolColumn> type.</span></span>  
  
3.  <span data-ttu-id="14011-130">Clique em Okey para fechar o **DataGridColumnStyle Collection Editor**e, em seguida, reabra-o clicando no botão de reticências ao lado de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14011-130">Click OK to close the **DataGridColumnStyle Collection Editor**, and then reopen it by clicking the ellipsis button next to the <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> property.</span></span>  
  
     <span data-ttu-id="14011-131">Quando você reabrir o editor de coleção, quaisquer colunas de dados na tabela de dados associada serão exibido na lista suspensa para o <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriedade do estilo de coluna.</span><span class="sxs-lookup"><span data-stu-id="14011-131">When you reopen the collection editor, any data columns in the bound data table will appear in the drop-down list for the <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> property of the column style.</span></span>  
  
4.  <span data-ttu-id="14011-132">Na caixa **Membros** do editor de coleção, clique no estilo de coluna.</span><span class="sxs-lookup"><span data-stu-id="14011-132">In the **Members** box of the collection editor, click the column style.</span></span>  
  
5.  <span data-ttu-id="14011-133">No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valor para a coluna que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="14011-133">In the **Properties** box of the collection editor, select the <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> value for the column you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14011-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14011-134">See Also</span></span>  
 [<span data-ttu-id="14011-135">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="14011-135">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="14011-136">Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14011-136">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)