---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d5e7106de716e4f25e649dbbca716ef66dfa496
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="4003a-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="4003a-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="4003a-103">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="4003a-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="4003a-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4003a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4003a-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="4003a-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4003a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4003a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" 
                        maxResults="Integer" 
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4003a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4003a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4003a-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4003a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4003a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4003a-109">Attributes</span></span>  
  
|<span data-ttu-id="4003a-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="4003a-110">Attribute</span></span>|<span data-ttu-id="4003a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4003a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4003a-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="4003a-112">discoveryEndpoint</span></span>|<span data-ttu-id="4003a-113">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente para procurar por um serviço detectável e encontre seu endereço em tempo de execução automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4003a-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4003a-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4003a-114">Child Elements</span></span>  
  
|<span data-ttu-id="4003a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4003a-115">Element</span></span>|<span data-ttu-id="4003a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4003a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4003a-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="4003a-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="4003a-118">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="4003a-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4003a-119">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="4003a-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4003a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4003a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4003a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="4003a-121">Element</span></span>|<span data-ttu-id="4003a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="4003a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4003a-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="4003a-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="4003a-124">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço de ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4003a-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4003a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4003a-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>