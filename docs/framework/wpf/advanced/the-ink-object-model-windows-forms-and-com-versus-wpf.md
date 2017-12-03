---
title: 'O modelo de objeto Ink: Windows Forms e COM versus WPF'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a82647d16536c9d7b49185461e91de03005cacda
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a><span data-ttu-id="efc9d-102">O modelo de objeto Ink: Windows Forms e COM versus WPF</span><span class="sxs-lookup"><span data-stu-id="efc9d-102">The Ink Object Model: Windows Forms and COM versus WPF</span></span>

<span data-ttu-id="efc9d-103">Há basicamente três plataformas que dão suporte à tinta digital: a plataforma Tablet PC Windows Forms, a plataforma Tablet PC COM e a plataforma [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efc9d-103">There are essentially three platforms that support digital ink: the Tablet PC Windows Forms platform, the Tablet PC COM platform, and the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] platform.</span></span>  <span data-ttu-id="efc9d-104">As plataformas Windows Forms e COM compartilham um modelo de objeto semelhante, mas o modelo de objeto para a plataforma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é significativamente diferente.</span><span class="sxs-lookup"><span data-stu-id="efc9d-104">The Windows Forms and COM platforms share a similar object model, but the object model for the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform is substantially different.</span></span>  <span data-ttu-id="efc9d-105">Este tópico discute as diferenças em um alto nível para que os desenvolvedores que trabalharam com um modelo de objetos possam entender o outro.</span><span class="sxs-lookup"><span data-stu-id="efc9d-105">This topic discusses the differences at a high-level so that developers that have worked with one object model can better understand the other.</span></span>  
  
## <a name="enabling-ink-in-an-application"></a><span data-ttu-id="efc9d-106">Habilitando o Ink em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="efc9d-106">Enabling Ink in an Application</span></span>  
 <span data-ttu-id="efc9d-107">Todas as três plataformas vêm com objetos e controles que permitem que um aplicativo receba entrada de uma caneta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="efc9d-107">All three platforms ship objects and controls that enable an application to receive input from a tablet pen.</span></span>  <span data-ttu-id="efc9d-108">As plataformas Windows Forms e COM acompanham [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) e [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) classes.</span><span class="sxs-lookup"><span data-stu-id="efc9d-108">The Windows Forms and COM platforms ship with [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) and [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) classes.</span></span>  <span data-ttu-id="efc9d-109">[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) e [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) são controles que você pode adicionar a um aplicativo para coletar tinta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-109">[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) and [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) are controls that you can add to an application to collect ink.</span></span>  <span data-ttu-id="efc9d-110">O [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) e [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) pode ser anexado a uma janela existente para ativar tinta nas janelas e controles personalizados.</span><span class="sxs-lookup"><span data-stu-id="efc9d-110">The [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) and [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) can be attached to an existing window to ink-enable windows and custom controls.</span></span>  
  
 <span data-ttu-id="efc9d-111">A plataforma WPF inclui o <xref:System.Windows.Controls.InkCanvas> controle.</span><span class="sxs-lookup"><span data-stu-id="efc9d-111">The WPF platform includes the <xref:System.Windows.Controls.InkCanvas> control.</span></span>  <span data-ttu-id="efc9d-112">Você pode adicionar uma <xref:System.Windows.Controls.InkCanvas> ao seu aplicativo e começar a coleta de tinta imediatamente.</span><span class="sxs-lookup"><span data-stu-id="efc9d-112">You can add an <xref:System.Windows.Controls.InkCanvas> to your application and begin collecting ink immediately.</span></span> <span data-ttu-id="efc9d-113">Com o <xref:System.Windows.Controls.InkCanvas>, o usuário pode copiar, selecionar e redimensionar a tinta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-113">With the <xref:System.Windows.Controls.InkCanvas>, the user can copy, select, and resize ink.</span></span>  <span data-ttu-id="efc9d-114">Você pode adicionar outros controles para o <xref:System.Windows.Controls.InkCanvas>, e o usuário também pode escrever sobre esses controles.</span><span class="sxs-lookup"><span data-stu-id="efc9d-114">You can add other controls to the <xref:System.Windows.Controls.InkCanvas>, and the user can handwrite over those controls, too.</span></span>  <span data-ttu-id="efc9d-115">Você pode criar um controle personalizado tinta adicionando um <xref:System.Windows.Controls.InkPresenter> e coletando seus pontos de caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-115">You can create an ink-enabled custom control by adding an <xref:System.Windows.Controls.InkPresenter> to it and collecting its stylus points.</span></span>  
  
 <span data-ttu-id="efc9d-116">A tabela a seguir lista em que você pode saber mais sobre como habilitar a tinta em um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="efc9d-116">The following table lists where to learn more about enabling ink in an application:</span></span>  
  
|<span data-ttu-id="efc9d-117">Para fazer isso...</span><span class="sxs-lookup"><span data-stu-id="efc9d-117">To do this…</span></span>|<span data-ttu-id="efc9d-118">Na plataforma WPF...</span><span class="sxs-lookup"><span data-stu-id="efc9d-118">On the WPF Platform…</span></span>|<span data-ttu-id="efc9d-119">Nas plataformas Windows Forms/COM...</span><span class="sxs-lookup"><span data-stu-id="efc9d-119">On the Windows Forms/COM Platforms…</span></span>|  
|-----------------|--------------------------|------------------------------------------|  
|<span data-ttu-id="efc9d-120">Adicionar um controle habilitado para tinta a um aplicativo</span><span class="sxs-lookup"><span data-stu-id="efc9d-120">Add an ink-enabled control to an application</span></span>|<span data-ttu-id="efc9d-121">Consulte [Introdução à tinta](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).</span><span class="sxs-lookup"><span data-stu-id="efc9d-121">See [Getting Started with Ink](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).</span></span>|<span data-ttu-id="efc9d-122">Consulte [Exemplo de formulário de declarações automáticas](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)</span><span class="sxs-lookup"><span data-stu-id="efc9d-122">See [Auto Claims Form Sample](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)</span></span>|  
|<span data-ttu-id="efc9d-123">Habilitar tinta em um controle personalizado</span><span class="sxs-lookup"><span data-stu-id="efc9d-123">Enable ink on a custom control</span></span>|<span data-ttu-id="efc9d-124">Consulte [Criando um controle de entrada de tinta](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="efc9d-124">See [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>|<span data-ttu-id="efc9d-125">Consulte [Exemplo da área de transferência de tinta](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).</span><span class="sxs-lookup"><span data-stu-id="efc9d-125">See [Ink Clipboard Sample](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).</span></span>|  
  
## <a name="ink-data"></a><span data-ttu-id="efc9d-126">Dados de tinta</span><span class="sxs-lookup"><span data-stu-id="efc9d-126">Ink Data</span></span>  
 <span data-ttu-id="efc9d-127">No Windows Forms e plataformas COM, [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), e [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) expõem um [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objeto.</span><span class="sxs-lookup"><span data-stu-id="efc9d-127">On the Windows Forms and COM platforms, [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), and [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) each expose a [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) object.</span></span> <span data-ttu-id="efc9d-128">O [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objeto contém os dados para um ou mais [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objetos e expõe métodos e propriedades comuns para gerenciar e manipular esses traços.</span><span class="sxs-lookup"><span data-stu-id="efc9d-128">The [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) object contains the data for one or more [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objects and exposes common methods and properties to manage and manipulate those strokes.</span></span>  <span data-ttu-id="efc9d-129">O [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objeto gerencia o tempo de vida de traços que ele contém; o [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objeto cria e exclui os traços que ele possui.</span><span class="sxs-lookup"><span data-stu-id="efc9d-129">The [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) object manages the lifetime of the strokes it contains; the [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) object creates and deletes the strokes that it owns.</span></span>  <span data-ttu-id="efc9d-130">Cada [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) tem um identificador que é exclusivo dentro de seu pai [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="efc9d-130">Each [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) has an identifier that is unique within its parent [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) object.</span></span>  
  
 <span data-ttu-id="efc9d-131">Na plataforma WPF, a <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> classe possui e gerencia seu próprio tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="efc9d-131">On the WPF platform, the <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> class owns and manages its own lifetime.</span></span> <span data-ttu-id="efc9d-132">Um grupo de <xref:System.Windows.Ink.Stroke> objetos podem ser coletados juntos em um <xref:System.Windows.Ink.StrokeCollection>, que fornece métodos para tinta comuns operações de gerenciamento de dados, como visitas de teste, apagar, transformar e serialização de tinta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-132">A group of <xref:System.Windows.Ink.Stroke> objects can be collected together in a <xref:System.Windows.Ink.StrokeCollection>, which provides methods for common ink data management operations such as hit testing, erasing, transforming, and serializing the ink.</span></span> <span data-ttu-id="efc9d-133">Um <xref:System.Windows.Ink.Stroke> pode pertencer a zero, um ou mais <xref:System.Windows.Ink.StrokeCollection> dar a objetos em qualquer tempo.</span><span class="sxs-lookup"><span data-stu-id="efc9d-133">A <xref:System.Windows.Ink.Stroke> can belong to zero, one, or more <xref:System.Windows.Ink.StrokeCollection> objects at any give time.</span></span>  <span data-ttu-id="efc9d-134">Em vez de ter um [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objeto, o <xref:System.Windows.Controls.InkCanvas> e <xref:System.Windows.Controls.InkPresenter> contêm um <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="efc9d-134">Instead of having a [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) object, the <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter> contain a <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="efc9d-135">O par de ilustrações a seguir compara os modelos de objeto de dados de tinta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-135">The following pair of illustrations compares the ink data object models.</span></span>  <span data-ttu-id="efc9d-136">No Windows Forms e plataformas COM, o [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objeto limita o tempo de vida do [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objetos e os pacotes da caneta pertencem aos traços individuais.</span><span class="sxs-lookup"><span data-stu-id="efc9d-136">On the Windows Forms and COM platforms, the [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) object constrains the lifetime of the [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objects, and the stylus packets belong to the individual strokes.</span></span>  <span data-ttu-id="efc9d-137">Dois ou mais traços podem fazer referência ao mesmo [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) do objeto, como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="efc9d-137">Two or more strokes can reference the same [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) object, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="efc9d-138">![Diagrama do modelo de objeto de tinta para COM&#47;Winforms.](../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")</span><span class="sxs-lookup"><span data-stu-id="efc9d-138">![Diagram of the Ink Object Model for COM&#47;Winforms.](../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")</span></span>  
  
 <span data-ttu-id="efc9d-139">Sobre o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], cada <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> é um objeto common language runtime que existe enquanto algo fizer uma referência a ele.</span><span class="sxs-lookup"><span data-stu-id="efc9d-139">On the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], each <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> is a common language runtime object that exists as long as something has a reference to it.</span></span>  <span data-ttu-id="efc9d-140">Cada <xref:System.Windows.Ink.Stroke> referências um <xref:System.Windows.Input.StylusPointCollection> e <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> objeto, que também são objetos common language runtime.</span><span class="sxs-lookup"><span data-stu-id="efc9d-140">Each <xref:System.Windows.Ink.Stroke> references a <xref:System.Windows.Input.StylusPointCollection> and <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> object, which are also common language runtime objects.</span></span>  
  
 <span data-ttu-id="efc9d-141">![Diagrama do modelo de objeto de tinta para WPF.](../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")</span><span class="sxs-lookup"><span data-stu-id="efc9d-141">![Diagram of the Ink Object Model for WPF.](../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")</span></span>  
  
 <span data-ttu-id="efc9d-142">A tabela a seguir compara como realizar algumas tarefas comuns na plataforma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e nas plataformas Windows Forms e COM.</span><span class="sxs-lookup"><span data-stu-id="efc9d-142">The following table compares how to accomplish some common tasks on the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform and the Windows Forms and COM platforms.</span></span>  
  
|<span data-ttu-id="efc9d-143">Tarefa</span><span class="sxs-lookup"><span data-stu-id="efc9d-143">Task</span></span>|<span data-ttu-id="efc9d-144">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="efc9d-144">Windows Presentation Foundation</span></span>|<span data-ttu-id="efc9d-145">Windows Forms e COM</span><span class="sxs-lookup"><span data-stu-id="efc9d-145">Windows Forms and COM</span></span>|  
|----------|-------------------------------------|---------------------------|  
|<span data-ttu-id="efc9d-146">Salvar tinta</span><span class="sxs-lookup"><span data-stu-id="efc9d-146">Save Ink</span></span>|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|<span data-ttu-id="efc9d-147">[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="efc9d-147">[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))</span></span>|  
|<span data-ttu-id="efc9d-148">Carregar tinta</span><span class="sxs-lookup"><span data-stu-id="efc9d-148">Load Ink</span></span>|<span data-ttu-id="efc9d-149">Criar um <xref:System.Windows.Ink.StrokeCollection> com o <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="efc9d-149">Create a <xref:System.Windows.Ink.StrokeCollection> with the <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> constructor.</span></span>|<span data-ttu-id="efc9d-150">[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9d-150">[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)</span></span>|  
|<span data-ttu-id="efc9d-151">Teste de clique</span><span class="sxs-lookup"><span data-stu-id="efc9d-151">Hit test</span></span>|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[<span data-ttu-id="efc9d-152">Microsoft.Ink.Ink.HitTest</span><span class="sxs-lookup"><span data-stu-id="efc9d-152">Microsoft.Ink.Ink.HitTest</span></span>](https://msdn.microsoft.com/library/aa515934.aspx)|  
|<span data-ttu-id="efc9d-153">Copiar tinta</span><span class="sxs-lookup"><span data-stu-id="efc9d-153">Copy Ink</span></span>|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|<span data-ttu-id="efc9d-154">[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9d-154">[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)</span></span>|  
|<span data-ttu-id="efc9d-155">Colar tinta</span><span class="sxs-lookup"><span data-stu-id="efc9d-155">Paste Ink</span></span>|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|<span data-ttu-id="efc9d-156">[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9d-156">[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)</span></span>|  
|<span data-ttu-id="efc9d-157">Acessar propriedades personalizadas em uma coleção de traços</span><span class="sxs-lookup"><span data-stu-id="efc9d-157">Access custom properties on a collection of strokes</span></span>|<span data-ttu-id="efc9d-158"><xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>(as propriedades são armazenadas internamente e acessadas via <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, e <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)</span><span class="sxs-lookup"><span data-stu-id="efc9d-158"><xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (the properties are stored internally and accessed via <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, and <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)</span></span>|<span data-ttu-id="efc9d-159">Use [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9d-159">Use [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)</span></span>|  
  
### <a name="sharing-ink-between-platforms"></a><span data-ttu-id="efc9d-160">Compartilhando tinta entre plataformas</span><span class="sxs-lookup"><span data-stu-id="efc9d-160">Sharing ink between platforms</span></span>  
 <span data-ttu-id="efc9d-161">Embora as plataformas tenham modelos de objeto diferentes para os dados de tinta, o compartilhamento de dados entre as plataformas é muito fácil.</span><span class="sxs-lookup"><span data-stu-id="efc9d-161">Although the platforms have different object models for the ink data, sharing the data between the platforms is very easy.</span></span> <span data-ttu-id="efc9d-162">Os exemplos a seguir salva a tinta de um aplicativo Windows Forms e carregam a tinta em um aplicativo do Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="efc9d-162">The following examples save ink from a Windows Forms application and load the ink into a Windows Presentation Foundation application.</span></span>  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 <span data-ttu-id="efc9d-163">Os exemplos a seguir salvam a tinta de um aplicativo Windows Presentation Foundation e carregam a tinta em um aplicativo dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="efc9d-163">The following examples save ink from a Windows Presentation Foundation application and load the ink into a Windows Forms application.</span></span>  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a><span data-ttu-id="efc9d-164">Eventos da caneta eletrônica</span><span class="sxs-lookup"><span data-stu-id="efc9d-164">Events from the Tablet Pen</span></span>  
 <span data-ttu-id="efc9d-165">O [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), e [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) no Windows Forms e COM plataformas recebem eventos quando o usuário Fornece dados da caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-165">The [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), and [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) on the Windows Forms and COM platforms receive events when the user inputs pen data.</span></span>  <span data-ttu-id="efc9d-166">O [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) ou [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) está anexado a uma janela ou um controle e pode assinar os eventos gerados pelos dados de entrada do tablet.</span><span class="sxs-lookup"><span data-stu-id="efc9d-166">The [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) or [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) is attached to a window or a control, and can subscribe to the events raised by the tablet input data.</span></span>  <span data-ttu-id="efc9d-167">O thread em que esses eventos ocorrem depende de se os eventos são gerados com uma caneta, um mouse ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="efc9d-167">The thread on which these events occurs depends on whether the events are raised with a pen, a mouse, or programmatically.</span></span>  <span data-ttu-id="efc9d-168">Para obter mais informações sobre o uso de threads em relação a esses eventos, consulte [Considerações gerais de thread](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) e [Threads nos quais um evento pode ser acionado](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).</span><span class="sxs-lookup"><span data-stu-id="efc9d-168">For more information about threading in relation to these events, see [General Threading Considerations](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) and [Threads on Which an Event Can Fire](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).</span></span>  
  
 <span data-ttu-id="efc9d-169">Na plataforma Windows Presentation Foundation, o <xref:System.Windows.UIElement> classe tem eventos para entrada de caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-169">On the Windows Presentation Foundation platform, the <xref:System.Windows.UIElement> class has events for pen input.</span></span> <span data-ttu-id="efc9d-170">Isso significa que cada controle expõe o conjunto completo de eventos de caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-170">This means that every control exposes the full set of stylus events.</span></span>  <span data-ttu-id="efc9d-171">Os eventos de caneta têm pares de eventos de túnel/propagação e sempre ocorrem no thread do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efc9d-171">The stylus events have tunneling/bubbling event pairs and always occur on the application thread.</span></span>  <span data-ttu-id="efc9d-172">Para obter mais informações, consulte [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="efc9d-172">For more information, see [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
 <span data-ttu-id="efc9d-173">O diagrama a seguir compara os modelos de objeto para as classes que geram eventos de caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-173">The following diagram shows compares the object models for the classes that raise stylus events.</span></span> <span data-ttu-id="efc9d-174">O modelo de objeto do Windows Presentation Foundation mostra somente os eventos de propagação, não os equivalentes do evento de túnel.</span><span class="sxs-lookup"><span data-stu-id="efc9d-174">The Windows Presentation Foundation object model shows only the bubbling events, not the tunneling event counterparts.</span></span>  
  
 <span data-ttu-id="efc9d-175">![Diagrama dos eventos da caneta no WPF versus Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")</span><span class="sxs-lookup"><span data-stu-id="efc9d-175">![Diagram of the Stylus events in WPF vs Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")</span></span>  
  
## <a name="pen-data"></a><span data-ttu-id="efc9d-176">Dados da caneta</span><span class="sxs-lookup"><span data-stu-id="efc9d-176">Pen Data</span></span>  
 <span data-ttu-id="efc9d-177">Todas as três plataformas fornecem meios para interceptar e manipular os dados provenientes de uma caneta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="efc9d-177">All three platforms provide you with ways to intercept and manipulate the data that comes in from a tablet pen.</span></span>  <span data-ttu-id="efc9d-178">Nas plataformas COM e Windows Forms, isso é feito criando um [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx), anexar uma janela ou controle a ela e criando uma classe que implementa o [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) ou [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) interface.</span><span class="sxs-lookup"><span data-stu-id="efc9d-178">On the Windows Forms and COM Platforms, this is achieved by creating a [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx), attaching a window or control to it, and creating a class that implements the [Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) or [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) interface.</span></span> <span data-ttu-id="efc9d-179">O plug-in personalizado é adicionado à coleção de plug-in de [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).</span><span class="sxs-lookup"><span data-stu-id="efc9d-179">The custom plug-in is then added to the plug-in collection of the [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).</span></span> <span data-ttu-id="efc9d-180">Para obter mais informações sobre esse modelo de objeto, consulte [Arquitetura de APIs StylusInput](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).</span><span class="sxs-lookup"><span data-stu-id="efc9d-180">For more information about this object model, see [Architecture of the StylusInput APIs](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).</span></span>  
  
 <span data-ttu-id="efc9d-181">No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plataforma, o <xref:System.Windows.UIElement> classe expõe um conjunto de plug-ins, semelhante no projeto para o [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).</span><span class="sxs-lookup"><span data-stu-id="efc9d-181">On the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform, the <xref:System.Windows.UIElement> class exposes a collection of plug-ins, similar in design to the [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).</span></span>  <span data-ttu-id="efc9d-182">Para interceptar dados da caneta, crie uma classe que herda de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e adicionar o objeto para o <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção do <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="efc9d-182">To intercept pen data, create a class that inherits from <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and add the object to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection of the <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="efc9d-183">Para obter mais informações sobre essa interação, consulte [Interceptando a entrada da caneta](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).</span><span class="sxs-lookup"><span data-stu-id="efc9d-183">For more information about this interaction, see [Intercepting Input from the Stylus](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).</span></span>  
  
 <span data-ttu-id="efc9d-184">Em todas as plataformas, um pool de threads recebe os dados de tinta por eventos de caneta e o envia para o thread do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efc9d-184">On all platforms, a thread pool receives the ink data via stylus events and sends it to the application thread.</span></span>  <span data-ttu-id="efc9d-185">Para obter mais informações sobre uso de threads nas plataformas Windows e COM, consulte [Considerações de thread para APIs StylusInput](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).</span><span class="sxs-lookup"><span data-stu-id="efc9d-185">For more information about threading on the COM and Windows Platforms, see [Threading Considerations for the StylusInput APIs](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).</span></span>  <span data-ttu-id="efc9d-186">Para obter mais informações sobre uso de threads no software Windows Presentation, consulte [O modelo de threading de tinta](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span><span class="sxs-lookup"><span data-stu-id="efc9d-186">For more information about threading on the Windows Presentation Software, see [The Ink Threading Model](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span></span>  
  
 <span data-ttu-id="efc9d-187">A ilustração a seguir compara os modelos de objeto para as classes que recebem dados da caneta no pool de threads de caneta.</span><span class="sxs-lookup"><span data-stu-id="efc9d-187">The following illustration compares the object models for the classes that receive pen data on the pen thread pool.</span></span>  
  
 <span data-ttu-id="efc9d-188">![Diagrama do WPF do modelo StylusPlugin vs Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")</span><span class="sxs-lookup"><span data-stu-id="efc9d-188">![Diagram of the StylusPlugin model WPF vs Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")</span></span>