---
title: "Como capturar a entrada do usuário de um PrintDialog em tempo de execução"
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
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fcc2ccc240752c8c54c28fe2358d3ef49cbf3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Como capturar a entrada do usuário de um PrintDialog em tempo de execução
Enquanto você pode definir opções de impressão em tempo de design, às vezes, convém alterar essas opções em tempo de execução, provavelmente devido a escolhas feitas pelo usuário. Você pode capturar a entrada do usuário para imprimir um documento usando o <xref:System.Windows.Forms.PrintDialog> e <xref:System.Drawing.Printing.PrintDocument> componentes.  
  
### <a name="to-change-print-options-programmatically"></a>Para alterar opções de impressão programaticamente  
  
1.  Adicionar um <xref:System.Windows.Forms.PrintDialog> e um <xref:System.Drawing.Printing.PrintDocument> componente para seu formulário.  
  
2.  Definir o <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade o <xref:System.Windows.Forms.PrintDialog> para o <xref:System.Drawing.Printing.PrintDocument> adicionado ao formulário.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Exibição de <xref:System.Windows.Forms.PrintDialog> componente usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Opções de impressão do usuário na caixa de diálogo serão copiadas para o <xref:System.Drawing.Printing.PrinterSettings> propriedade o <xref:System.Drawing.Printing.PrintDocument> componente.  
  
## <a name="see-also"></a>Consulte também  
 [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
