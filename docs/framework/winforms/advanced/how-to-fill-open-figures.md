---
title: Como preencher figuras abertas
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a8a2d5a13cac97063bf2a04969928c859a5954d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="c72ef-102">Como preencher figuras abertas</span><span class="sxs-lookup"><span data-stu-id="c72ef-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="c72ef-103">Você pode preencher um caminho, passando um <xref:System.Drawing.Drawing2D.GraphicsPath> o objeto para o <xref:System.Drawing.Graphics.FillPath%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c72ef-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="c72ef-104">O <xref:System.Drawing.Graphics.FillPath%2A> método preenche o caminho de acordo com o modo de preenchimento (alternativo ou contorno) definido atualmente para o caminho.</span><span class="sxs-lookup"><span data-stu-id="c72ef-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="c72ef-105">Se o caminho tiver figuras abertas, ele será preenchido como se essas figuras que foram fechadas.</span><span class="sxs-lookup"><span data-stu-id="c72ef-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c72ef-106"> fecha uma figura desenhando uma linha reta do ponto final para o seu ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="c72ef-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c72ef-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c72ef-107">Example</span></span>  
 <span data-ttu-id="c72ef-108">O exemplo a seguir cria um caminho que tem uma figura aberta (um arco) e uma figura fechada (uma elipse).</span><span class="sxs-lookup"><span data-stu-id="c72ef-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="c72ef-109">O <xref:System.Drawing.Graphics.FillPath%2A> método preenche o caminho de acordo com o modo de preenchimento padrão, que é <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="c72ef-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="c72ef-110">A ilustração a seguir mostra a saída do código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c72ef-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="c72ef-111">Observe que o caminho é preenchido (conforme <xref:System.Drawing.Drawing2D.FillMode.Alternate>) como se a figura aberta foi fechada por uma linha reta do ponto final para o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="c72ef-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="c72ef-112">![Preencher caminho aberto](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="c72ef-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c72ef-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c72ef-113">Compiling the Code</span></span>  
 <span data-ttu-id="c72ef-114">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c72ef-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72ef-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c72ef-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="c72ef-116">Caminhos de Elementos Gráficos no GDI+</span><span class="sxs-lookup"><span data-stu-id="c72ef-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)