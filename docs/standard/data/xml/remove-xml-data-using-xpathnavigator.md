---
title: Remova os dados XML usando XPathNavigator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29faf92b26908a37fb122dec00b2d4d6b5f3bf16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="e101b-102">Remova os dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e101b-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="e101b-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para remover os nós e valores de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="e101b-104">Para usar esses métodos, o objeto <xref:System.Xml.XPath.XPathNavigator> deve ser editável, ou seja, sua propriedade <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> deve ser `true`.</span><span class="sxs-lookup"><span data-stu-id="e101b-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="e101b-105">Os objetos <xref:System.Xml.XPath.XPathNavigator> que podem editar um documento XML são criados pelo método <xref:System.Xml.XmlDocument.CreateNavigator%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="e101b-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e101b-106">os objetos de<xref:System.Xml.XPath.XPathNavigator> criados pela classe de <xref:System.Xml.XPath.XPathDocument> são somente leitura e qualquer tentativa de usar os métodos de um objeto de <xref:System.Xml.XPath.XPathNavigator> criado por <xref:System.Xml.XPath.XPathDocument> objetos resultados em <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="e101b-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="e101b-107">Para obter mais informações sobre como criar editável <xref:System.Xml.XPath.XPathNavigator> objetos, consulte [leitura de dados XML usando XPathDocument e XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="e101b-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="e101b-108">Removendo os nós</span><span class="sxs-lookup"><span data-stu-id="e101b-108">Removing Nodes</span></span>  
 <span data-ttu-id="e101b-109">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece o método de <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> para remover os nós de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="e101b-110">Removendo um nó</span><span class="sxs-lookup"><span data-stu-id="e101b-110">Removing a Node</span></span>  
 <span data-ttu-id="e101b-111">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece o método de <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> para excluir o nó atual que um objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado atualmente de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="e101b-112">Depois que um nó foi excluído usando o método <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> , não é mais alcançável raiz do objeto de <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="e101b-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="e101b-113">Depois que um nó foi excluído, <xref:System.Xml.XPath.XPathNavigator> está localizado no nó pai do nó excluído.</span><span class="sxs-lookup"><span data-stu-id="e101b-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="e101b-114">Uma operação de exclusão não afeta a posição de nenhum objeto de <xref:System.Xml.XPath.XPathNavigator> posicionado sobre o nó excluído.</span><span class="sxs-lookup"><span data-stu-id="e101b-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="e101b-115">Esses objetos de <xref:System.Xml.XPath.XPathNavigator> são válidos no sentido que podem mover dentro da sub-árvore excluída, mas não podem ser movidos à árvore do nó usando os métodos definidos de navegação do nó normal da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="e101b-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e101b-116">O método de <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> pode ser usado para mover esses objetos de <xref:System.Xml.XPath.XPathNavigator> de novo na árvore do nó principal, ou de árvore nó principal da subárvore excluída.</span><span class="sxs-lookup"><span data-stu-id="e101b-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="e101b-117">No exemplo a seguir, o elemento de `price` do primeiro elemento de `book` do arquivo de `contosoBooks.xml` é excluído usando o método <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="e101b-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="e101b-118">A posição do objeto de <xref:System.Xml.XPath.XPathNavigator> após o elemento de `price` é excluída está no elemento pai de `book` .</span><span class="sxs-lookup"><span data-stu-id="e101b-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="e101b-119">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="e101b-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="e101b-120">Removendo um nó de atributo</span><span class="sxs-lookup"><span data-stu-id="e101b-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="e101b-121">Os nós de atributo são removidos de um documento XML usando o método <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="e101b-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="e101b-122">Depois que um nó de atributo foi excluído, não é mais alcançável do nó raiz de um objeto de <xref:System.Xml.XmlDocument> e o objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado no elemento pai.</span><span class="sxs-lookup"><span data-stu-id="e101b-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="e101b-123">Atributos padrão</span><span class="sxs-lookup"><span data-stu-id="e101b-123">Default Attributes</span></span>  
 <span data-ttu-id="e101b-124">Independentemente do método usado para remover os atributos, há limitações especiais em remover os atributos que são definidos como atributos padrão no DTD ou no esquema XML para o documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="e101b-125">Os atributos padrão não podem ser removidos a menos que o elemento que pertencem a também é removido.</span><span class="sxs-lookup"><span data-stu-id="e101b-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="e101b-126">Os atributos padrão são sempre atual para elementos que têm atributos padrões declarados, e como resultado, excluindo resultados de um atributo padrão em uma substituição atributo ser inserido no elemento e ser inicializado para o valor padrão que foi declarado.</span><span class="sxs-lookup"><span data-stu-id="e101b-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="e101b-127">Removendo os valores</span><span class="sxs-lookup"><span data-stu-id="e101b-127">Removing Values</span></span>  
 <span data-ttu-id="e101b-128">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece os métodos de <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> e de <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> para remover sem tipo e os valores tipados de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="e101b-129">Removendo os valores sem tipo</span><span class="sxs-lookup"><span data-stu-id="e101b-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="e101b-130">O método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> simplesmente insere o valor sem tipo de `string` passado como um parâmetro como o valor do nó no qual o objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="e101b-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="e101b-131">Passando uma cadeia de caracteres vazia para o método de <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> remove o valor do nó atual.</span><span class="sxs-lookup"><span data-stu-id="e101b-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="e101b-132">O exemplo a seguir remove o valor do elemento de `price` do primeiro elemento de `book` no arquivo de `contosoBooks.xml` usando o método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="e101b-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="e101b-133">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="e101b-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="e101b-134">Removendo os valores tipados</span><span class="sxs-lookup"><span data-stu-id="e101b-134">Removing Typed Values</span></span>  
 <span data-ttu-id="e101b-135">Quando o tipo de um nó é um tipo simples de Esquema XML do W3C, o novo valor inserido pelo método <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> é verificado em relação às facetas do tipo simples antes que o valor seja definido.</span><span class="sxs-lookup"><span data-stu-id="e101b-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="e101b-136">Se o novo valor não for válido de acordo com o tipo de nó (por exemplo, definir um valor de `-1` em um elemento cujo tipo seja `xs:positiveInteger`), isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e101b-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="e101b-137">O método de <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> também não pode ser `null` passado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e101b-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="e101b-138">Como resultado remova o valor de um nó tipado deve seguir com o tipo do nó.</span><span class="sxs-lookup"><span data-stu-id="e101b-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="e101b-139">O exemplo a seguir remove o valor do elemento de `price` do primeiro elemento de `book` no arquivo de `contosoBooks.xml` usando o método <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> definindo o valor a `0`.</span><span class="sxs-lookup"><span data-stu-id="e101b-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="e101b-140">O valor do nó não é removido, mas o custo de livro foi removido de acordo com seu tipo de dados de `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="e101b-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="e101b-141">Nós de namespace</span><span class="sxs-lookup"><span data-stu-id="e101b-141">Namespace Nodes</span></span>  
 <span data-ttu-id="e101b-142">Os nós de namespace não podem ser excluídos de um objeto de <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="e101b-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="e101b-143">Tentativas de excluir os nós de namespace usando o método de <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> resultam em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e101b-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="e101b-144">As propriedades de InnerXml e de OuterXml</span><span class="sxs-lookup"><span data-stu-id="e101b-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="e101b-145">As propriedades <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> da classe <xref:System.Xml.XPath.XPathNavigator> alteram a marcação XML dos nós nos quais um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="e101b-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="e101b-146">A propriedade <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento com o conteúdo analisado da `string` do XML determinada.</span><span class="sxs-lookup"><span data-stu-id="e101b-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="e101b-147">Da mesma maneira, a propriedade <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento além do próprio nó atual.</span><span class="sxs-lookup"><span data-stu-id="e101b-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="e101b-148">Além dos métodos descritos neste tópico, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e as propriedades de <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> podem ser usados para remover os nós e valores de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e101b-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="e101b-149">Para obter mais informações sobre como usar o <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> propriedades para modificar nós, consulte o [modificar dados XML usando XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="e101b-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="e101b-150">Salvando um documento XML</span><span class="sxs-lookup"><span data-stu-id="e101b-150">Saving an XML Document</span></span>  
 <span data-ttu-id="e101b-151">Salvando as alterações feitas a um objeto de <xref:System.Xml.XmlDocument> como resultado dos métodos descritos neste tópico é executado usando os métodos da classe <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="e101b-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e101b-152">Para obter mais informações sobre como salvar as alterações feitas em um <xref:System.Xml.XmlDocument> de objeto, consulte [salvando e escrevendo um documento](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="e101b-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e101b-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e101b-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="e101b-154">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="e101b-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="e101b-155">Inserir dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e101b-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e101b-156">Modificar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e101b-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)