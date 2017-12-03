---
title: "Instruções passo a passo: criando um controle ToolStrip com estilo profissional"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fbc03ad16bcc0d63a75df5478f7da8abbf19193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="8d393-102">Instruções passo a passo: criando um controle ToolStrip com estilo profissional</span><span class="sxs-lookup"><span data-stu-id="8d393-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="8d393-103">Você pode dar a seu aplicativo <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional e o comportamento ao escrever sua própria classe que deriva de <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tipo.</span><span class="sxs-lookup"><span data-stu-id="8d393-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="8d393-104">Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStrip> controles para criar um controle composto é semelhante a **painel de navegação** fornecidas pelo Microsoft® Outlook.</span><span class="sxs-lookup"><span data-stu-id="8d393-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="8d393-105">As seguintes tarefas são ilustradas nesta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="8d393-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="8d393-106">Criar um projeto da Biblioteca de Controle do Windows.</span><span class="sxs-lookup"><span data-stu-id="8d393-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="8d393-107">Projetar o controle StackView.</span><span class="sxs-lookup"><span data-stu-id="8d393-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="8d393-108">Implementar um renderizador personalizado.</span><span class="sxs-lookup"><span data-stu-id="8d393-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="8d393-109">Quando tiver terminado, você terá um controle de cliente personalizado reutilizável com a aparência profissional de um controle do Microsoft Office XP.</span><span class="sxs-lookup"><span data-stu-id="8d393-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="8d393-110">Para copiar o código neste tópico como uma única lista, consulte [Como criar um controle ToolStrip com estilo profissional](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="8d393-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d393-111">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8d393-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8d393-112">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8d393-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8d393-113">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8d393-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8d393-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8d393-114">Prerequisites</span></span>  
 <span data-ttu-id="8d393-115">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="8d393-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="8d393-116">Permissões suficientes para poder criar e executar projetos de Aplicativo dos Windows Forms no computador no qual [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] está instalado.</span><span class="sxs-lookup"><span data-stu-id="8d393-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="8d393-117">Criar um projeto da Biblioteca de Controle do Windows</span><span class="sxs-lookup"><span data-stu-id="8d393-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="8d393-118">A primeira etapa é criar o projeto de biblioteca de controles.</span><span class="sxs-lookup"><span data-stu-id="8d393-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="8d393-119">Para criar o projeto de biblioteca de controles</span><span class="sxs-lookup"><span data-stu-id="8d393-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="8d393-120">Crie um novo projeto da Biblioteca de Controle do Windows chamado `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="8d393-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="8d393-121">No **Gerenciador de Soluções**, exclua o controle padrão do projeto excluindo o arquivo de origem denominado "UserControl1.cs" ou "UserControl1.vb", dependendo da linguagem de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="8d393-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="8d393-122">Para obter mais informações, consulte [NIB: como remover, apagar e excluir itens](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="8d393-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="8d393-123">Adicionar um novo <xref:System.Windows.Forms.UserControl> item para o **StackViewLibrary** projeto.</span><span class="sxs-lookup"><span data-stu-id="8d393-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="8d393-124">Dê ao novo arquivo de origem o nome base `StackView`.</span><span class="sxs-lookup"><span data-stu-id="8d393-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="8d393-125">Projetar o controle StackView</span><span class="sxs-lookup"><span data-stu-id="8d393-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="8d393-126">O `StackView` é um controle composto com um filho <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="8d393-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="8d393-127">Para obter mais informações sobre controles de composição, consulte [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8d393-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="8d393-128">Para projetar o controle StackView</span><span class="sxs-lookup"><span data-stu-id="8d393-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="8d393-129">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStrip> controle à superfície de design.</span><span class="sxs-lookup"><span data-stu-id="8d393-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="8d393-130">No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolStrip> propriedades do controle de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d393-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="8d393-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8d393-131">Property</span></span>|<span data-ttu-id="8d393-132">Valor</span><span class="sxs-lookup"><span data-stu-id="8d393-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="8d393-133">Nome</span><span class="sxs-lookup"><span data-stu-id="8d393-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="8d393-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="8d393-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="8d393-135">Encaixar</span><span class="sxs-lookup"><span data-stu-id="8d393-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="8d393-136">Fonte</span><span class="sxs-lookup"><span data-stu-id="8d393-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="8d393-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="8d393-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="8d393-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="8d393-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="8d393-139">Enchimento</span><span class="sxs-lookup"><span data-stu-id="8d393-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="8d393-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="8d393-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="8d393-141">No Designer de formulários do Windows, clique no <xref:System.Windows.Forms.ToolStrip> do controle **adicionar** botão e adicione um <xref:System.Windows.Forms.ToolStripButton> para o `stackStrip` controle.</span><span class="sxs-lookup"><span data-stu-id="8d393-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="8d393-142">No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolStripButton> propriedades do controle de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d393-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="8d393-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8d393-143">Property</span></span>|<span data-ttu-id="8d393-144">Valor</span><span class="sxs-lookup"><span data-stu-id="8d393-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="8d393-145">Nome</span><span class="sxs-lookup"><span data-stu-id="8d393-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="8d393-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="8d393-146">CheckOnClick</span></span>|<span data-ttu-id="8d393-147">true</span><span class="sxs-lookup"><span data-stu-id="8d393-147">true</span></span>|  
    |<span data-ttu-id="8d393-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="8d393-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="8d393-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="8d393-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="8d393-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="8d393-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="8d393-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="8d393-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="8d393-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="8d393-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="8d393-153">Margem</span><span class="sxs-lookup"><span data-stu-id="8d393-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="8d393-154">Enchimento</span><span class="sxs-lookup"><span data-stu-id="8d393-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="8d393-155">Texto</span><span class="sxs-lookup"><span data-stu-id="8d393-155">Text</span></span>|<span data-ttu-id="8d393-156">**Email**</span><span class="sxs-lookup"><span data-stu-id="8d393-156">**Mail**</span></span>|  
    |<span data-ttu-id="8d393-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="8d393-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="8d393-158">Repita a etapa 7 para três mais <xref:System.Windows.Forms.ToolStripButton> controles.</span><span class="sxs-lookup"><span data-stu-id="8d393-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="8d393-159">Nomeie os controles como `calendarStackButton`, `contactsStackButton` e `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="8d393-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="8d393-160">Defina o valor da <xref:System.Windows.Forms.Control.Text%2A> propriedade **calendário**, **contatos**, e **tarefas**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8d393-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="8d393-161">Tratando eventos</span><span class="sxs-lookup"><span data-stu-id="8d393-161">Handling Events</span></span>  
 <span data-ttu-id="8d393-162">Dois eventos são importantes para fazer com que o controle `StackView` se comporte corretamente.</span><span class="sxs-lookup"><span data-stu-id="8d393-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="8d393-163">Manipular o <xref:System.Windows.Forms.UserControl.Load> evento para posicionar o controle corretamente.</span><span class="sxs-lookup"><span data-stu-id="8d393-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="8d393-164">Manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para cada <xref:System.Windows.Forms.ToolStripButton> para dar o `StackView` controlar o comportamento semelhante do estado a <xref:System.Windows.Forms.RadioButton> controle.</span><span class="sxs-lookup"><span data-stu-id="8d393-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="8d393-165">Para manipular eventos</span><span class="sxs-lookup"><span data-stu-id="8d393-165">To handle events</span></span>  
  
1.  <span data-ttu-id="8d393-166">No Designer de Formulários do Windows, selecione o controle `StackView`.</span><span class="sxs-lookup"><span data-stu-id="8d393-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="8d393-167">Na janela **Propriedades**, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="8d393-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="8d393-168">Clique duas vezes no evento Carregar para gerar o manipulador de eventos `StackView_Load`.</span><span class="sxs-lookup"><span data-stu-id="8d393-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="8d393-169">No manipulador de eventos `StackView_Load`, copie e cole o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d393-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="8d393-170">No Designer de Formulários do Windows, selecione o controle `mailStackButton`.</span><span class="sxs-lookup"><span data-stu-id="8d393-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="8d393-171">Na janela **Propriedades**, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="8d393-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="8d393-172">Clique duas vezes no evento Clique.</span><span class="sxs-lookup"><span data-stu-id="8d393-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="8d393-173">O Designer de Formulários do Windows gera o manipulador de eventos `mailStackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8d393-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="8d393-174">Renomeie o manipulador de eventos `mailStackButton_Click` como `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8d393-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="8d393-175">Para obter mais informações, consulte [Como renomear um identificador (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="8d393-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="8d393-176">Adicione o seguinte código ao manipulador de eventos `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8d393-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="8d393-177">No Designer de Formulários do Windows, selecione o controle `calendarStackButton`.</span><span class="sxs-lookup"><span data-stu-id="8d393-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="8d393-178">Na janela **Propriedades**, defina o evento Clique para o manipulador de eventos `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8d393-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="8d393-179">Repita as etapas 10 e 11 para os controles `contactsStackButton` e `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="8d393-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="8d393-180">Definindo ícones</span><span class="sxs-lookup"><span data-stu-id="8d393-180">Defining Icons</span></span>  
 <span data-ttu-id="8d393-181">Cada botão `StackView` tem um ícone associado.</span><span class="sxs-lookup"><span data-stu-id="8d393-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="8d393-182">Para sua conveniência, cada ícone é representado como uma cadeia de caracteres codificada em Base64, que é desserializado antes de um <xref:System.Drawing.Bitmap> é criado a partir dele.</span><span class="sxs-lookup"><span data-stu-id="8d393-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="8d393-183">Em um ambiente de produção, armazene dados de bitmap como um recurso e seus ícones serão exibidos no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="8d393-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="8d393-184">Para obter mais informações, consulte [Como adicionar imagens de tela de fundo ao Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="8d393-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="8d393-185">Para definir ícones</span><span class="sxs-lookup"><span data-stu-id="8d393-185">To define icons</span></span>  
  
1.  <span data-ttu-id="8d393-186">No Editor de Códigos, insira o seguinte código na definição de classe `StackView`.</span><span class="sxs-lookup"><span data-stu-id="8d393-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="8d393-187">Esse código inicializa os bitmaps para o <xref:System.Windows.Forms.ToolStripButton> ícones.</span><span class="sxs-lookup"><span data-stu-id="8d393-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="8d393-188">Adicione uma chamada ao método `InitializeImages` no construtor de classe `StackView`.</span><span class="sxs-lookup"><span data-stu-id="8d393-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="8d393-189">Implementar um renderizador personalizado</span><span class="sxs-lookup"><span data-stu-id="8d393-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="8d393-190">Você pode personalizar a maioria dos elementos do `StackView` controle meu implementando uma classe que deriva de <xref:System.Windows.Forms.ToolStripRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="8d393-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="8d393-191">Neste procedimento, você irá implementar um <xref:System.Windows.Forms.ToolStripProfessionalRenderer> classe que personaliza a alça e desenha gradientes planos de fundo para o <xref:System.Windows.Forms.ToolStripButton> controles.</span><span class="sxs-lookup"><span data-stu-id="8d393-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="8d393-192">Para implementar um renderizador personalizado</span><span class="sxs-lookup"><span data-stu-id="8d393-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="8d393-193">Insira o seguinte código na definição de controle `StackView`.</span><span class="sxs-lookup"><span data-stu-id="8d393-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="8d393-194">Esta é a definição para o `StackRenderer` de classe que substitui o <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, e <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> métodos para produzir uma aparência personalizada.</span><span class="sxs-lookup"><span data-stu-id="8d393-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="8d393-195">No `StackView` construtor do controle, crie uma nova instância do `StackRenderer` classe e atribuir essa instância para o `stackStrip` do controle <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d393-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="8d393-196">Testando o controle StackView</span><span class="sxs-lookup"><span data-stu-id="8d393-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="8d393-197">O `StackView` controle deriva o <xref:System.Windows.Forms.UserControl> classe.</span><span class="sxs-lookup"><span data-stu-id="8d393-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="8d393-198">Portanto, você pode testar o controle com o **Contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8d393-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="8d393-199">Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).</span><span class="sxs-lookup"><span data-stu-id="8d393-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="8d393-200">Para testar o controle StackView</span><span class="sxs-lookup"><span data-stu-id="8d393-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="8d393-201">Pressione F5 para compilar o projeto e iniciar o **Contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8d393-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="8d393-202">Mova o ponteiro sobre os botões do controle `StackView` e, em seguida, clique em um botão para ver a aparência de seu estado selecionado.</span><span class="sxs-lookup"><span data-stu-id="8d393-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8d393-203">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8d393-203">Next Steps</span></span>  
 <span data-ttu-id="8d393-204">Neste passo a passo, você criou controle de cliente personalizado reutilizável com a aparência profissional de um controle do Office XP.</span><span class="sxs-lookup"><span data-stu-id="8d393-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="8d393-205">Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="8d393-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="8d393-206">Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8d393-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="8d393-207">Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8d393-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="8d393-208">Criar um formulário com um menu padrão preenchido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8d393-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="8d393-209">Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="8d393-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="8d393-210">Criar um formulário de interface MDI vários documentos com encaixe <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="8d393-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="8d393-211">Para obter mais informações, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8d393-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d393-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d393-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="8d393-213">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8d393-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="8d393-214">Como fornecer itens de menu padrão para um formulário</span><span class="sxs-lookup"><span data-stu-id="8d393-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)