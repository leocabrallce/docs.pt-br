---
title: "Como concluir trabalhos de impressão do Windows Forms"
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
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00c43ff4ca418d272dc00132907c5bcbc0c5bc8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Como concluir trabalhos de impressão do Windows Forms
Frequentemente, processadores de texto e outros aplicativos que envolvem impressão fornecerão a opção para exibir uma mensagem aos usuários de que um trabalho de impressão foi concluído. Você pode fornecer essa funcionalidade em seus formulários do Windows manipulando o <xref:System.Drawing.Printing.PrintDocument.EndPrint> evento o <xref:System.Drawing.Printing.PrintDocument> componente.  
  
 O procedimento a seguir requer que você criou um aplicativo baseado em Windows com um <xref:System.Drawing.Printing.PrintDocument> componente nele, que é o modo padrão de ativar a impressão de um aplicativo baseado em Windows. Para obter mais informações sobre a impressão no Windows Forms usando o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: criar padrão Windows Forms trabalhos de impressão](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Para concluir um trabalho de impressão  
  
1.  Definir o <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> propriedade o <xref:System.Drawing.Printing.PrintDocument> componente.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  Escreva código para manipular o <xref:System.Drawing.Printing.PrintDocument.EndPrint> evento.  
  
     No exemplo de código a seguir, uma caixa de mensagem é exibida, indicando que o documento terminou a impressão.  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
