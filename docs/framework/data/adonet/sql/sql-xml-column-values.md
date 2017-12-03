---
title: Valores de coluna de XML do SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c974749ee84bf64d1912ed71ea0817227b1ea514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="14696-102">Valores de coluna de XML do SQL</span><span class="sxs-lookup"><span data-stu-id="14696-102">SQL XML Column Values</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="14696-103">oferece suporte a `xml` tipo de dados, e os desenvolvedores podem recuperar conjuntos de resultados desse tipo usando o comportamento padrão da <xref:System.Data.SqlClient.SqlCommand> classe.</span><span class="sxs-lookup"><span data-stu-id="14696-103"> supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="14696-104">Um `xml` coluna pode ser recuperada como qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, você deve usar um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="14696-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14696-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14696-105">Example</span></span>  
 <span data-ttu-id="14696-106">O aplicativo de console a seguir seleciona duas linhas, cada uma contendo uma `xml` coluna, do **Sales** tabela o **AdventureWorks** de banco de dados para um <xref:System.Data.SqlClient.SqlDataReader> instância.</span><span class="sxs-lookup"><span data-stu-id="14696-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="14696-107">Para cada linha, o valor da `xml` coluna é leitura usando o <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> método <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="14696-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="14696-108">O valor é armazenado em um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="14696-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="14696-109">Observe que você deve usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez de <xref:System.Data.IDataRecord.GetValue%2A> método se você deseja definir o conteúdo um <xref:System.Data.SqlTypes.SqlXml> variável; <xref:System.Data.IDataRecord.GetValue%2A> retorna o valor da `xml` coluna como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="14696-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14696-110">O **AdventureWorks** banco de dados de exemplo não é instalado por padrão quando você instala o [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14696-110">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="14696-111">Você pode instalá-lo executando [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instalação.</span><span class="sxs-lookup"><span data-stu-id="14696-111">You can install it by running [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="14696-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14696-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="14696-113">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="14696-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="14696-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="14696-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>