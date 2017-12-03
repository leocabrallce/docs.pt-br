---
title: "Noções básicas sobre o desenvolvimento de controle dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca2bac983e25ab7453230a6718fe7eaa98e82275
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-control-development-basics"></a><span data-ttu-id="ea097-102">Noções básicas sobre o desenvolvimento de controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea097-102">Windows Forms Control Development Basics</span></span>
<span data-ttu-id="ea097-103">Um controle de formulários do Windows é uma classe que deriva diretamente ou indiretamente de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ea097-103">A Windows Forms control is a class that derives directly or indirectly from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ea097-104">A lista a seguir descreve os cenários comuns para o desenvolvimento de controles do Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="ea097-104">The following list describes common scenarios for developing Windows Forms controls:</span></span>  
  
-   <span data-ttu-id="ea097-105">Combinando controles existentes para criar um controle composto.</span><span class="sxs-lookup"><span data-stu-id="ea097-105">Combining existing controls to author a composite control.</span></span>  
  
     <span data-ttu-id="ea097-106">Controles compostos encapsulam uma interface do usuário que pode ser reutilizada como um controle.</span><span class="sxs-lookup"><span data-stu-id="ea097-106">Composite controls encapsulate a user interface that can be reused as a control.</span></span> <span data-ttu-id="ea097-107">Um exemplo de um controle composto é um controle que consiste em uma caixa de texto e um botão de redefinição.</span><span class="sxs-lookup"><span data-stu-id="ea097-107">An example of a composite control is a control that consists of a text box and a reset button.</span></span> <span data-ttu-id="ea097-108">Designers visuais dão suporte avançado para a criação de controles compostos.</span><span class="sxs-lookup"><span data-stu-id="ea097-108">Visual designers offer rich support for creating composite controls.</span></span> <span data-ttu-id="ea097-109">Para criar um controle composto, derivam <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ea097-109">To author a composite control, derive from <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ea097-110">A classe base <xref:System.Windows.Forms.UserControl> fornece o roteamento de teclado para controles e permite que os controles filho funcionar como um grupo filho.</span><span class="sxs-lookup"><span data-stu-id="ea097-110">The base class <xref:System.Windows.Forms.UserControl> provides keyboard routing for child controls and enables child controls to work as a group.</span></span> <span data-ttu-id="ea097-111">Para obter mais informações, consulte [Desenvolvendo um controle composto do Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea097-111">For more information, see [Developing a Composite Windows Forms Control](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span></span>  
  
-   <span data-ttu-id="ea097-112">Estendendo um controle existente para personalizá-la ou aumentar sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ea097-112">Extending an existing control to customize it or to add to its functionality.</span></span>  
  
     <span data-ttu-id="ea097-113">Um botão cuja cor não pode ser alterado e um botão que tem uma propriedade adicional que controla quantas vezes ele foi clicado são exemplos de controles estendidos.</span><span class="sxs-lookup"><span data-stu-id="ea097-113">A button whose color cannot be changed and a button that has an additional property that tracks how many times it has been clicked are examples of extended controls.</span></span> <span data-ttu-id="ea097-114">Você pode personalizar qualquer controle do Windows Forms derivado dele e substituir ou adicionar propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="ea097-114">You can customize any Windows Forms control by deriving from it and overriding or adding properties, methods, and events.</span></span>  
  
-   <span data-ttu-id="ea097-115">Criando um controle que não combina ou estende os controles existentes.</span><span class="sxs-lookup"><span data-stu-id="ea097-115">Authoring a control that does not combine or extend existing controls.</span></span>  
  
     <span data-ttu-id="ea097-116">Nesse cenário, o controle é derivado da classe base <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="ea097-116">In this scenario, derive your control from the base class <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="ea097-117">Você pode adicionar e substituir propriedades, métodos e eventos da classe base.</span><span class="sxs-lookup"><span data-stu-id="ea097-117">You can add as well as override properties, methods, and events of the base class.</span></span> <span data-ttu-id="ea097-118">Para começar, consulte [Como desenvolver um controle simples do Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea097-118">To get started, see [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span></span>  
  
 <span data-ttu-id="ea097-119">A classe base para controles de formulários do Windows, <xref:System.Windows.Forms.Control>, fornece os detalhes necessários para a exibição visual em aplicativos do lado do cliente Windows.</span><span class="sxs-lookup"><span data-stu-id="ea097-119">The base class for Windows Forms controls, <xref:System.Windows.Forms.Control>, provides the plumbing required for visual display in client-side Windows-based applications.</span></span> <span data-ttu-id="ea097-120"><xref:System.Windows.Forms.Control>Fornece um identificador de janela, manipula o roteamento de mensagens e fornece eventos de mouse e teclado, assim como muitos outros usuário eventos de interface.</span><span class="sxs-lookup"><span data-stu-id="ea097-120"><xref:System.Windows.Forms.Control> provides a window handle, handles message routing, and provides mouse and keyboard events as well as many other user interface events.</span></span> <span data-ttu-id="ea097-121">Ele fornece o layout avançado e tem propriedades específicas para a exibição visual, como <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="ea097-121">It provides advanced layout and has properties specific to visual display, such as <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, and many others.</span></span> <span data-ttu-id="ea097-122">Além disso, ele fornece segurança, suporte a threading e interoperabilidade com controles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="ea097-122">Additionally, it provides security, threading support, and interoperability with ActiveX controls.</span></span> <span data-ttu-id="ea097-123">Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ea097-123">Because so much of the infrastructure is provided by the base class, it is relatively easy to develop your own Windows Forms controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea097-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea097-124">See Also</span></span>  
 [<span data-ttu-id="ea097-125">Como desenvolver um controle simples dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea097-125">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="ea097-126">Desenvolvendo um controle de composição dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea097-126">Developing a Composite Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [<span data-ttu-id="ea097-127">Como criar um controle dos Windows Forms que mostre o progresso</span><span class="sxs-lookup"><span data-stu-id="ea097-127">How to: Create a Windows Forms Control That Shows Progress</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [<span data-ttu-id="ea097-128">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="ea097-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)