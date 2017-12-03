---
title: "Como definir o tamanho de painéis da barra de status"
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
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc9eca130b238ac686e88ebbc6e8491bc7be93bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="787fd-102">Como definir o tamanho de painéis da barra de status</span><span class="sxs-lookup"><span data-stu-id="787fd-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
>  <span data-ttu-id="787fd-103">O controle <xref:System.Windows.Forms.ToolStripStatusLabel> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.StatusBar>, no entanto, o controle <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="787fd-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="787fd-104">Cada instância do <xref:System.Windows.Forms.StatusBarPanel> classe dentro de um [controle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) controle tem um número de propriedades dinâmicas que determinam a largura e redimensione o comportamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="787fd-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="787fd-105">Para definir o tamanho de um painel</span><span class="sxs-lookup"><span data-stu-id="787fd-105">To set the size of a panel</span></span>  
  
1.  <span data-ttu-id="787fd-106">Em um procedimento, defina o <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, e <xref:System.Windows.Forms.StatusBarPanel.Width%2A> propriedades (ou qualquer subconjunto nele) para a barra de status painéis usando seu índice passado a <xref:System.Windows.Forms.StatusBar.Panels%2A> propriedade o <xref:System.Windows.Forms.StatusBarPanel> coleção.</span><span class="sxs-lookup"><span data-stu-id="787fd-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="787fd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="787fd-107">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="787fd-108">Passo a passo: atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="787fd-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="787fd-109">Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="787fd-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="787fd-110">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="787fd-110">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)