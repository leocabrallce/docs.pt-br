---
title: Como acessar a fonte HTML no Document Object Model HTML gerenciado
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
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0c4f894c3d9178f1dc32f7c99481a7daf565511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Como acessar a fonte HTML no Document Object Model HTML gerenciado
As propriedades <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> no controle <xref:System.Windows.Forms.WebBrowser> retornam o HTML do documento atual do modo que foi inicialmente exibido. No entanto, caso modificar a página usando chamadas de método e propriedade como <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> e <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, essas mudanças não aparecerão quando chamar <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Para obter a fonte HTML mais atualizada do DOM, é necessário chamar a <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> propriedade no elemento HTML.  
  
 O procedimento a seguir mostra como recuperar a fonte dinâmica e exibi-la em um menu de atalho separado.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Recuperação de fonte dinâmica com a propriedade OuterHtml  
  
1.  Criar um novo aplicativo Windows Form. Iniciar com um único <xref:System.Windows.Forms.Form>e chamá-la `Form1`.  
  
2.  Host de <xref:System.Windows.Forms.WebBrowser> controlar em seu aplicativo de formulários do Windows e o nome de `WebBrowser1`. Para obter mais informações, consulte [Como adicionar recursos do navegador da Web a um Aplicativo dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Crie um segundo <xref:System.Windows.Forms.Form> em seu aplicativo chamado `CodeForm`.  
  
4.  Adicionar um <xref:System.Windows.Forms.RichTextBox> controle `CodeForm` e defina seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade `Fill`.  
  
5.  Crie uma propriedade pública em `CodeForm` chamada `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Adicionar um <xref:System.Windows.Forms.Button> controle chamado `Button1` para sua <xref:System.Windows.Forms.Form>e monitora o <xref:System.Windows.Forms.Control.Click> evento. Para obter detalhes sobre como monitorar eventos, consulte [Eventos](../../../../docs/standard/events/index.md).  
  
7.  Adicione o seguinte código ao manipulador de eventos do <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Sempre teste o valor de <xref:System.Windows.Forms.WebBrowser.Document%2A> antes de tentar recuperá-lo. Se a página atual não tiver terminado de carregar, o <xref:System.Windows.Forms.WebBrowser.Document%2A> ou um ou mais de seus objetos filhos podem não ser inicializados.  
  
## <a name="see-also"></a>Consulte também  
 [Usando o Modelo de Objeto do Documento HTML gerenciado](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [Visão geral do controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
