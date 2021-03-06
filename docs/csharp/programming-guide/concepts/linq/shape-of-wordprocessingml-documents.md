---
title: Formato de documentos de WordprocessingML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee03c9cd64c3c3b251049be0826c7b29abe80bfa
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Formato de documentos de WordprocessingML (C#)
Este tópico apresenta a forma XML de um documento WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formatos do Microsoft Office  
 O formato de arquivo nativo para o sistema do Microsoft Office 2007 é Office Open XML (geralmente chamado de Open XML). O Open XML é um formato baseado em XML que tem um padrão Ecma e está no momento passando por um processo de padrões de ISO-IEC. A linguagem de marcação para arquivos de processamento de texto dentro do Open XML é chamada de WordprocessingML. Este tutorial usa arquivos de origem do WordprocessingML como entrada para os exemplos.  
  
 Se você estiver usando o Microsoft Office 2003, pode salvar documentos no formato Office Open XML se instalou os formatos de arquivo do Pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>O formato de documentos de WordprocessingML  
 A primeira coisa a entender é a forma dos documentos de WordprocessingML. Um documento de WordprocessingML contém um elemento do corpo (chamado `w:body`) que contém os parágrafos do documento. Cada parágrafo contém uma ou mais execuções de texto (chamado `w:r`). Cada execução de texto contém uma ou mais partes de texto (chamado `w:t`).  
  
 Veja a seguir um documento muito simples de WordprocessingML:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 Este documento contém dois parágrafos. Ambos contêm uma única execução de texto, e cada execução de texto contém uma única parte de texto.  
  
 A maneira mais fácil para ver o conteúdo de um documento de WordprocessingML no formato XML é criar um usando Microsoft Word, salvá-lo e executar o seguinte programa que lê XML no console.  
  
 Este exemplo usa as classes encontradas no assembly WindowsBase. Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a>Recursos externos  
 [Apresentando os formatos de arquivo do Office (2007) Open XML](https://msdn.microsoft.com/library/ms406049.aspx)  
 [Visão geral de WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)  
 [Anatomia de um arquivo de WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Introdução a WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: página de download de esquemas de referência XML](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
