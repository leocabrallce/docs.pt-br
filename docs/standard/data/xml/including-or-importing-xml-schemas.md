---
title: Incluindo ou importando um esquema XML
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
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d3b336b0ac4ca4fd02950a572404a117d4c193f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="ff290-102">Incluindo ou importando um esquema XML</span><span class="sxs-lookup"><span data-stu-id="ff290-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="ff290-103">Um esquema XML pode conter os elementos `<xs:import />`, `<xs:include />` e `<xs:redefine />`.</span><span class="sxs-lookup"><span data-stu-id="ff290-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="ff290-104">Esses elementos de esquema referem-se a outros esquemas XML que podem ser usados para complementar a estrutura do esquema que os inclui ou importa.</span><span class="sxs-lookup"><span data-stu-id="ff290-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="ff290-105">As classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> e <xref:System.Xml.Schema.XmlSchemaRedefine> são mapeadas para esses elementos na API do modelo de objeto (SOM) de esquema.</span><span class="sxs-lookup"><span data-stu-id="ff290-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="ff290-106">Incluindo ou importando um esquema XML</span><span class="sxs-lookup"><span data-stu-id="ff290-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="ff290-107">O exemplo de código a seguir complementa o esquema de cliente criado no [compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tópico com o esquema de endereço.</span><span class="sxs-lookup"><span data-stu-id="ff290-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="ff290-108">Complementar o esquema de cliente com o esquema de endereço torna disponíveis os tipos de endereço no esquema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff290-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="ff290-109">É possível incorporar o esquema de endereços empregando os elementos `<xs:include />` ou `<xs:import />` para usar os componentes do esquema de endereços como está, ou empregando um elemento `<xs:redefine />` para modificar qualquer um de seus componentes conforme as necessidades do esquema de cliente.</span><span class="sxs-lookup"><span data-stu-id="ff290-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="ff290-110">Desde que o esquema de endereço tenha um `targetNamespace` diferente daquele do esquema de cliente, o elemento `<xs:import />` e, consequentemente, a semântica de importação serão usados.</span><span class="sxs-lookup"><span data-stu-id="ff290-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="ff290-111">O exemplo de código inclui o esquema de endereço nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="ff290-111">The code example includes the address schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="ff290-112">Adiciona o esquema de cliente e o esquema de endereço a um novo objeto de <xref:System.Xml.Schema.XmlSchemaSet> e os compila.</span><span class="sxs-lookup"><span data-stu-id="ff290-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="ff290-113">Todos os avisos e erros de validação de esquema apresentados durante a leitura ou a compilação dos esquemas são tratados pelo delegado <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ff290-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="ff290-114">Recupera os objetos compilados de <xref:System.Xml.Schema.XmlSchema> para os esquemas de cliente e de endereço de <xref:System.Xml.Schema.XmlSchemaSet> ao fazer a iteração na propriedade <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff290-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="ff290-115">As propriedades de PSCI (Post-Schema-Compilation-Infoset) ficarão acessíveis desde que os esquemas sejam compilados.</span><span class="sxs-lookup"><span data-stu-id="ff290-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="ff290-116">Cria um objeto de <xref:System.Xml.Schema.XmlSchemaImport>, define a propriedade <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> da importação para o namespace do esquema de endereço, define a propriedade <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> da importação para o objeto de <xref:System.Xml.Schema.XmlSchema> do esquema de endereço e adiciona a importação à propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> do esquema de cliente.</span><span class="sxs-lookup"><span data-stu-id="ff290-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4.  <span data-ttu-id="ff290-117">Reutiliza e compila o objeto modificado de <xref:System.Xml.Schema.XmlSchema> do esquema de cliente usando os métodos <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> e <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> da classe <xref:System.Xml.Schema.XmlSchemaSet> e o grava no console.</span><span class="sxs-lookup"><span data-stu-id="ff290-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5.  <span data-ttu-id="ff290-118">Por fim, grava recursivamente no console todos os esquemas importados para o esquema de cliente usando a propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> do esquema de cliente.</span><span class="sxs-lookup"><span data-stu-id="ff290-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="ff290-119">A propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> fornece acesso a qualquer include (incluir), import (importar) ou redefine (redefinir) adicionados a um esquema.</span><span class="sxs-lookup"><span data-stu-id="ff290-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="ff290-120">Veja abaixo o exemplo de código completo e os esquemas de endereço e de cliente gravados no console.</span><span class="sxs-lookup"><span data-stu-id="ff290-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="ff290-121">Para obter mais informações sobre o `<xs:import />`, `<xs:include />`, e `<xs:redefine />` elementos e o <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> e <xref:System.Xml.Schema.XmlSchemaRedefine> classes, consulte o [W3C XML Schema](http://go.microsoft.com/fwlink/?LinkId=45242) e <xref:System.Xml.Schema?displayProperty=nameWithType> documentação de referência de classe de namespace.</span><span class="sxs-lookup"><span data-stu-id="ff290-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](http://go.microsoft.com/fwlink/?LinkId=45242) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff290-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff290-122">See Also</span></span>  
 [<span data-ttu-id="ff290-123">Visão geral de modelo de objeto de esquema XML</span><span class="sxs-lookup"><span data-stu-id="ff290-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="ff290-124">Lendo e gravando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="ff290-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="ff290-125">Compilando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="ff290-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="ff290-126">Percorrer esquemas XML</span><span class="sxs-lookup"><span data-stu-id="ff290-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="ff290-127">Edição de esquemas XML</span><span class="sxs-lookup"><span data-stu-id="ff290-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="ff290-128">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="ff290-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)