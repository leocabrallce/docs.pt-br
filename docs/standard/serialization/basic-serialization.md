---
title: "Serialização básica"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
caps.latest.revision: 7
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 334fe65c41e283f9ea6335183da1b2dab53e30af
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="basic-serialization"></a><span data-ttu-id="7114b-102">Serialização básica</span><span class="sxs-lookup"><span data-stu-id="7114b-102">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="7114b-103">A maneira mais fácil de tornar uma classe serializável é marcá-la com o atributo <xref:System.SerializableAttribute>, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="7114b-103">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="7114b-104">O exemplo de código a seguir mostra como uma instância dessa classe pode ser serializada para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7114b-104">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="7114b-105">Este exemplo usa um formatador binário para fazer a serialização.</span><span class="sxs-lookup"><span data-stu-id="7114b-105">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="7114b-106">Basta criar uma instância do fluxo e do formatador que você pretende usar e, em seguida, chamar o método **Serialize** no formatador.</span><span class="sxs-lookup"><span data-stu-id="7114b-106">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="7114b-107">O fluxo e o objeto a serem serializados são fornecidos como parâmetros para essa chamada.</span><span class="sxs-lookup"><span data-stu-id="7114b-107">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="7114b-108">Embora não seja explicitamente demonstrado neste exemplo, todas as variáveis de membro de uma classe serão serializadas — mesmo variáveis marcadas como particulares.</span><span class="sxs-lookup"><span data-stu-id="7114b-108">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="7114b-109">Neste aspecto, a serialização binária é diferente da classe <xref:System.Xml.Serialization.XmlSerializer>, que serializa somente campos públicos.</span><span class="sxs-lookup"><span data-stu-id="7114b-109">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="7114b-110">Para obter informações sobre como excluir variáveis de membro da serialização binária, consulte [Serialização seletiva](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="7114b-110">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="7114b-111">A restauração do objeto de volta para o estado anterior também é fácil.</span><span class="sxs-lookup"><span data-stu-id="7114b-111">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="7114b-112">Primeiro, crie um fluxo para leitura e um <xref:System.Runtime.Serialization.Formatter> e, em seguida, instrua o formatador a desserializar o objeto.</span><span class="sxs-lookup"><span data-stu-id="7114b-112">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="7114b-113">O exemplo de código a seguir mostra como isso é feito.</span><span class="sxs-lookup"><span data-stu-id="7114b-113">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="7114b-114">O <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> usado acima é muito eficiente e produz um fluxo de bytes compacto.</span><span class="sxs-lookup"><span data-stu-id="7114b-114">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="7114b-115">Todos os objetos serializados com esse formatador também podem ser desserializados com ele, o que o torna uma ferramenta ideal para serializar objetos que serão desserializados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7114b-115">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="7114b-116">É importante observar que os construtores não são chamados quando um objeto é desserializado.</span><span class="sxs-lookup"><span data-stu-id="7114b-116">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="7114b-117">Essa restrição é colocada na desserialização por razões de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7114b-117">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="7114b-118">No entanto, isso viola alguns dos contratos normais que o tempo de execução cria com o gravador de objeto, e os desenvolvedores devem compreender as ramificações ao marcar um objeto como serializável.</span><span class="sxs-lookup"><span data-stu-id="7114b-118">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="7114b-119">Se a portabilidade for um requisito, use o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7114b-119">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="7114b-120">Basta substituir o **BinaryFormatter** no código acima por **SoapFormatter** e chamar **Serialize** e **Deserialize** como antes.</span><span class="sxs-lookup"><span data-stu-id="7114b-120">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="7114b-121">Esse formatador produz a seguinte saída para o exemplo usado acima.</span><span class="sxs-lookup"><span data-stu-id="7114b-121">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="7114b-122">É importante observar que o atributo [Serializable](xref:System.SerializableAttribute) não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="7114b-122">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="7114b-123">Se você derivar uma nova classe `MyObject`, a nova classe também deverá ser marcada com o atributo ou não poderá ser serializada.</span><span class="sxs-lookup"><span data-stu-id="7114b-123">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="7114b-124">Por exemplo, ao tentar serializar uma instância da classe abaixo, você obterá uma <xref:System.Runtime.Serialization.SerializationException> informando que o tipo `MyStuff` não está marcado como serializável.</span><span class="sxs-lookup"><span data-stu-id="7114b-124">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="7114b-125">O uso do atributo [Serializable](xref:System.SerializableAttribute) é conveniente, mas tem limitações, conforme demonstrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7114b-125">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="7114b-126">Consulte as [Diretrizes de serialização](serialization-guidelines.md) para obter informações sobre quando é necessário marcar uma classe para serialização.</span><span class="sxs-lookup"><span data-stu-id="7114b-126">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="7114b-127">A serialização não pode ser adicionada a uma classe depois que ela foi compilada.</span><span class="sxs-lookup"><span data-stu-id="7114b-127">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7114b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7114b-128">See also</span></span>  
 <span data-ttu-id="7114b-129">[Serialização Binária](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="7114b-129">[Binary Serialization](binary-serialization.md) </span></span>  
 [<span data-ttu-id="7114b-130">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="7114b-130">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
