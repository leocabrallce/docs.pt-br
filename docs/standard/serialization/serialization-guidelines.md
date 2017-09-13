---
title: "Diretrizes de serialização"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
caps.latest.revision: 11
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: ff2b5bc2e34a061f577dd839de8b5e834af102b8
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="serialization-guidelines"></a><span data-ttu-id="30d2d-102">Diretrizes de serialização</span><span class="sxs-lookup"><span data-stu-id="30d2d-102">Serialization guidelines</span></span>
<span data-ttu-id="30d2d-103">Este documento lista as diretrizes a serem consideradas na criação de uma API a ser serializado.</span><span class="sxs-lookup"><span data-stu-id="30d2d-103">This document lists the guidelines to consider when designing an API to be serialized.</span></span>  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 <span data-ttu-id="30d2d-104">O .NET oferece três tecnologias de serialização principais que são otimizadas para vários cenários de serialização.</span><span class="sxs-lookup"><span data-stu-id="30d2d-104">.NET offers three main serialization technologies that are optimized for various serialization scenarios.</span></span> <span data-ttu-id="30d2d-105">A tabela a seguir lista essas tecnologias e os principais tipos de .NET relacionados a elas.</span><span class="sxs-lookup"><span data-stu-id="30d2d-105">The following table lists these technologies and the main .NET types related to these technologies.</span></span>  
  
|<span data-ttu-id="30d2d-106">Tecnologia</span><span class="sxs-lookup"><span data-stu-id="30d2d-106">Technology</span></span>|<span data-ttu-id="30d2d-107">Classes relevantes</span><span class="sxs-lookup"><span data-stu-id="30d2d-107">Relevant Classes</span></span>|<span data-ttu-id="30d2d-108">Notas</span><span class="sxs-lookup"><span data-stu-id="30d2d-108">Notes</span></span>|  
|----------------|----------------------|-----------|  
|<span data-ttu-id="30d2d-109">Serialização do contrato de dados</span><span class="sxs-lookup"><span data-stu-id="30d2d-109">Data Contract Serialization</span></span>|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|<span data-ttu-id="30d2d-110">Persistência geral</span><span class="sxs-lookup"><span data-stu-id="30d2d-110">General persistence</span></span><br /><br /> <span data-ttu-id="30d2d-111">Serviços Web</span><span class="sxs-lookup"><span data-stu-id="30d2d-111">Web Services</span></span><br /><br /> <span data-ttu-id="30d2d-112">JSON</span><span class="sxs-lookup"><span data-stu-id="30d2d-112">JSON</span></span>|  
|<span data-ttu-id="30d2d-113">Serialização XML</span><span class="sxs-lookup"><span data-stu-id="30d2d-113">XML Serialization</span></span>|<xref:System.Xml.Serialization.XmlSerializer>|<span data-ttu-id="30d2d-114">Formato XML</span><span class="sxs-lookup"><span data-stu-id="30d2d-114">XML format</span></span> <br /><span data-ttu-id="30d2d-115">com controle total</span><span class="sxs-lookup"><span data-stu-id="30d2d-115">with full control</span></span>|  
|<span data-ttu-id="30d2d-116">Tempo de execução - serialização (binário e SOAP)</span><span class="sxs-lookup"><span data-stu-id="30d2d-116">Runtime -Serialization (Binary and SOAP)</span></span>|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|<span data-ttu-id="30d2d-117">Comunicação remota .NET</span><span class="sxs-lookup"><span data-stu-id="30d2d-117">.NET Remoting</span></span>|  
  
 <span data-ttu-id="30d2d-118">Ao criar novos tipos, você deverá decidir a quais dessas tecnologias, se houver alguma, esses tipos precisam oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="30d2d-118">When you design new types, you should decide which, if any, of these technologies those types need to support.</span></span> <span data-ttu-id="30d2d-119">As diretrizes a seguir descrevem como fazer essa escolha e como fornecer esse suporte.</span><span class="sxs-lookup"><span data-stu-id="30d2d-119">The following guidelines describe how to make that choice and how to provide such support.</span></span> <span data-ttu-id="30d2d-120">Essas diretrizes não foram criadas para ajudar você a escolher qual tecnologia de serialização usará na implementação do aplicativo ou da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="30d2d-120">These guidelines are not meant to help you choose which serialization technology you should use in the implementation of your application or library.</span></span> <span data-ttu-id="30d2d-121">Elas não estão diretamente relacionadas ao design da API e, portanto, não estão dentro do escopo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="30d2d-121">Such guidelines are not directly related to API design and thus are not within the scope of this topic.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="30d2d-122">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="30d2d-122">Guidelines</span></span>  
  
-   <span data-ttu-id="30d2d-123">Pense sobre a serialização ao criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="30d2d-123">DO think about serialization when you design new types.</span></span>  
  
     <span data-ttu-id="30d2d-124">A serialização é uma questão de design importante a ser considerada para qualquer tipo, pois os programas talvez precisem persistir ou transmitir instâncias do tipo.</span><span class="sxs-lookup"><span data-stu-id="30d2d-124">Serialization is an important design consideration for any type, because programs might need to persist or transmit instances of the type.</span></span>  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a><span data-ttu-id="30d2d-125">Escolhendo a tecnologia de serialização correta que receberá suporte</span><span class="sxs-lookup"><span data-stu-id="30d2d-125">Choosing the right serialization technology to support</span></span>  
 <span data-ttu-id="30d2d-126">Qualquer tipo específico pode oferecer suporte a nenhuma, uma ou mais tecnologias de serialização.</span><span class="sxs-lookup"><span data-stu-id="30d2d-126">Any given type can support none, one, or more of the serialization technologies.</span></span>  
  
-   <span data-ttu-id="30d2d-127">CONSIDERE dar suporte à *serialização de contrato de dados* se houver possibilidade de que as instâncias do seu tipo precisem ser persistentes ou usadas nos Serviços Web.</span><span class="sxs-lookup"><span data-stu-id="30d2d-127">CONSIDER supporting *data contract serialization* if instances of your type might need to be persisted or used in Web Services.</span></span>  
  
-   <span data-ttu-id="30d2d-128">CONSIDERE dar suporte à *serialização XML* em vez da ou além da serialização do contrato de dados se você precisar ter mais controle sobre o formato XML gerado quando o tipo for serializado.</span><span class="sxs-lookup"><span data-stu-id="30d2d-128">CONSIDER supporting the *XML serialization* instead of or in addition to data contract serialization if you need more control over the XML format that is produced when the type is serialized.</span></span>  
  
     <span data-ttu-id="30d2d-129">Isso talvez seja necessário em alguns cenários de interoperabilidade no qual você precise usar uma construção XML para a qual não haja suporte na serialização do contrato de dados, por exemplo, para gerar atributos XML.</span><span class="sxs-lookup"><span data-stu-id="30d2d-129">This may be necessary in some interoperability scenarios where you need to use an XML construct that is not supported by data contract serialization, for example, to produce XML attributes.</span></span>  
  
-   <span data-ttu-id="30d2d-130">CONSIDERE dar suporte à *serialização em tempo de execução* se as instâncias do tipo precisarem ultrapassar os limites da comunicação remota .NET.</span><span class="sxs-lookup"><span data-stu-id="30d2d-130">CONSIDER supporting *runtime serialization* if instances of your type need to travel across .NET Remoting boundaries.</span></span>  
  
-   <span data-ttu-id="30d2d-131">EVITE o suporte à serialização em tempo de execução ou à serialização XML apenas por motivos gerais de persistência.</span><span class="sxs-lookup"><span data-stu-id="30d2d-131">AVOID supporting runtime serialization or XML serialization just for general persistence reasons.</span></span> <span data-ttu-id="30d2d-132">Prefira a serialização do contrato de dados em vez disso</span><span class="sxs-lookup"><span data-stu-id="30d2d-132">Prefer data contract serialization instead</span></span>  
  
#### <a name="supporting-data-contract-serialization"></a><span data-ttu-id="30d2d-133">Dando suporte à serialização do contrato de dados</span><span class="sxs-lookup"><span data-stu-id="30d2d-133">Supporting data contract serialization</span></span>  
 <span data-ttu-id="30d2d-134">Os tipos podem dar suporte à serialização do contrato de dados aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> ao tipo e o <xref:System.Runtime.Serialization.DataMemberAttribute> aos membros (campos e propriedades) do tipo.</span><span class="sxs-lookup"><span data-stu-id="30d2d-134">Types can support data contract serialization by applying the <xref:System.Runtime.Serialization.DataContractAttribute> to the type and the <xref:System.Runtime.Serialization.DataMemberAttribute> to the members (fields and properties) of the type.</span></span>  
  
 <span data-ttu-id="30d2d-135">[!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)] [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-135">[!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)] [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]</span></span>  
  
1.  <span data-ttu-id="30d2d-136">CONSIDERE marcar os membros de dados do tipo público se o tipo puder ser usado na confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="30d2d-136">CONSIDER marking data members of your type public if the type can be used in partial trust.</span></span> <span data-ttu-id="30d2d-137">Na confiança total, os serializadores do contrato de dados podem serializar e desserializar tipos e membros não públicos, mas somente os membros públicos podem ser serializados e desserializados na confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="30d2d-137">In full trust, data contract serializers can serialize and deserialize nonpublic types and members, but only public members can be serialized and deserialized in partial trust.</span></span>  
  
2.  <span data-ttu-id="30d2d-138">IMPLEMENTE um getter e um setter em todas as propriedades que têm Data-MemberAttribute.</span><span class="sxs-lookup"><span data-stu-id="30d2d-138">DO implement a getter and setter on all properties that have Data-MemberAttribute.</span></span> <span data-ttu-id="30d2d-139">Os serializadores do contrato de dados requerem o getter e o setter para o tipo a ser considerado serializável.</span><span class="sxs-lookup"><span data-stu-id="30d2d-139">Data contract serializers require both the getter and the setter for the type to be considered serializable.</span></span> <span data-ttu-id="30d2d-140">Se o tipo não será usado na confiança parcial, um ou ambos os acessadores de propriedade poderão ser não públicos.</span><span class="sxs-lookup"><span data-stu-id="30d2d-140">If the type won’t be used in partial trust, one or both of the property accessors can be nonpublic.</span></span>  
  
     <span data-ttu-id="30d2d-141">[!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]  [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-141">[!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]  [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]</span></span>  
  
3.  <span data-ttu-id="30d2d-142">CONSIDERE o uso de retornos de chamada de serialização para a inicialização de instâncias desserializadas.</span><span class="sxs-lookup"><span data-stu-id="30d2d-142">CONSIDER using the serialization callbacks for initialization of deserialized instances.</span></span>  
  
     <span data-ttu-id="30d2d-143">Os construtores não são chamados quando os objetos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="30d2d-143">Constructors are not called when objects are deserialized.</span></span> <span data-ttu-id="30d2d-144">Portanto, qualquer lógica que executada durante a construção normal precisa ser implementada como um dos *retornos de chamada de serialização*.</span><span class="sxs-lookup"><span data-stu-id="30d2d-144">Therefore, any logic that executes during normal construction needs to be implemented as one of the *serialization callbacks*.</span></span>  
  
     <span data-ttu-id="30d2d-145">[!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]  [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-145">[!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]  [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]</span></span>  
  
     <span data-ttu-id="30d2d-146"><xref:System.Runtime.Serialization.OnDeserializedAttribute> é o atributo de retorno de chamada mais usado.</span><span class="sxs-lookup"><span data-stu-id="30d2d-146">The <xref:System.Runtime.Serialization.OnDeserializedAttribute> attribute is the most commonly used callback attribute.</span></span> <span data-ttu-id="30d2d-147">Os outros atributos da família são <xref:System.Runtime.Serialization.OnDeserializingAttribute>,</span><span class="sxs-lookup"><span data-stu-id="30d2d-147">The other attributes in the family are <xref:System.Runtime.Serialization.OnDeserializingAttribute>,</span></span>    
    <span data-ttu-id="30d2d-148"><xref:System.Runtime.Serialization.OnSerializingAttribute> e <xref:System.Runtime.Serialization.OnSerializedAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30d2d-148"><xref:System.Runtime.Serialization.OnSerializingAttribute>, and <xref:System.Runtime.Serialization.OnSerializedAttribute>.</span></span> <span data-ttu-id="30d2d-149">Eles podem ser usados para marcar os retornos de chamada que são executados antes de desserialização, antes da serialização e, por fim, após a serialização, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="30d2d-149">They can be used to mark callbacks that get executed before deserialization, before serialization, and finally, after serialization, respectively.</span></span>  
  
4.  <span data-ttu-id="30d2d-150">CONSIDERE o uso do <xref:System.Runtime.Serialization.KnownTypeAttribute> para indicar os tipos concretos que devem ser usados ao desserializar um gráfico de objeto complexo.</span><span class="sxs-lookup"><span data-stu-id="30d2d-150">CONSIDER using the <xref:System.Runtime.Serialization.KnownTypeAttribute> to indicate concrete types that should be used when deserializing a complex object graph.</span></span>  
  
     <span data-ttu-id="30d2d-151">Por exemplo, se o tipo de um membro de dados desserializado for representado por uma classe abstrata, o serializador precisará das informações de *tipo conhecido* para decidir qual tipo concreto será instanciado e atribuído ao membro.</span><span class="sxs-lookup"><span data-stu-id="30d2d-151">For example, if a type of a deserialized data member is represented by an abstract class, the serializer will need the *known type* information to decide what concrete type to instantiate and assign to the member.</span></span> <span data-ttu-id="30d2d-152">Se o tipo conhecido não for especificado por meio do atributo, ele precisará ser passado para o serializador explicitamente (você pode fazer isso passando os tipos conhecidos para o construtor do serializador) ou precisará ser especificado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="30d2d-152">If the known type is not specified using the attribute, it will need to be passed to the serializer explicitly (you can do it by passing known types to the serializer constructor) or it will need to be specified in the configuration file.</span></span>  
  
     <span data-ttu-id="30d2d-153">[!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]  [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-153">[!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]  [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]</span></span>  
  
     <span data-ttu-id="30d2d-154">Nos casos em que a lista de tipos conhecidos não é conhecida estaticamente (quando a classe **Person** é compilada), **KnownTypeAttribute** também pode apontar para um método que retorna uma lista de tipos conhecidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30d2d-154">In cases where the list of known types is not known statically (when the **Person** class is compiled), the **KnownTypeAttribute** can also point to a method that returns a list of known types at runtime.</span></span>  
  
5.  <span data-ttu-id="30d2d-155">Considere a compatibilidade com versões anteriores e posteriores ao criar ou modificar tipos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="30d2d-155">DO consider backward and forward compatibility when creating or changing serializable types.</span></span>  
  
     <span data-ttu-id="30d2d-156">Tenha em mente que os fluxos serializados de versões futuras do tipo podem ser desserializados na versão atual de tipo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="30d2d-156">Keep in mind that serialized streams of future versions of your type can be deserialized into the current version of the type, and vice versa.</span></span> <span data-ttu-id="30d2d-157">Verifique se compreendeu que os membros de dados, até mesmo os privados e internos, não podem alterar seus nomes, tipos ou mesmo sua ordem nas versões futuras do tipo, a menos que se tome um cuidado especial para preservar o contrato usando parâmetros explícitos para os atributos do contrato de dados. Teste a compatibilidade da serialização ao fazer alterações nos tipos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="30d2d-157">Make sure you understand that data members, even private and internal, cannot change their names, types, or even their order in future versions of the type unless special care is taken to preserve the contract using explicit parameters to the data contract attributes.Test compatibility of serialization when making changes to serializable types.</span></span> <span data-ttu-id="30d2d-158">Tente desserializar a nova versão em uma versão antiga e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="30d2d-158">Try deserializing the new version into an old version, and vice versa.</span></span>  
  
6.  <span data-ttu-id="30d2d-159">CONSIDERE implementar a interface <xref:System.Runtime.Serialization.IExtensibleDataObject> para permitir o ciclo completo entre diferentes versões do tipo.</span><span class="sxs-lookup"><span data-stu-id="30d2d-159">CONSIDER implementing <xref:System.Runtime.Serialization.IExtensibleDataObject> interface to allow round-tripping between different versions of the type.</span></span>  
  
     <span data-ttu-id="30d2d-160">A interface permite que o serializador assegure de que nenhum dado sejam perdido durante o ciclo completo.</span><span class="sxs-lookup"><span data-stu-id="30d2d-160">The interface allows the serializer to ensure that no data is lost during round-tripping.</span></span> <span data-ttu-id="30d2d-161">A propriedade <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> armazena todos os dados da versão futura do tipo desconhecido na versão atual.</span><span class="sxs-lookup"><span data-stu-id="30d2d-161">The <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property stores any data from the future version of the type that is unknown to the current version.</span></span> <span data-ttu-id="30d2d-162">Quando a versão atual for serializada e desserializada subsequentemente em uma versão futura, os dados adicionais estarão disponíveis no fluxo serializado através do valor da propriedade **ExtensionData**.</span><span class="sxs-lookup"><span data-stu-id="30d2d-162">When the current version is subsequently serialized and deserialized into a future version, the additional data will be available in the serialized stream through the **ExtensionData** property value.</span></span>  
  
     <span data-ttu-id="30d2d-163">[!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]  [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-163">[!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]  [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]</span></span>  
  
     <span data-ttu-id="30d2d-164">Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="30d2d-164">For more information, see [Forward-Compatible Data Contracts](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
#### <a name="supporting-xml-serialization"></a><span data-ttu-id="30d2d-165">Suporte à serialização XML</span><span class="sxs-lookup"><span data-stu-id="30d2d-165">Supporting XML serialization</span></span>  
 <span data-ttu-id="30d2d-166">A serialização do contrato de dados é a tecnologia de serialização principal (padrão) do .NET Framework, mas há situações de serialização para as quais a serialização do contrato de dados não oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="30d2d-166">Data contract serialization is the main (default) serialization technology in the .NET Framework, but there are serialization scenarios that data contract serialization does not support.</span></span> <span data-ttu-id="30d2d-167">Por exemplo, ela não fornece controle total sobre o formato XML gerado ou consumido pelo serializador.</span><span class="sxs-lookup"><span data-stu-id="30d2d-167">For example, it does not give you full control over the shape of XML produced or consumed by the serializer.</span></span> <span data-ttu-id="30d2d-168">Se esse controle fino for necessário, a *serialização XML* precisará ser usada e você precisará criar seus tipos para oferecer suporte essa tecnologia de serialização.</span><span class="sxs-lookup"><span data-stu-id="30d2d-168">If such fine control is required, *XML serialization* has to be used, and you need to design your types to support this serialization technology.</span></span>  
  
1.  <span data-ttu-id="30d2d-169">EVITE criar os tipos especificamente para a Serialização XML, a menos que você tenha um motivo muito forte para controlar o formato do XML gerado</span><span class="sxs-lookup"><span data-stu-id="30d2d-169">AVOID designing your types specifically for XML Serialization, unless you have a very strong reason to control the shape of the XML produced.</span></span> <span data-ttu-id="30d2d-170">Essa tecnologia de serialização foi substituída pela serialização do contrato de dados abordada na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="30d2d-170">This serialization technology has been superseded by the Data Contract Serialization discussed in the previous section.</span></span>  
  
     <span data-ttu-id="30d2d-171">Em outras palavras, não aplique atributos do namespace <xref:System.Runtime.Serialization> a novos tipos, a menos que você saiba que o tipo será usado com a Serialização XML.</span><span class="sxs-lookup"><span data-stu-id="30d2d-171">In other words, don’t apply attributes from the <xref:System.Runtime.Serialization> namespace to new types, unless you know that the type will be used with XML Serialization.</span></span> <span data-ttu-id="30d2d-172">O exemplo a seguir mostra como **System.Xml.Serialization** pode ser usado para controlar a forma do XML gerado.</span><span class="sxs-lookup"><span data-stu-id="30d2d-172">The following example shows how **System.Xml.Serialization** can be used to control the shape of the XML -produced.</span></span>  
  
     <span data-ttu-id="30d2d-173">[!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]  [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-173">[!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]  [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]</span></span>  
  
2.  <span data-ttu-id="30d2d-174">CONSIDERE implementar a interface <xref:System.Xml.Serialization.IXmlSerializable> se quiser ainda mais controle sobre o formato do XML serializado do que o que é oferecido aplicando os atributos de Serialização XML.</span><span class="sxs-lookup"><span data-stu-id="30d2d-174">CONSIDER implementing the <xref:System.Xml.Serialization.IXmlSerializable> interface if you want even more control over the shape of the serialized XML than what’s offered by applying the XML Serialization attributes.</span></span> <span data-ttu-id="30d2d-175">Dois métodos da interface <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>e <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> permitem que você controle totalmente o fluxo XML serializável.</span><span class="sxs-lookup"><span data-stu-id="30d2d-175">Two methods of the interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>and <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, allow you to fully control the serialized XML stream.</span></span> <span data-ttu-id="30d2d-176">Você também pode controlar o esquema XML gerado para o tipo aplicando o atributo <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30d2d-176">You can also control the XML schema that gets generated for the type by applying the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute.</span></span>  
  
#### <a name="supporting-runtime-serialization"></a><span data-ttu-id="30d2d-177">Suporte à serialização em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="30d2d-177">Supporting runtime serialization</span></span>  
 <span data-ttu-id="30d2d-178">A *serialização em tempo de execução* é uma tecnologia usada pelo .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="30d2d-178">*Runtime serialization* is a technology used by .NET Remoting.</span></span> <span data-ttu-id="30d2d-179">Se você considerar que os tipos serão transportados por meio da comunicação remota .NET, será necessário verificar se eles oferecem suporte à serialização em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30d2d-179">If you think your types will be transported using .NET Remoting, you need to make sure they support runtime serialization.</span></span>  
  
 <span data-ttu-id="30d2d-180">O suporte básico da *serialização em tempo de execução* pode ser fornecido aplicando o atributo <xref:System.SerializableAttribute> e os cenários mais avançados envolvem a implementação de um *padrão serializável de tempo de execução* simples (implemente –<xref:System.Runtime.Serialization.ISerializable> e forneça um construtor de serialização).</span><span class="sxs-lookup"><span data-stu-id="30d2d-180">The basic support for *runtime serialization* can be provided by applying the <xref:System.SerializableAttribute> attribute, and more advanced scenarios involve implementing a simple *runtime serializable pattern* (implement -<xref:System.Runtime.Serialization.ISerializable> and provide a serialization constructor).</span></span>  
  
1.  <span data-ttu-id="30d2d-181">CONSIDERE o suporte à serialização em tempo de execução se os tipos forem usados com a comunicação remota .NET.</span><span class="sxs-lookup"><span data-stu-id="30d2d-181">CONSIDER supporting runtime serialization if your types will be used with .NET Remoting.</span></span> <span data-ttu-id="30d2d-182">Por exemplo, o namespace <xref:System.AddIn> usa a comunicação remota .NET e, portanto, todos os tipos trocados entre os suplementos **System.AddIn** precisam oferecer suporte à serialização em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30d2d-182">For example, the <xref:System.AddIn> namespace uses .NET Remoting, and so all types exchanged between **System.AddIn** add-ins need to support runtime serialization.</span></span>  
  
     <span data-ttu-id="30d2d-183">[!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]  [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-183">[!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]  [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]</span></span>  
  
2.  <span data-ttu-id="30d2d-184">CONSIDERE a implementação do *padrão serializável em tempo de execução* se quiser controle completo sobre o processo de serialização.</span><span class="sxs-lookup"><span data-stu-id="30d2d-184">CONSIDER implementing the *runtime serializable pattern* if you want complete control over the serialization process.</span></span> <span data-ttu-id="30d2d-185">Por exemplo, se você quiser transformar os dados à medida que eles forem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="30d2d-185">For example, if you want to transform data as it gets serialized or deserialized.</span></span>  
  
     <span data-ttu-id="30d2d-186">O padrão é muito simples.</span><span class="sxs-lookup"><span data-stu-id="30d2d-186">The pattern is very simple.</span></span> <span data-ttu-id="30d2d-187">Tudo o que você precisa fazer é implementar a interface <xref:System.Runtime.Serialization.ISerializable> e fornecer um construtor especial que é usado quando o objeto é desserializado.</span><span class="sxs-lookup"><span data-stu-id="30d2d-187">All you need to do is implement the <xref:System.Runtime.Serialization.ISerializable> interface and provide a special constructor that is used when the object is deserialized.</span></span>  
  
     <span data-ttu-id="30d2d-188">[!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]  [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-188">[!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]  [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]</span></span>  
  
3.  <span data-ttu-id="30d2d-189">PROTEJA o construtor de serialização e forneça dois parâmetros tipados e nomeados exatamente conforme mostrado no exemplo aqui.</span><span class="sxs-lookup"><span data-stu-id="30d2d-189">DO make the serialization constructor protected and provide two parameters typed and named exactly as shown in the sample here.</span></span>  
  
     <span data-ttu-id="30d2d-190">[!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]  [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-190">[!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]  [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]</span></span>  
  
4.  <span data-ttu-id="30d2d-191">IMPLEMENTE os membros ISerializable explicitamente.</span><span class="sxs-lookup"><span data-stu-id="30d2d-191">DO implement the ISerializable members explicitly.</span></span>  
  
     <span data-ttu-id="30d2d-192">[!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]  [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-192">[!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]  [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]</span></span>  
  
5.  <span data-ttu-id="30d2d-193">Aplicar uma demanda de link para a implementação **ISerializable.GetObjectData**.</span><span class="sxs-lookup"><span data-stu-id="30d2d-193">DO apply a link demand to **ISerializable.GetObjectData** implementation.</span></span> <span data-ttu-id="30d2d-194">Isso garantirá que o somente núcleo completamente confiável e o serializador em tempo de execução terão acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="30d2d-194">This ensures that only fully trusted core and the runtime serializer have access to the member.</span></span>  
  
     <span data-ttu-id="30d2d-195">[!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]  [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]</span><span class="sxs-lookup"><span data-stu-id="30d2d-195">[!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]  [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d2d-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30d2d-196">See also</span></span>  
 <span data-ttu-id="30d2d-197">[Usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md) </span><span class="sxs-lookup"><span data-stu-id="30d2d-197">[Using Data Contracts](../../../docs/framework/wcf/feature-details/using-data-contracts.md) </span></span>  
 <span data-ttu-id="30d2d-198">[Serializador de contrato de dados](../../../docs/framework/wcf/feature-details/data-contract-serializer.md) </span><span class="sxs-lookup"><span data-stu-id="30d2d-198">[Data Contract Serializer](../../../docs/framework/wcf/feature-details/data-contract-serializer.md) </span></span>  
 <span data-ttu-id="30d2d-199">[Tipos com suporte pelo serializador de contrato de dados](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md) </span><span class="sxs-lookup"><span data-stu-id="30d2d-199">[Types Supported by the Data Contract Serializer](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md) </span></span>  
 <span data-ttu-id="30d2d-200">[Serialização Binária](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="30d2d-200">[Binary Serialization](binary-serialization.md) </span></span>  
 <span data-ttu-id="30d2d-201">[Objetos remotos](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) </span><span class="sxs-lookup"><span data-stu-id="30d2d-201">[Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) </span></span>  
 <span data-ttu-id="30d2d-202">[Serialização XML e SOAP](xml-and-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="30d2d-202">[XML and SOAP Serialization](xml-and-soap-serialization.md) </span></span>  
 [<span data-ttu-id="30d2d-203">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="30d2d-203">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
