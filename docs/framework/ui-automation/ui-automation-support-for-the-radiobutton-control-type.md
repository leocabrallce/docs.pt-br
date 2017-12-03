---
title: "Suporte de automação de interface de usuário para o tipo de controle RadioButton"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Radio Button
- UI Automation, Radio Button control type
- RadioButton control type
ms.assetid: 87170464-7857-41f1-bcf7-bb41be31cb53
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: e3b2723aaf61d25afb6164da8c3c6ca7a61e9e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-radiobutton-control-type"></a><span data-ttu-id="30208-102">Suporte de automação de interface de usuário para o tipo de controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="30208-102">UI Automation Support for the RadioButton Control Type</span></span>
> [!NOTE]
>  <span data-ttu-id="30208-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="30208-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="30208-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="30208-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="30208-105">Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle RadioButton.</span><span class="sxs-lookup"><span data-stu-id="30208-105">This topic provides information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support for the RadioButton control type.</span></span> <span data-ttu-id="30208-106">Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade.</span><span class="sxs-lookup"><span data-stu-id="30208-106">In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], a control type is a set of conditions that a control must meet in order to use the <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> property.</span></span> <span data-ttu-id="30208-107">As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="30208-107">The conditions include specific guidelines for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values and control patterns.</span></span>  
  
 <span data-ttu-id="30208-108">Um botão de opção consiste em um botão redondo e texto definido pelo aplicativo (um rótulo), um ícone, ou um bitmap que indica uma opção que o usuário pode fazer ao selecionar o botão.</span><span class="sxs-lookup"><span data-stu-id="30208-108">A radio button consists of a round button and application-defined text (a label), an icon, or a bitmap that indicates a choice the user can make by selecting the button.</span></span> <span data-ttu-id="30208-109">Um aplicativo normalmente usa botões de opção em uma caixa de grupo para permitir que o usuário pode escolher entre um conjunto de relacionado, mas as opções mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="30208-109">An application typically uses radio buttons in a group box to permit the user to choose from a set of related, but mutually exclusive options.</span></span> <span data-ttu-id="30208-110">Por exemplo, o aplicativo pode apresentar um grupo de botões de opção na qual o usuário pode selecionar um formato preferencial para o texto selecionado na área cliente.</span><span class="sxs-lookup"><span data-stu-id="30208-110">For example, the application might present a group of radio buttons from which the user can select a format preference for text selected in the client area.</span></span> <span data-ttu-id="30208-111">O usuário pode selecionar um formato alinhado à esquerda, direita ou centralizado, selecionando o botão de opção correspondente.</span><span class="sxs-lookup"><span data-stu-id="30208-111">The user could select a left-aligned, right-aligned, or centered format by selecting the corresponding radio button.</span></span> <span data-ttu-id="30208-112">Normalmente, o usuário pode selecionar apenas uma opção em vez de um conjunto de botões de opção.</span><span class="sxs-lookup"><span data-stu-id="30208-112">Typically, the user can select only one option at a time from a set of radio buttons.</span></span>  
  
 <span data-ttu-id="30208-113">As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle RadioButton, propriedades, padrões de controle e estrutura de árvore.</span><span class="sxs-lookup"><span data-stu-id="30208-113">The following sections define the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, properties, control patterns, and events for the RadioButton control type.</span></span> <span data-ttu-id="30208-114">O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de lista, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30208-114">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requirements apply to all list controls, whether [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], or [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a><span data-ttu-id="30208-115">Estrutura de árvore de automação da interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="30208-115">Required UI Automation Tree Structure</span></span>  
 <span data-ttu-id="30208-116">A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles de árvore que se refere ao botão de opção e descreve o que pode ser contido em cada modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="30208-116">The following table depicts the control view and the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree that pertains to radio button controls and describes what can be contained in each view.</span></span> <span data-ttu-id="30208-117">Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30208-117">For more information on the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span></span>  
  
|<span data-ttu-id="30208-118">Exibição de controle</span><span class="sxs-lookup"><span data-stu-id="30208-118">Control View</span></span>|<span data-ttu-id="30208-119">Exibição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="30208-119">Content View</span></span>|  
|------------------|------------------|  
|<span data-ttu-id="30208-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="30208-120">RadioButton</span></span>|<span data-ttu-id="30208-121">RadioButton</span><span class="sxs-lookup"><span data-stu-id="30208-121">RadioButton</span></span>|  
  
 <span data-ttu-id="30208-122">Não há filhos na exibição do controle ou o modo de exibição de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="30208-122">There are no children in the control view or the content view.</span></span>  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a><span data-ttu-id="30208-123">Propriedades de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="30208-123">Required UI Automation Properties</span></span>  
 <span data-ttu-id="30208-124">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para o botão de opção tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="30208-124">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties whose value or definition is especially relevant to the RadioButton control type.</span></span> <span data-ttu-id="30208-125">Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="30208-125">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="30208-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="30208-126"> Property</span></span>|<span data-ttu-id="30208-127">Valor</span><span class="sxs-lookup"><span data-stu-id="30208-127">Value</span></span>|<span data-ttu-id="30208-128">Observações</span><span class="sxs-lookup"><span data-stu-id="30208-128">Notes</span></span>|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|<span data-ttu-id="30208-129">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-129">See notes.</span></span>|<span data-ttu-id="30208-130">O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30208-130">The value of this property needs to be unique across all controls in an application.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|<span data-ttu-id="30208-131">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-131">See notes.</span></span>|<span data-ttu-id="30208-132">O retângulo mais externo que contém todo o controle.</span><span class="sxs-lookup"><span data-stu-id="30208-132">The outermost rectangle that contains the whole control.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|<span data-ttu-id="30208-133">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-133">See notes.</span></span>|<span data-ttu-id="30208-134">Se o controle pode receber o foco do teclado, deve suportar essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="30208-134">If the control can receive keyboard focus, it must support this property.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|<span data-ttu-id="30208-135">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-135">See notes.</span></span>|<span data-ttu-id="30208-136">Nome do controle de botão de opção é o texto que é exibido ao lado do botão que mantém o estado de seleção.</span><span class="sxs-lookup"><span data-stu-id="30208-136">The radio button control’s name is the text that is displayed beside the button that maintains selection state.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|<span data-ttu-id="30208-137">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-137">See notes.</span></span>|<span data-ttu-id="30208-138">Botão de opção clicáveis ponto deve do controle ser um ponto que define a seleção do botão de opção se clicado com um ponteiro de mouse.</span><span class="sxs-lookup"><span data-stu-id="30208-138">The radio button control’s clickable point MUST be a point that sets selection on the radio button if clicked with a mouse pointer.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|<span data-ttu-id="30208-139">Botões de opção são automática rotular os controles.</span><span class="sxs-lookup"><span data-stu-id="30208-139">Radio buttons are self-labeling controls.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|<span data-ttu-id="30208-140">RadioButton</span><span class="sxs-lookup"><span data-stu-id="30208-140">RadioButton</span></span>|<span data-ttu-id="30208-141">Esse valor é o mesmo para todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="30208-141">This value is the same for all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] frameworks.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|<span data-ttu-id="30208-142">"botão de opção"</span><span class="sxs-lookup"><span data-stu-id="30208-142">"radio button"</span></span>|<span data-ttu-id="30208-143">Cadeia de caracteres localizada correspondente ao tipo de controle RadioButton.</span><span class="sxs-lookup"><span data-stu-id="30208-143">Localized string corresponding to the RadioButton Control Type.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|<span data-ttu-id="30208-144">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="30208-144">True</span></span>|<span data-ttu-id="30208-145">O controle de botão de opção é sempre incluído na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.</span><span class="sxs-lookup"><span data-stu-id="30208-145">The radio button control is always included in the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|<span data-ttu-id="30208-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="30208-146">True</span></span>|<span data-ttu-id="30208-147">O controle de botão de opção é sempre incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.</span><span class="sxs-lookup"><span data-stu-id="30208-147">The radio button control is always included in the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a><span data-ttu-id="30208-148">Padrões de controle de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="30208-148">Required UI Automation Control Patterns</span></span>  
 <span data-ttu-id="30208-149">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por todos os controles de botão de opção de padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="30208-149">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns required to be supported by all radio button controls.</span></span> <span data-ttu-id="30208-150">Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30208-150">For more information on control patterns, see [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span></span>  
  
|<span data-ttu-id="30208-151">Propriedade de padrão de controle/padrão de controle</span><span class="sxs-lookup"><span data-stu-id="30208-151">Control Pattern/Control Pattern Property</span></span>|<span data-ttu-id="30208-152">Valor do suporte</span><span class="sxs-lookup"><span data-stu-id="30208-152">Support/Value</span></span>|<span data-ttu-id="30208-153">Observações</span><span class="sxs-lookup"><span data-stu-id="30208-153">Notes</span></span>|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|<span data-ttu-id="30208-154">Sim</span><span class="sxs-lookup"><span data-stu-id="30208-154">Yes</span></span>|<span data-ttu-id="30208-155">Todos os controles de botão de opção devem suportar o padrão de Item de seleção para habilitar a mesmos ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="30208-155">All radio button controls must support the Selection Item pattern to enable themselves to be selected.</span></span>|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|<span data-ttu-id="30208-156">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="30208-156">See notes.</span></span>|<span data-ttu-id="30208-157">O `SelectionContainerProperty` sempre devem ser concluídas para que um cliente de automação de interface do usuário pode determinar que outros botões de opção em um contexto específico estão relacionados uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="30208-157">The `SelectionContainerProperty` must always be completed so that a UI Automation client can determine what other radio buttons within a specific context relate to one another.</span></span>  <span data-ttu-id="30208-158">Para o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] versão do botão de opção, essa propriedade não terá suporte porque não é possível obter essas informações a partir desse framework herdado.</span><span class="sxs-lookup"><span data-stu-id="30208-158">For the [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] version of the radio button, this property will not be supported because it is not possible to obtain this information from that legacy framework.</span></span>|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|<span data-ttu-id="30208-159">Nunca</span><span class="sxs-lookup"><span data-stu-id="30208-159">Never</span></span>|<span data-ttu-id="30208-160">Botão de opção não pode percorrer seu estado quando ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="30208-160">The radio button cannot cycle through its state once it has been set.</span></span>  <span data-ttu-id="30208-161">Esse padrão nunca deve ser suportado em botão de opção.</span><span class="sxs-lookup"><span data-stu-id="30208-161">This pattern must never be supported on radio button.</span></span>|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a><span data-ttu-id="30208-162">Eventos de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="30208-162">Required UI Automation Events</span></span>  
 <span data-ttu-id="30208-163">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de botão de opção.</span><span class="sxs-lookup"><span data-stu-id="30208-163">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events required to be supported by all radio button controls.</span></span> <span data-ttu-id="30208-164">Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30208-164">For more information on events, see [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="30208-165">Evento</span><span class="sxs-lookup"><span data-stu-id="30208-165"> Event</span></span>|<span data-ttu-id="30208-166">Suporte</span><span class="sxs-lookup"><span data-stu-id="30208-166">Support</span></span>|<span data-ttu-id="30208-167">Observações</span><span class="sxs-lookup"><span data-stu-id="30208-167">Notes</span></span>|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|<span data-ttu-id="30208-168">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-168">Required</span></span>|<span data-ttu-id="30208-169">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-169">None</span></span>|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|<span data-ttu-id="30208-170">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-170">Required</span></span>|<span data-ttu-id="30208-171">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-171">None</span></span>|  
|<span data-ttu-id="30208-172"><xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="30208-172"><xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> property-changed event.</span></span>|<span data-ttu-id="30208-173">Nunca</span><span class="sxs-lookup"><span data-stu-id="30208-173">Never</span></span>|<span data-ttu-id="30208-174">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-174">None</span></span>|  
|<span data-ttu-id="30208-175"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="30208-175"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> property-changed event.</span></span>|<span data-ttu-id="30208-176">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-176">Required</span></span>|<span data-ttu-id="30208-177">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-177">None</span></span>|  
|<span data-ttu-id="30208-178"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="30208-178"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> property-changed event.</span></span>|<span data-ttu-id="30208-179">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-179">Required</span></span>|<span data-ttu-id="30208-180">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-180">None</span></span>|  
|<span data-ttu-id="30208-181"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="30208-181"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> property-changed event.</span></span>|<span data-ttu-id="30208-182">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-182">Required</span></span>|<span data-ttu-id="30208-183">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-183">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|<span data-ttu-id="30208-184">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-184">Required</span></span>|<span data-ttu-id="30208-185">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-185">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|<span data-ttu-id="30208-186">Necessária</span><span class="sxs-lookup"><span data-stu-id="30208-186">Required</span></span>|<span data-ttu-id="30208-187">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30208-187">None</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30208-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30208-188">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType.RadioButton>  
 [<span data-ttu-id="30208-189">Visão geral de tipos de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="30208-189">UI Automation Control Types Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [<span data-ttu-id="30208-190">Visão geral de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="30208-190">UI Automation Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-overview.md)