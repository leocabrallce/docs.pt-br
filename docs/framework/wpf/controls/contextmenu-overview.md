---
title: "Visão geral de ContextMenu"
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
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0776e7960aa76a76422d01180af5fd6a089bc98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-overview"></a>Visão geral de ContextMenu
O <xref:System.Windows.Controls.ContextMenu> classe representa o elemento que expõe funcionalidade usando um contexto específico <xref:System.Windows.Controls.Menu>. Normalmente, um usuário expõe o <xref:System.Windows.Controls.ContextMenu> no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] clicando com o botão do mouse. Este tópico apresenta o <xref:System.Windows.Controls.ContextMenu> elemento e fornece exemplos de como usá-lo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e código.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Controle ContextMenu  
 Um <xref:System.Windows.Controls.ContextMenu> é anexado a um controle específico. O <xref:System.Windows.Controls.ContextMenu> elemento permite apresentar aos usuários uma lista de itens que especificam comandos ou opções que estão associadas um controle específico, por exemplo, um <xref:System.Windows.Controls.Button>. Os usuários clicam com o botão direito do mouse no controle para exibir o menu. Geralmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo executar um comando.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Criando ContextMenus  
 Os exemplos a seguir mostram como criar um <xref:System.Windows.Controls.ContextMenu> com submenus. O <xref:System.Windows.Controls.ContextMenu> controles são anexados aos controles de botão.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Aplicando estilos a um ContextMenu  
 Usando um controle <xref:System.Windows.Style>, você pode alterar consideravelmente a aparência e comportamento de um <xref:System.Windows.Controls.ContextMenu> sem escrever um controle personalizado. Além de definir propriedades visuais, você também pode aplicar estilos a partes de um controle. Por exemplo, você pode alterar o comportamento das partes do controle usando as propriedades, ou você pode adicionar partes, ou alterar o layout de um <xref:System.Windows.Controls.ContextMenu>. Os exemplos a seguir mostram várias maneiras de adicionar estilos para <xref:System.Windows.Controls.ContextMenu> controles.  
  
 O primeiro exemplo define um estilo chamado `SimpleSysResources`, que mostra como usar as configurações atuais do sistema no seu estilo. O exemplo atribui <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> como o <xref:System.Windows.Controls.Control.Background%2A> cor e <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> como o <xref:System.Windows.Controls.Control.Foreground%2A> cor do <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 O exemplo a seguir usa o <xref:System.Windows.Trigger> elemento para alterar a aparência de um <xref:System.Windows.Controls.Menu> em resposta a eventos que são gerados no <xref:System.Windows.Controls.ContextMenu>. Quando um usuário move o mouse sobre o menu, a aparência do <xref:System.Windows.Controls.ContextMenu> itens de alterações.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [Estilos e modelos ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [Exemplo da galeria de controles de WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
