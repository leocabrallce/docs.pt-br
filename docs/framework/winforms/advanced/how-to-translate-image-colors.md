---
title: Como converter cores de imagens
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
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a2147b9bc86aa7ec03e8455bb0dc51c89a8b282
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-image-colors"></a>Como converter cores de imagens
Uma conversão adiciona um valor a um ou mais dos componentes de quatro cores. As entradas de matriz de cores que representam as conversões são fornecidas na tabela a seguir.  
  
|Componente a ser convertido|Entrada da matriz|  
|--------------------------------|------------------|  
|Vermelho|[4][0]|  
|Verde|[4][1]|  
|Azul|[4][2]|  
|Alfa|[4][3]|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars.bmp. Em seguida, o código adiciona 0,75 ao componente vermelho de cada pixel na imagem. A imagem original é desenhada ao lado da imagem transformada.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem transformada à direita.  
  
 ![Converter cores](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 A tabela a seguir lista os vetores de cores para as quatro barras antes e depois da conversão em vermelho. Observe que, como o valor máximo para um componente de cor é 1, o componente vermelho na segunda linha não será alterado. (Da mesma forma, o valor mínimo para um componente de cor é 0).  
  
|Original|Convertido|  
|--------------|----------------|  
|Preto (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Vermelho (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Verde (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Azul (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `ColorBars.bmp` por um nome de arquivo de imagem e um caminho que sejam válidos no sistema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Recolorindo Imagens](../../../../docs/framework/winforms/advanced/recoloring-images.md)
