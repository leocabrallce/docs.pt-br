---
title: Exportando e importando metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6231d6e4b6562aafbb5b6bd88b65b66f44469023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exporting-and-importing-metadata"></a><span data-ttu-id="7c8a2-102">Exportando e importando metadados</span><span class="sxs-lookup"><span data-stu-id="7c8a2-102">Exporting and Importing Metadata</span></span>
<span data-ttu-id="7c8a2-103">Em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], exportação de metadados é o processo de descrever os pontos de extremidade de serviço e projeção-los em uma representação padronizada paralela que os clientes podem usar para entender como usar o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-103">In [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], exporting metadata is the process of describing service endpoints and projecting them into a parallel, standardized representation that clients can use to understand how to use the service.</span></span> <span data-ttu-id="7c8a2-104">Importação de metadados de serviço é o processo de geração de <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias ou partes de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-104">Importing service metadata is the process of generating <xref:System.ServiceModel.Description.ServiceEndpoint> instances or parts from service metadata.</span></span>  
  
## <a name="exporting-metadata"></a><span data-ttu-id="7c8a2-105">Exportação de metadados</span><span class="sxs-lookup"><span data-stu-id="7c8a2-105">Exporting Metadata</span></span>  
 <span data-ttu-id="7c8a2-106">Para exportar metadados de <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instâncias, use uma implementação do <xref:System.ServiceModel.Description.MetadataExporter> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-106">To export metadata from <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instances, use an implementation of the <xref:System.ServiceModel.Description.MetadataExporter> abstract class.</span></span> <span data-ttu-id="7c8a2-107">O <xref:System.ServiceModel.Description.WsdlExporter> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataExporter> acompanha de classe abstrata [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c8a2-107">The <xref:System.ServiceModel.Description.WsdlExporter> type is the implementation of the <xref:System.ServiceModel.Description.MetadataExporter> abstract class included with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="7c8a2-108">O <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> tipo gera metadados de WSDL Web Services Description Language () com expressões de política anexada encapsuladas em um <xref:System.ServiceModel.Description.MetadataSet> instância.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-108">The <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> type generates Web Services Description Language (WSDL) metadata with attached policy expressions encapsulated in a <xref:System.ServiceModel.Description.MetadataSet> instance.</span></span> <span data-ttu-id="7c8a2-109">Você pode usar um <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instância iterativamente exportar metadados para <xref:System.ServiceModel.Description.ContractDescription> objetos e <xref:System.ServiceModel.Description.ServiceEndpoint> objetos.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-109">You can use a <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instance to iteratively export metadata for <xref:System.ServiceModel.Description.ContractDescription> objects and <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span> <span data-ttu-id="7c8a2-110">Você também pode exportar uma coleção de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos e associá-los com um nome de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-110">You can also export a collection of <xref:System.ServiceModel.Description.ServiceEndpoint> objects and associate them with a specific service name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c8a2-111">Você só pode usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias que contêm o common language runtime (CLR) digite informações, como um `ContractDescription` instância criada usando o `ContractDescription.GetContract` método ou criado como parte do `ServiceDescription` para um `ServiceHost` instância.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-111">You can only use the `WsdlExporter` to export metadata from `ContractDescription` instances that contain common language runtime (CLR) type information, such as a `ContractDescription` instance created using the `ContractDescription.GetContract` method or created as part of the `ServiceDescription` for a `ServiceHost` instance.</span></span> <span data-ttu-id="7c8a2-112">Não é possível usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias importados de metadados de serviço ou construída sem informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-112">You cannot use the `WsdlExporter` to export metadata from `ContractDescription` instances imported from service metadata or constructed without type information.</span></span>  
  
## <a name="importing-metadata"></a><span data-ttu-id="7c8a2-113">Importação de metadados</span><span class="sxs-lookup"><span data-stu-id="7c8a2-113">Importing Metadata</span></span>  
  
### <a name="importing-wsdl-documents"></a><span data-ttu-id="7c8a2-114">Importando documentos WSDL</span><span class="sxs-lookup"><span data-stu-id="7c8a2-114">Importing WSDL Documents</span></span>  
 <span data-ttu-id="7c8a2-115">Para importar os metadados de serviço em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], use uma implementação do <xref:System.ServiceModel.Description.MetadataImporter> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-115">To import service metadata in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], use an implementation of the <xref:System.ServiceModel.Description.MetadataImporter> abstract class.</span></span> <span data-ttu-id="7c8a2-116">O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter> acompanha de classe abstrata [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c8a2-116">The <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type is the implementation of the <xref:System.ServiceModel.Description.MetadataImporter> abstract class included with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="7c8a2-117">O <xref:System.ServiceModel.Description.WsdlImporter> digite importa metadados WSDL com políticas anexados agrupados em um <xref:System.ServiceModel.Description.MetadataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-117">The <xref:System.ServiceModel.Description.WsdlImporter> type imports WSDL metadata with attached policies bundled in a <xref:System.ServiceModel.Description.MetadataSet> object.</span></span>  
  
 <span data-ttu-id="7c8a2-118">O <xref:System.ServiceModel.Description.WsdlImporter> tipo lhe dá controle sobre como importar os metadados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-118">The <xref:System.ServiceModel.Description.WsdlImporter> type gives you control over how to import the metadata.</span></span> <span data-ttu-id="7c8a2-119">Você pode importar todos os pontos de extremidade, todas as associações de ou em todos os contratos.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-119">You can import all of the endpoints, all of the bindings, or all of the contracts.</span></span> <span data-ttu-id="7c8a2-120">Você pode importar todos os pontos de extremidade associados a um serviço específico de WSDL, associação ou tipo de porta.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-120">You can import all of the endpoints associated with a specific WSDL service, binding, or port type.</span></span> <span data-ttu-id="7c8a2-121">Você também pode importar o ponto de extremidade para uma porta específica do WSDL, a associação para uma associação WSDL específica ou o contrato para um tipo específico de porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-121">You can also import the endpoint for a specific WSDL port, the binding for a specific WSDL binding or the contract for a specific WSDL port type.</span></span>  
  
 <span data-ttu-id="7c8a2-122">O <xref:System.ServiceModel.Description.WsdlImporter> também expõe um <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade que permite que você especifique um conjunto de contratos que não precisam ser importados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-122">The <xref:System.ServiceModel.Description.WsdlImporter> also exposes a <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> property that allows you to specify a set of contracts that do not need to be imported.</span></span> <span data-ttu-id="7c8a2-123">O <xref:System.ServiceModel.Description.WsdlImporter> usa os contratos no <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade em vez de importar um contrato com o mesmo nome qualificado de metadados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-123">The <xref:System.ServiceModel.Description.WsdlImporter> uses the contracts in the <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> property instead of importing a contract with the same qualified name from the metadata.</span></span>  
  
### <a name="importing-policies"></a><span data-ttu-id="7c8a2-124">Importação de políticas</span><span class="sxs-lookup"><span data-stu-id="7c8a2-124">Importing Policies</span></span>  
 <span data-ttu-id="7c8a2-125">O <xref:System.ServiceModel.Description.WsdlImporter> tipo coleta as expressões de política anexadas à mensagem, operação, e a política de ponto de extremidade assuntos e, em seguida, usa o <xref:System.ServiceModel.Description.IPolicyImportExtension> implementações no <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> coleção para importar as expressões de política.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-125">The <xref:System.ServiceModel.Description.WsdlImporter> type collects the policy expressions attached to the message, operation, and endpoint policy subjects and then uses the <xref:System.ServiceModel.Description.IPolicyImportExtension> implementations in the <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> collection to import the policy expressions.</span></span>  
  
 <span data-ttu-id="7c8a2-126">A lógica de política de importação lida com referências de política para expressões de política no mesmo documento WSDL automaticamente e é identificada com um `wsu:Id` ou `xml:id` atributo.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-126">The policy import logic automatically handles policy references to policy expressions in the same WSDL document and is identified with a `wsu:Id` or `xml:id` attribute.</span></span> <span data-ttu-id="7c8a2-127">A lógica de política de importação protege os aplicativos referências circulares política limitando o tamanho de uma expressão de diretiva para 4096 nós, em que um nó é um dos seguintes elementos: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-127">The policy import logic protects applications against circular policy references by limiting the size of a policy expression to 4096 nodes, where a node is a one of the following elements: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.</span></span>  
  
 <span data-ttu-id="7c8a2-128">A lógica de política de importação automaticamente normaliza expressões de política.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-128">The policy import logic also automatically normalizes policy expressions.</span></span> <span data-ttu-id="7c8a2-129">Aninhados expressões de política e o `wsp:Optional` atributo não são normalizados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-129">Nested policy expressions and the `wsp:Optional` attribute are not normalized.</span></span> <span data-ttu-id="7c8a2-130">A quantidade de processamento de normalização feito é limitada a 4096 etapas, onde cada etapa resulta em uma declaração de política ou um elemento filho de um `wsp:ExactlyOne` elemento.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-130">The amount of normalization processing done is limited to 4096 steps, where each step yields a policy assertion, or a child element of a `wsp:ExactlyOne` element.</span></span>  
  
 <span data-ttu-id="7c8a2-131">O <xref:System.ServiceModel.Description.WsdlImporter> tipo tenta até 32 combinações de alternativas de política anexadas para as entidades de política WSDL diferentes.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-131">The <xref:System.ServiceModel.Description.WsdlImporter> type tries up to 32 combinations of policy alternatives attached to the different WSDL policy subjects.</span></span> <span data-ttu-id="7c8a2-132">Se nenhuma combinação importa corretamente, a primeira combinação é usada para construir uma associação personalizada parcial.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-132">If no combination imports cleanly, the first combination is used to construct a partial custom binding.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="7c8a2-133">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="7c8a2-133">Error Handling</span></span>  
 <span data-ttu-id="7c8a2-134">Tanto o <xref:System.ServiceModel.Description.MetadataExporter> e <xref:System.ServiceModel.Description.MetadataImporter> tipos expor um `Errors` propriedade que pode conter uma coleção de mensagens de erro e aviso encontradas durante os processos de importação e exportação, respectivamente, que pode ser usado durante a implementação de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-134">Both the <xref:System.ServiceModel.Description.MetadataExporter> and the <xref:System.ServiceModel.Description.MetadataImporter> types expose an `Errors` property that can contain a collection of error and warning messages encountered during the export and import processes, respectively, that can be used when implementing tools.</span></span>  
  
 <span data-ttu-id="7c8a2-135">O <xref:System.ServiceModel.Description.WsdlImporter> tipo geralmente gera uma exceção de uma exceção capturada durante o processo de importação e adiciona um erro correspondente ao seu `Errors` propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-135">The <xref:System.ServiceModel.Description.WsdlImporter> type generally throws an exception for an exception caught during the import process and adds a corresponding error to its `Errors` property.</span></span> <span data-ttu-id="7c8a2-136">O <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, e <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> métodos, no entanto, não gerar essas exceções, por isso, você deve verificar o `Errors` propriedade para determinar se os problemas ocorreram ao chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-136">The <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, and <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> methods, however, do not throw these exceptions, so you must check the `Errors` property to determine if any issues occurred when calling these methods.</span></span>  
  
 <span data-ttu-id="7c8a2-137">O <xref:System.ServiceModel.Description.WsdlExporter> tipo relança qualquer exceção capturada durante o processo de exportação.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-137">The <xref:System.ServiceModel.Description.WsdlExporter> type rethrows any exceptions caught during the export process.</span></span> <span data-ttu-id="7c8a2-138">Essas exceções não são capturadas como erros de `Errors` propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-138">These exceptions are not captured as errors in the `Errors` property.</span></span> <span data-ttu-id="7c8a2-139">Uma vez o <xref:System.ServiceModel.Description.WsdlExporter> lançará uma exceção, ele está em um estado de falha e não pode ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-139">Once the <xref:System.ServiceModel.Description.WsdlExporter> throws an exception, it is in a faulted state and cannot be reused.</span></span> <span data-ttu-id="7c8a2-140">O <xref:System.ServiceModel.Description.WsdlExporter> Adicionar avisos para sua `Errors` propriedade quando uma operação não pode ser exportada porque ele usa o curinga ações e quando os nomes de associação duplicada forem encontrados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-140">The <xref:System.ServiceModel.Description.WsdlExporter> does add warnings to its `Errors` property when an operation cannot be exported because it uses wildcard actions and when duplicate binding names are encountered.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c8a2-141">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7c8a2-141">In This Section</span></span>  
 [<span data-ttu-id="7c8a2-142">Como: importar metadados para pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="7c8a2-142">How to: Import Metadata into Service Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 <span data-ttu-id="7c8a2-143">Descreve como importar metadados baixado para objetos de descrição.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-143">Describes how to import downloaded metadata into description objects.</span></span>  
  
 [<span data-ttu-id="7c8a2-144">Como: exportar metadados de pontos de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="7c8a2-144">How to: Export Metadata from Service Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 <span data-ttu-id="7c8a2-145">Descreve como exportar objetos de descrição nos metadados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-145">Describes how to export description objects into metadata.</span></span>  
  
 [<span data-ttu-id="7c8a2-146">Referência WSDL e ServiceDescription</span><span class="sxs-lookup"><span data-stu-id="7c8a2-146">ServiceDescription and WSDL Reference</span></span>](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 <span data-ttu-id="7c8a2-147">Descreve o mapeamento entre os objetos de descrição e WSDL.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-147">Describes the mapping between the description objects and WSDL.</span></span>  
  
 [<span data-ttu-id="7c8a2-148">Como: usar o Svcutil.exe para exportar metadados de código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="7c8a2-148">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 <span data-ttu-id="7c8a2-149">Descreve o uso de Svcutil.exe para exportar metadados para os serviços, contratos e tipos de dados em assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-149">Describes the use of Svcutil.exe to export metadata for services, contracts, and data types in compiled assemblies.</span></span>  
  
 [<span data-ttu-id="7c8a2-150">Referência de esquema de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="7c8a2-150">Data Contract Schema Reference</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 <span data-ttu-id="7c8a2-151">Descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos de serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="7c8a2-151">Describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language run-time (CLR) types for XML serialization.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7c8a2-152">Referência</span><span class="sxs-lookup"><span data-stu-id="7c8a2-152">Reference</span></span>  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a><span data-ttu-id="7c8a2-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c8a2-153">See Also</span></span>  
 [<span data-ttu-id="7c8a2-154">Exportando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="7c8a2-154">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 [<span data-ttu-id="7c8a2-155">Importando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="7c8a2-155">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)