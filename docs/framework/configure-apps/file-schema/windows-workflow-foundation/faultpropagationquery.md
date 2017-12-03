---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50dc2c4c5d4c1517d6ac3409dc4d932f67cbeb8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="9518d-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="9518d-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="9518d-103">Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9518d-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9518d-104">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="9518d-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9518d-105">Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9518d-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9518d-106">A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.</span><span class="sxs-lookup"><span data-stu-id="9518d-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="9518d-107">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9518d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9518d-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9518d-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9518d-109">\<controle ></span><span class="sxs-lookup"><span data-stu-id="9518d-109">\<tracking></span></span>  
<span data-ttu-id="9518d-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9518d-110">\<trackingProfile></span></span>  
<span data-ttu-id="9518d-111">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="9518d-111">\<workflow></span></span>  
<span data-ttu-id="9518d-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9518d-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="9518d-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="9518d-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9518d-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9518d-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9518d-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9518d-115">Attributes and Elements</span></span>  
 <span data-ttu-id="9518d-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9518d-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9518d-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="9518d-117">Attributes</span></span>  
  
|<span data-ttu-id="9518d-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="9518d-118">Attribute</span></span>|<span data-ttu-id="9518d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9518d-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9518d-120">Nome_da_atividade</span><span class="sxs-lookup"><span data-stu-id="9518d-120">activityName</span></span>|<span data-ttu-id="9518d-121">Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha.</span><span class="sxs-lookup"><span data-stu-id="9518d-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="9518d-122">O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.</span><span class="sxs-lookup"><span data-stu-id="9518d-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="9518d-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="9518d-123">faultHandlerActivityName</span></span>|<span data-ttu-id="9518d-124">Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.</span><span class="sxs-lookup"><span data-stu-id="9518d-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9518d-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9518d-125">Child Elements</span></span>  
 <span data-ttu-id="9518d-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9518d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9518d-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9518d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9518d-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="9518d-128">Element</span></span>|<span data-ttu-id="9518d-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="9518d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9518d-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9518d-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="9518d-131">Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9518d-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9518d-132">Esse evento ocorre sempre que um FaultHandler processa uma falha.</span><span class="sxs-lookup"><span data-stu-id="9518d-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9518d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9518d-133">See Also</span></span>  
 <span data-ttu-id="9518d-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9518d-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9518d-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9518d-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9518d-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9518d-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9518d-137">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="9518d-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)