---
title: "Instruções passo a passo: demonstrando herança visual"
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
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 711f823e418a1bbea1479b9d6a8d70d4fa506365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="edc8b-102">Instruções passo a passo: demonstrando herança visual</span><span class="sxs-lookup"><span data-stu-id="edc8b-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="edc8b-103">A herança visual permite que você veja os controles no formulário de base e adicione novos controles.</span><span class="sxs-lookup"><span data-stu-id="edc8b-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="edc8b-104">Neste passo a passo, você criará um formulário de base e o compilará em uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="edc8b-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="edc8b-105">Você importará esta biblioteca de classes em outro projeto e criará um novo formulário que herda do formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="edc8b-106">Durante este passo a passo, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="edc8b-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="edc8b-107">Criar um projeto de biblioteca de classes que contém um formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="edc8b-108">Adicionar um botão com propriedades que as classes derivadas do formulário de base podem modificar.</span><span class="sxs-lookup"><span data-stu-id="edc8b-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="edc8b-109">Adicionar um botão que não pode ser modificado por herdeiros do formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="edc8b-110">Criar um projeto que contém um formulário que herda de `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="edc8b-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="edc8b-111">Por fim, este passo a passo demonstrará a diferença entre controles particulares e protegidos em um formulário herdado.</span><span class="sxs-lookup"><span data-stu-id="edc8b-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edc8b-112">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="edc8b-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="edc8b-113">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="edc8b-114">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="edc8b-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="edc8b-115">Nem todos os controles dão suporte à herança visual de um formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="edc8b-116">Os seguintes controles não dão suporte ao cenário descrito neste passo a passo:</span><span class="sxs-lookup"><span data-stu-id="edc8b-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  <span data-ttu-id="edc8b-117">Esses controles no formulário herdado sempre são somente leitura, independentemente dos modificadores que você usar (`private`, `protected` ou `public`).</span><span class="sxs-lookup"><span data-stu-id="edc8b-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="edc8b-118">Etapas do cenário</span><span class="sxs-lookup"><span data-stu-id="edc8b-118">Scenario Steps</span></span>  
 <span data-ttu-id="edc8b-119">A primeira etapa é criar o formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="edc8b-120">Para criar um projeto de biblioteca de classes que contém um formulário de base</span><span class="sxs-lookup"><span data-stu-id="edc8b-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="edc8b-121">No menu **Arquivo**, escolha **Novo** e selecione **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="edc8b-122">Crie um aplicativo dos Windows Forms chamado `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="edc8b-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="edc8b-123">Para criar uma biblioteca de classes em vez de um aplicativo padrão dos Windows Forms, no **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto **BaseFormLibrary** e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="edc8b-124">Nas propriedades do projeto, altere o **Tipo de saída** de **Aplicativo do Windows** para **Biblioteca de Classes**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="edc8b-125">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto e os arquivos no local padrão.</span><span class="sxs-lookup"><span data-stu-id="edc8b-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="edc8b-126">Os dois procedimentos seguintes adicionam botões ao formulário de base.</span><span class="sxs-lookup"><span data-stu-id="edc8b-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="edc8b-127">Para demonstrar a herança visual, você dará aos botões diferentes níveis de acesso configurando suas propriedades `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="edc8b-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="edc8b-128">Para adicionar um botão que os herdeiros do formulário de base podem modificar</span><span class="sxs-lookup"><span data-stu-id="edc8b-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="edc8b-129">Abra **Form1** no designer.</span><span class="sxs-lookup"><span data-stu-id="edc8b-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="edc8b-130">Na guia **Todos os Windows Forms** da **Caixa de Ferramentas**, clique duas vezes em **Botão** para adicionar um botão ao formulário.</span><span class="sxs-lookup"><span data-stu-id="edc8b-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="edc8b-131">Use o mouse para posicionar e redimensionar o botão.</span><span class="sxs-lookup"><span data-stu-id="edc8b-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="edc8b-132">Na janela Propriedades, defina as seguintes propriedades do botão:</span><span class="sxs-lookup"><span data-stu-id="edc8b-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="edc8b-133">Defina a propriedade **Texto** como **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="edc8b-134">Defina a propriedade **(Nome)** como **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="edc8b-135">Defina a propriedade **Modificadores** como **Protegido**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="edc8b-136">Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="edc8b-137">Clique duas vezes no botão **Say Hello** para adicionar um manipulador de eventos para o evento **Clique**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="edc8b-138">Adicione a seguinte linha de código ao manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="edc8b-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="edc8b-139">Para adicionar um botão que não pode ser modificado por herdeiros do formulário de base</span><span class="sxs-lookup"><span data-stu-id="edc8b-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="edc8b-140">Passe para o modo de exibição de Design clicando na guia **Form1.vb [Design], Form1.cs [Design] ou Form1.jsl [Design]** acima do editor de código ou pressionando F7.</span><span class="sxs-lookup"><span data-stu-id="edc8b-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="edc8b-141">Adicione um segundo botão e defina suas propriedades da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="edc8b-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="edc8b-142">Defina a propriedade **Texto** como **Say Goodbye**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="edc8b-143">Defina a propriedade **(Nome)** como **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="edc8b-144">Defina a propriedade **(Nome)** como **Particular**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="edc8b-145">Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="edc8b-146">Clique duas vezes no botão **Say Goodbye** para adicionar um manipulador de eventos para o evento **Clique**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="edc8b-147">Coloque a seguinte linha de código no procedimento do evento:</span><span class="sxs-lookup"><span data-stu-id="edc8b-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="edc8b-148">Do menu **Compilação**, escolha **Compilar Biblioteca de BaseForm** para compilar a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="edc8b-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="edc8b-149">Após a biblioteca ter sido compilada, você pode criar um novo projeto que herda do formulário que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="edc8b-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="edc8b-150">Para criar um projeto que contém um formulário que herda do formulário de base</span><span class="sxs-lookup"><span data-stu-id="edc8b-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="edc8b-151">No menu **Arquivo**, escolha **Adicionar** e selecione **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="edc8b-152">Crie um aplicativo dos Windows Forms chamado `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="edc8b-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="edc8b-153">Para adicionar um formulário herdado</span><span class="sxs-lookup"><span data-stu-id="edc8b-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="edc8b-154">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest**, selecione **Adicionar** e selecione **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="edc8b-155">Na caixa de diálogo **Adicionar Novo Item**, selecione a categoria **Windows Forms** (se você tiver uma lista de categorias) e selecione o modelo **Formulário Herdado**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="edc8b-156">Deixe o nome padrão `Form2` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="edc8b-157">Na caixa de diálogo **Selecionador de Herança**, selecione **Form1** do projeto **BaseFormLibrary** como o formulário do qual herdar e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="edc8b-158">Isso cria um formulário no projeto **InheritanceTest** que deriva de formulário em **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="edc8b-159">Abra o formulário herdado (**Form2**) no designer clicando duas vezes nele, se ele ainda não estiver aberto.</span><span class="sxs-lookup"><span data-stu-id="edc8b-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="edc8b-160">No designer, os botões herdados têm um símbolo (![Captura de tela de VisualBasicInheritanceSymbol](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) no canto superior, indicando que são herdados.</span><span class="sxs-lookup"><span data-stu-id="edc8b-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="edc8b-161">Selecione o botão **Say Hello** e observe as alças de redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="edc8b-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="edc8b-162">Como esse botão é protegido, os herdeiros podem movê-lo, redimensioná-lo, alterar sua legenda e fazer outras modificações.</span><span class="sxs-lookup"><span data-stu-id="edc8b-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="edc8b-163">Selecione o botão particular **Say Goodbye** e observe que ele não tem alças de redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="edc8b-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="edc8b-164">Além disso, na janela **Propriedades**, as propriedades deste botão ficam cinza para indicar que não podem ser modificadas.</span><span class="sxs-lookup"><span data-stu-id="edc8b-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="edc8b-165">Se você estiver usando [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="edc8b-165">If you are using [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="edc8b-166">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1** no projeto **InheritanceTest** e selecione **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="edc8b-167">Na caixa de mensagem que aparece, clique em **OK** para confirmar a exclusão.</span><span class="sxs-lookup"><span data-stu-id="edc8b-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="edc8b-168">Abra o arquivo Program.cs e altere a linha `Application.Run(new Form1());` para `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="edc8b-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="edc8b-169">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="edc8b-170">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="edc8b-171">Na página de propriedades de **InheritanceTest**, defina o **Objeto de Inicialização** para ser o formulário herdado (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="edc8b-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="edc8b-172">Pressione F5 para executar o aplicativo e observe o comportamento do formulário herdado.</span><span class="sxs-lookup"><span data-stu-id="edc8b-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="edc8b-173">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="edc8b-173">Next Steps</span></span>  
 <span data-ttu-id="edc8b-174">A herança para controles de usuário funciona basicamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="edc8b-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="edc8b-175">Abra um novo projeto de biblioteca de classes e adicione um controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="edc8b-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="edc8b-176">Coloque os controles constituintes nele e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="edc8b-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="edc8b-177">Abra outro novo projeto de biblioteca de classes e adicione uma referência à biblioteca de classes compilada.</span><span class="sxs-lookup"><span data-stu-id="edc8b-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="edc8b-178">Além disso, tente adicionar um controle herdado (por meio da caixa de diálogo **Adicionar Novos Itens**) ao projeto e usar o **Selecionador de Herança**.</span><span class="sxs-lookup"><span data-stu-id="edc8b-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="edc8b-179">Adicione um controle de usuário e alterar a instrução `Inherits` (`:` em [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="edc8b-179">Add a user control, and change the `Inherits` (`:` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) statement.</span></span> <span data-ttu-id="edc8b-180">Para mais informações, consulte [Como herdar Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="edc8b-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc8b-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edc8b-181">See Also</span></span>  
 [<span data-ttu-id="edc8b-182">Como Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edc8b-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="edc8b-183">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edc8b-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="edc8b-184">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edc8b-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)