---
title: "Identificando os limites de modelo de domínio para cada microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Identificando os limites de modelo de domínio para cada microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6fef11e5718706701abb29149c4c4a23ba39bde0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a><span data-ttu-id="9d684-104">Identificar limites de modelo de domínio para cada microsserviço</span><span class="sxs-lookup"><span data-stu-id="9d684-104">Identify domain-model boundaries for each microservice</span></span>

<span data-ttu-id="9d684-105">O objetivo de identificar os limites do modelo e o tamanho de cada microsserviço é não get para a separação mais granular possíveis, embora deve tendem para microservices pequeno se possível.</span><span class="sxs-lookup"><span data-stu-id="9d684-105">The goal when identifying model boundaries and size for each microservice is not to get to the most granular separation possible, although you should tend toward small microservices if possible.</span></span> <span data-ttu-id="9d684-106">Em vez disso, sua meta deve ser para obter a separação mais significativa orientada por seu conhecimento do domínio.</span><span class="sxs-lookup"><span data-stu-id="9d684-106">Instead, your goal should be to get to the most meaningful separation guided by your domain knowledge.</span></span> <span data-ttu-id="9d684-107">A ênfase não é o tamanho, mas em recursos de negócios.</span><span class="sxs-lookup"><span data-stu-id="9d684-107">The emphasis is not on the size, but instead on business capabilities.</span></span> <span data-ttu-id="9d684-108">Além disso, se houver limpar coesão necessários para uma determinada área do aplicativo com base em um grande número de dependências, que indica a necessidade de um único microsserviço, muito.</span><span class="sxs-lookup"><span data-stu-id="9d684-108">In addition, if there is clear cohesion needed for a certain area of the application based on a high number of dependencies, that indicates the need for a single microservice, too.</span></span> <span data-ttu-id="9d684-109">Coesão é uma maneira de identificar como separar ou microservices juntos de grupo.</span><span class="sxs-lookup"><span data-stu-id="9d684-109">Cohesion is a way to identify how to break apart or group together microservices.</span></span> <span data-ttu-id="9d684-110">Por fim, enquanto você obtém mais dados de Conhecimento sobre o domínio, você deve adaptar o tamanho do seu microsserviço iterativamente.</span><span class="sxs-lookup"><span data-stu-id="9d684-110">Ultimately, while you gain more knowledge about the domain, you should adapt the size of your microservice, iteratively.</span></span> <span data-ttu-id="9d684-111">Localizar o tamanho correto não é um processo única.</span><span class="sxs-lookup"><span data-stu-id="9d684-111">Finding the right size is not a one-shot process.</span></span>

<span data-ttu-id="9d684-112">[SAM Newman](http://samnewman.io/), um promotor reconhecida de microservices e autor do livro [Microservices de construção](http://samnewman.io/books/building_microservices/), realça o que você deve projetar seu microservices baseado no padrão de contexto limitado (BC) (parte do controlado por domínio design), conforme apresentado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9d684-112">[Sam Newman](http://samnewman.io/), a recognized promoter of microservices and author of the book [Building Microservices](http://samnewman.io/books/building_microservices/), highlights that you should design your microservices based on the Bounded Context (BC) pattern (part of domain-driven design), as introduced earlier.</span></span> <span data-ttu-id="9d684-113">Às vezes, uma continuidade de negócios pode ser composta de vários serviços físicos, mas não vice-versa.</span><span class="sxs-lookup"><span data-stu-id="9d684-113">Sometimes, a BC could be composed of several physical services, but not vice versa.</span></span>

<span data-ttu-id="9d684-114">Aplica um modelo de domínio com entidades de domínio específico dentro de um BC concreto ou microsserviço.</span><span class="sxs-lookup"><span data-stu-id="9d684-114">A domain model with specific domain entities applies within a concrete BC or microservice.</span></span> <span data-ttu-id="9d684-115">Um BC delimita a aplicabilidade de um modelo de domínio e os membros da equipe do desenvolvedor dá uma compreensão clara e compartilhada dos quais devem ser consistente e que podem ser desenvolvido de modo independente.</span><span class="sxs-lookup"><span data-stu-id="9d684-115">A BC delimits the applicability of a domain model and gives developer team members a clear and shared understanding of what must be cohesive and what can be developed independently.</span></span> <span data-ttu-id="9d684-116">Esses são os mesmos objetivos de microservices.</span><span class="sxs-lookup"><span data-stu-id="9d684-116">These are the same goals for microservices.</span></span>

<span data-ttu-id="9d684-117">Outra ferramenta que informa a sua escolha de design é [lei de Conway](https://en.wikipedia.org/wiki/Conway%27s_law), indicando que um aplicativo irão refletir os limites sociais da organização que produziu.</span><span class="sxs-lookup"><span data-stu-id="9d684-117">Another tool that informs your design choice is [Conway’s law](https://en.wikipedia.org/wiki/Conway%27s_law), which states that an application will reflect the social boundaries of the organization that produced it.</span></span> <span data-ttu-id="9d684-118">Mas, às vezes, o oposto é verdadeiro, a organização da empresa é formada pelo software.</span><span class="sxs-lookup"><span data-stu-id="9d684-118">But sometimes the opposite is true—the company’s organization is formed by the software.</span></span> <span data-ttu-id="9d684-119">Você precisará reverter lei de Conway e os limites de compilação a maneira como deseja que a empresa sejam organizados, inclinada em direção de consultoria do processo de negócios.</span><span class="sxs-lookup"><span data-stu-id="9d684-119">You might need to reverse Conway’s law and build the boundaries the way you want the company to be organized, leaning toward business process consulting.</span></span>

<span data-ttu-id="9d684-120">Para identificar os contextos limitados, um padrão DDD que pode ser usado para isso é o [contexto mapeamento padrão](https://www.infoq.com/articles/ddd-contextmapping).</span><span class="sxs-lookup"><span data-stu-id="9d684-120">In order to identify bounded contexts, a DDD pattern that can be used for this is the [Context Mapping pattern](https://www.infoq.com/articles/ddd-contextmapping).</span></span> <span data-ttu-id="9d684-121">Mapeamento de contexto, você identificar os vários contextos no aplicativo e seus limites.</span><span class="sxs-lookup"><span data-stu-id="9d684-121">With Context Mapping, you identify the various contexts in the application and their boundaries.</span></span> <span data-ttu-id="9d684-122">É comum que haja um contexto diferente e limites para cada subsistema pequeno, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="9d684-122">It is common to have a different context and boundary for each small subsystem, for instance.</span></span> <span data-ttu-id="9d684-123">O mapa de contexto é uma maneira de definir e tornar explícita esses limites entre domínios.</span><span class="sxs-lookup"><span data-stu-id="9d684-123">The Context Map is a way to define and make explicit those boundaries between domains.</span></span> <span data-ttu-id="9d684-124">Um BC autônomo e inclui os detalhes de um único domínio — detalhes como as entidades de domínio — e define os contratos de integração com outros BCs.</span><span class="sxs-lookup"><span data-stu-id="9d684-124">A BC is autonomous and includes the details of a single domain—details like the domain entities—and defines integration contracts with other BCs.</span></span> <span data-ttu-id="9d684-125">Isso é semelhante à definição de um microsserviço: é autônomo, ele implementa determinados recursos de domínio e ele deve fornecer interfaces.</span><span class="sxs-lookup"><span data-stu-id="9d684-125">This is similar to the definition of a microservice: it is autonomous, it implements certain domain capability, and it must provide interfaces.</span></span> <span data-ttu-id="9d684-126">Isso é porque o mapeamento de contexto e o padrão de contexto limitado bom abordagens para identificar os limites de modelo de domínio do seu microservices.</span><span class="sxs-lookup"><span data-stu-id="9d684-126">This is why Context Mapping and the Bounded Context pattern are good approaches for identifying the domain model boundaries of your microservices.</span></span>

<span data-ttu-id="9d684-127">Ao criar um aplicativo grande, você verá como seu modelo de domínio pode ser fragmentado — um especialista de domínio do domínio de catálogo nomeará entidades de maneira diferente nos domínios de catálogo e inventário de um domínio de envio especializado, para a instância.</span><span class="sxs-lookup"><span data-stu-id="9d684-127">When designing a large application, you will see how its domain model can be fragmented — a domain expert from the catalog domain will name entities differently in the catalog and inventory domains than a shipping domain expert, for instance.</span></span> <span data-ttu-id="9d684-128">Ou a entidade de usuário de domínio pode ser diferente em tamanho e número de atributos ao lidar com um especialista do CRM que deseja armazenar todos os detalhes sobre o cliente do que para especialista ordenação do domínio que precisa apenas parcial de dados sobre o cliente.</span><span class="sxs-lookup"><span data-stu-id="9d684-128">Or the user domain entity might be different in size and number of attributes when dealing with a CRM expert who wants to store every detail about the customer than for an ordering domain expert who just needs partial data about the customer.</span></span> <span data-ttu-id="9d684-129">É muito difícil de resolver a ambiguidade de todos os termos do domínio em todos os domínios relacionados a um aplicativo grande.</span><span class="sxs-lookup"><span data-stu-id="9d684-129">It is very hard to disambiguate all domain terms across all the domains related to a large application.</span></span> <span data-ttu-id="9d684-130">Mas o mais importante é que você não deve tentar unificar os termos; em vez disso, aceite as diferenças e riqueza fornecidas por cada domínio.</span><span class="sxs-lookup"><span data-stu-id="9d684-130">But the most important thing is that you should not try to unify the terms; instead, accept the differences and richness provided by each domain.</span></span> <span data-ttu-id="9d684-131">Se você tentar se tiver um banco de dados unificado para o aplicativo inteiro, tentativas de um vocabulário unificada serão inadequadas e não tocará direita a qualquer um dos vários especialistas de domínio.</span><span class="sxs-lookup"><span data-stu-id="9d684-131">If you try to have a unified database for the whole application, attempts at a unified vocabulary will be awkward and will not sound right to any of the multiple domain experts.</span></span> <span data-ttu-id="9d684-132">Portanto, BCs (implementados como microservices) ajudará a esclarecer onde você pode usar determinados termos do domínio e onde você precisará dividir o sistema e criar BCs adicionais com domínios diferentes.</span><span class="sxs-lookup"><span data-stu-id="9d684-132">Therefore, BCs (implemented as microservices) will help you to clarify where you can use certain domain terms and where you will need to split the system and create additional BCs with different domains.</span></span>

<span data-ttu-id="9d684-133">Você saberá que você obteve os limites à direita e os tamanhos de cada BC e modelo de domínio se você tem algumas relações fortes entre modelos de domínio e normalmente não faria necessário mesclar as informações de vários modelos de domínio ao executar um aplicativo típico operações.</span><span class="sxs-lookup"><span data-stu-id="9d684-133">You will know that you got the right boundaries and sizes of each BC and domain model if you have few strong relationships between domain models, and you do not usually need to merge information from multiple domain models when performing typical application operations.</span></span>

<span data-ttu-id="9d684-134">Talvez a melhor resposta à pergunta de grande como um modelo de domínio para cada microsserviço deve ser é o seguinte: ele deve ter um BC autônomo, como isolado possível, o que permite que você trabalhe sem precisar alternar constantemente a outros contextos (outros modelos do microsserviço).</span><span class="sxs-lookup"><span data-stu-id="9d684-134">Perhaps the best answer to the question of how big a domain model for each microservice should be is the following: it should have an autonomous BC, as isolated as possible, that enables you to work without having to constantly switch to other contexts (other microservice’s models).</span></span> <span data-ttu-id="9d684-135">Figura 4-10, você pode ver como várias microservices (várias BCs) cada têm seus próprios modelos e como suas entidades podem ser definidas, dependendo dos requisitos específicos para cada um dos domínios identificados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d684-135">In Figure 4-10 you can see how multiple microservices (multiple BCs) each have their own model and how their entities can be defined, depending on the specific requirements for each of the identified domains in your application.</span></span>

![](./media/image10.png)

<span data-ttu-id="9d684-136">**Figura 4-10**.</span><span class="sxs-lookup"><span data-stu-id="9d684-136">**Figure 4-10**.</span></span> <span data-ttu-id="9d684-137">Identificação de entidades e limites de modelo de microsserviço</span><span class="sxs-lookup"><span data-stu-id="9d684-137">Identifying entities and microservice model boundaries</span></span>

<span data-ttu-id="9d684-138">Figura 4-10 ilustra um cenário de exemplo relacionado a um sistema de gerenciamento de conferência on-line.</span><span class="sxs-lookup"><span data-stu-id="9d684-138">Figure 4-10 illustrates a sample scenario related to an online conference management system.</span></span> <span data-ttu-id="9d684-139">Você identificou várias BCs que podem ser implementados como microservices, com base em domínios que especialistas de domínio definidos para você.</span><span class="sxs-lookup"><span data-stu-id="9d684-139">You have identified several BCs that could be implemented as microservices, based on domains that domain experts defined for you.</span></span> <span data-ttu-id="9d684-140">Como você pode ver, há entidades que estão presentes apenas em um modelo de microsserviço único, como pagamentos em microsserviço de pagamento.</span><span class="sxs-lookup"><span data-stu-id="9d684-140">As you can see, there are entities that are present just in a single microservice model, like Payments in the Payment microservice.</span></span> <span data-ttu-id="9d684-141">Esses serão fáceis de implementar.</span><span class="sxs-lookup"><span data-stu-id="9d684-141">Those will be easy to implement.</span></span>

<span data-ttu-id="9d684-142">No entanto, você também pode ter entidades que têm uma forma diferente, mas compartilham a mesma identidade em vários modelos de domínio de microservices a vários.</span><span class="sxs-lookup"><span data-stu-id="9d684-142">However, you might also have entities that have a different shape but share the same identity across the multiple domain models from the multiple microservices.</span></span> <span data-ttu-id="9d684-143">Por exemplo, a entidade de usuário é identificada no microsserviço gerenciamento de conferências.</span><span class="sxs-lookup"><span data-stu-id="9d684-143">For example, the User entity is identified in the Conferences Management microservice.</span></span> <span data-ttu-id="9d684-144">Esse mesmo usuário, com a mesma identidade, é o chamado compradores em microsserviço a ordenação ou a chamada contribuinte no microsserviço o pagamento e até mesmo o um cliente nomeado no microsserviço atendimento ao cliente.</span><span class="sxs-lookup"><span data-stu-id="9d684-144">That same user, with the same identity, is the one named Buyers in the Ordering microservice, or the one named Payer in the Payment microservice, and even the one named Customer in the Customer Service microservice.</span></span> <span data-ttu-id="9d684-145">Isso ocorre porque, dependendo do [idioma onipresente](https://martinfowler.com/bliki/UbiquitousLanguage.html) que está usando o especialista em cada domínio, um usuário pode ter uma perspectiva diferente, mesmo com atributos diferentes.</span><span class="sxs-lookup"><span data-stu-id="9d684-145">This is because, depending on the [ubiquitous language](https://martinfowler.com/bliki/UbiquitousLanguage.html) that each domain expert is using, a user might have a different perspective even with different attributes.</span></span> <span data-ttu-id="9d684-146">A entidade de usuário no modelo de microsserviço denominado conferências Management pode ter mais de seus atributos de dados pessoais.</span><span class="sxs-lookup"><span data-stu-id="9d684-146">The user entity in the microservice model named Conferences Management might have most of its personal data attributes.</span></span> <span data-ttu-id="9d684-147">No entanto, esse mesmo usuário na forma de cliente em que o pagamento de microsserviço ou na forma de cliente de microsserviço atendimento ao cliente talvez não seja necessário a mesma lista de atributos.</span><span class="sxs-lookup"><span data-stu-id="9d684-147">However, that same user in the shape of Payer in the microservice Payment or in the shape of Customer in the microservice Customer Service might not need the same list of attributes.</span></span>

<span data-ttu-id="9d684-148">Uma abordagem semelhante é ilustrada na Figura 4-11.</span><span class="sxs-lookup"><span data-stu-id="9d684-148">A similar approach is illustrated in Figure 4-11.</span></span>

![](./media/image11.png)

<span data-ttu-id="9d684-149">**Figura 4-11**.</span><span class="sxs-lookup"><span data-stu-id="9d684-149">**Figure 4-11**.</span></span> <span data-ttu-id="9d684-150">A decomposição de modelos de dados tradicional em vários modelos de domínio</span><span class="sxs-lookup"><span data-stu-id="9d684-150">Decomposing traditional data models into multiple domain models</span></span>

<span data-ttu-id="9d684-151">Você pode ver como o usuário está presente no modelo de microsserviço de gerenciamento de conferências como entidade de usuário e também está presente no formulário da entidade comprador microsserviço a preços, com detalhes sobre o usuário quando ele é realmente um comprador ou de atributos alternativos.</span><span class="sxs-lookup"><span data-stu-id="9d684-151">You can see how the user is present in the Conferences Management microservice model as the User entity and is also present in the form of the Buyer entity in the Pricing microservice, with alternate attributes or details about the user when it is actually a buyer.</span></span> <span data-ttu-id="9d684-152">Cada microsserviço ou BC talvez não seja necessário todos os dados relacionados a uma entidade de usuário, apenas parte dele, dependendo de resolver o problema ou o contexto.</span><span class="sxs-lookup"><span data-stu-id="9d684-152">Each microservice or BC might not need all the data related to a User entity, just part of it, depending on the problem to solve or the context.</span></span> <span data-ttu-id="9d684-153">Por exemplo, no modelo de preços de microsserviço, não é necessário o endereço ou a ID do usuário, apenas o ID (como identidade) e o Status, que terá um impacto em descontos quando preços estações por comprador.</span><span class="sxs-lookup"><span data-stu-id="9d684-153">For instance, in the Pricing microservice model, you do not need the address or the ID of the user, just ID (as identity) and Status, which will have an impact on discounts when pricing the seats per buyer.</span></span>

<span data-ttu-id="9d684-154">A entidade de estação tem o mesmo nome mas diferentes atributos em cada modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9d684-154">The Seat entity has the same name but different attributes in each domain model.</span></span> <span data-ttu-id="9d684-155">No entanto, os compartilhamentos de estação identidade com base na ID da mesma, como acontece com o comprador e o usuário.</span><span class="sxs-lookup"><span data-stu-id="9d684-155">However, Seat shares identity based on the same ID, as happens with User and Buyer.</span></span>

<span data-ttu-id="9d684-156">Basicamente, há um conceito compartilhado de um usuário que existe em vários serviços (domínios), que compartilham a identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="9d684-156">Basically, there is a shared concept of a user that exists in multiple services (domains), which all share the identity of that user.</span></span> <span data-ttu-id="9d684-157">Mas, em cada modelo de domínio pode ser adicionais ou diferentes detalhes sobre a entidade de usuário.</span><span class="sxs-lookup"><span data-stu-id="9d684-157">But in each domain model there might be additional or different details about the user entity.</span></span> <span data-ttu-id="9d684-158">Portanto, precisa ser uma maneira de mapear uma entidade de usuário de um domínio (microsserviço) para outro.</span><span class="sxs-lookup"><span data-stu-id="9d684-158">Therefore, there needs to be a way to map a user entity from one domain (microservice) to another.</span></span>

<span data-ttu-id="9d684-159">Há vários benefícios para não compartilhar a mesma entidade de usuário com o mesmo número de atributos entre domínios.</span><span class="sxs-lookup"><span data-stu-id="9d684-159">There are several benefits to not sharing the same user entity with the same number of attributes across domains.</span></span> <span data-ttu-id="9d684-160">Um benefício é reduzir a duplicação, para que os modelos de microsserviço não tem todos os dados que não seja necessário.</span><span class="sxs-lookup"><span data-stu-id="9d684-160">One benefit is to reduce duplication, so that microservice models do not have any data that they do not need.</span></span> <span data-ttu-id="9d684-161">Outro benefício está tendo um microsserviço mestre que possui um determinado tipo de dados por entidade para que as atualizações e consultas para esse tipo de dados são controladas por apenas por esse microsserviço.</span><span class="sxs-lookup"><span data-stu-id="9d684-161">Another benefit is having a master microservice that owns a certain type of data per entity so that updates and queries for that type of data are driven only by that microservice.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9d684-162">[Anterior] (distributed-data-management.md) [Avançar] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="9d684-162">[Previous] (distributed-data-management.md) [Next] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)</span></span>