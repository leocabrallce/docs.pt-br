---
title: Como gravar texto em arquivos com um StreamWriter no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Como gravar texto em arquivos com um StreamWriter no Visual Basic
Este exemplo abre um objeto <xref:System.IO.StreamWriter> com o método `My.Computer.FileSystem.OpenTextFileWriter` e o usa para gravar uma cadeia de caracteres em um arquivo de texto com o método <xref:System.IO.TextWriter.WriteLine%2A> da classe <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo existe e é somente leitura (<xref:System.IO.IOException>).  
  
-   O disco está cheio (<xref:System.IO.IOException>).  
  
-   O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existe. Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta. Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Como ler em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
