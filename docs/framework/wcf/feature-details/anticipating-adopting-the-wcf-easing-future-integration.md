---
title: "Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f60b2566895acfd7d2b749729fab9c3f5deb20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="4326c-102">Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração</span><span class="sxs-lookup"><span data-stu-id="4326c-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="4326c-103">Se você usar o ASP.NET e prever usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no futuro, este tópico fornece diretrizes para garantir que novos serviços da Web do ASP.NET funciona bem junto com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4326c-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="4326c-104">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="4326c-104">General Recommendations</span></span>  
 <span data-ttu-id="4326c-105">Adote o ASP.NET 2.0 para quaisquer novos serviços.</span><span class="sxs-lookup"><span data-stu-id="4326c-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="4326c-106">Isso fornecerá acesso aos aprimoramentos e melhorias da nova versão.</span><span class="sxs-lookup"><span data-stu-id="4326c-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="4326c-107">No entanto, ele também permitirá a possibilidade de usar o ASP.NET 2.0 componentes junto com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4326c-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="4326c-108">Protocolos</span><span class="sxs-lookup"><span data-stu-id="4326c-108">Protocols</span></span>  
 <span data-ttu-id="4326c-109">Use o recurso novo do ASP.NET 2.0 para validar a conformidade com o WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="4326c-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="4326c-110">Serviços Web do ASP.NET que estão de acordo com WS-I Basic Profile 1.1 será interoperável com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefinidos de associação, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="4326c-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="4326c-111">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="4326c-111">Service Development</span></span>  
 <span data-ttu-id="4326c-112">Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para os métodos com base no nome totalmente qualificado do elemento de corpo de mensagem SOAP em vez de um cabeçalho HTTP SOAPAction.</span><span class="sxs-lookup"><span data-stu-id="4326c-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4326c-113">usa o cabeçalho HTTP SOAPAction para roteamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4326c-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="4326c-114">Representação de dados</span><span class="sxs-lookup"><span data-stu-id="4326c-114">Data Representation</span></span>  
 <span data-ttu-id="4326c-115">O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, fornecido o namespace para o XML é definido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="4326c-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="4326c-116">Quando definir um tipo de dados para uso com o ASP.NET Web services antecipadamente adotando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no futuro, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4326c-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="4326c-117">Defina o tipo usando classes do .NET Framework em vez de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="4326c-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="4326c-118">Adicione somente o <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.XmlRootAttribute> para a classe usando o último definir explicitamente o namespace para o tipo.</span><span class="sxs-lookup"><span data-stu-id="4326c-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="4326c-119">Fazer sem adicionar atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework é para ser convertido em XML.</span><span class="sxs-lookup"><span data-stu-id="4326c-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="4326c-120">Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão.</span><span class="sxs-lookup"><span data-stu-id="4326c-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="4326c-121">Os tipos usados em mensagens, serviços Web ASP.NET poderão ser processados como contratos de dados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, gerando, entre outros benefícios, melhor desempenho em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4326c-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="4326c-122">Segurança</span><span class="sxs-lookup"><span data-stu-id="4326c-122">Security</span></span>  
 <span data-ttu-id="4326c-123">Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="4326c-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4326c-124">os clientes não dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="4326c-124"> clients do not support them.</span></span> <span data-ttu-id="4326c-125">Se um serviço precisa ser protegido, use as opções fornecidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], porque essas opções são mais sofisticadas e baseadas em protocolos padrão.</span><span class="sxs-lookup"><span data-stu-id="4326c-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4326c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4326c-126">See Also</span></span>  
 [<span data-ttu-id="4326c-127">Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura</span><span class="sxs-lookup"><span data-stu-id="4326c-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)