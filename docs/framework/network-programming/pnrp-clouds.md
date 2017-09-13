---
title: Nuvens PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: 4
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 17770f43d04916ae55b1b62010c8b43e0e4c95e3
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="pnrp-clouds"></a><span data-ttu-id="875df-102">Nuvens PNRP</span><span class="sxs-lookup"><span data-stu-id="875df-102">PNRP Clouds</span></span>
<span data-ttu-id="875df-103">A "nuvem" PNRP representa um conjunto de nós que podem se comunicar entre si através da rede.</span><span class="sxs-lookup"><span data-stu-id="875df-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="875df-104">O termo "nuvem" é sinônimo de "malha ponto a ponto" e "grafo ponto a ponto".</span><span class="sxs-lookup"><span data-stu-id="875df-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="875df-105">A comunicação entre nós nunca deve cruzar de uma nuvem para outra.</span><span class="sxs-lookup"><span data-stu-id="875df-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="875df-106">Uma instância <xref:System.Net.PeerToPeer.Cloud> é identificada exclusivamente pelo seu nome, que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="875df-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="875df-107">Um único par ou nó pode estar conectado a mais de uma nuvem.</span><span class="sxs-lookup"><span data-stu-id="875df-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="875df-108">As nuvens estão muito diretamente ligadas a adaptadores de rede.</span><span class="sxs-lookup"><span data-stu-id="875df-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="875df-109">Em um computador multihomed com duas placas de rede conectadas a diferentes sub-redes, três nuvens serão retornadas: uma para cada um dos endereços locais de link por adaptador e uma única nuvem de escopo global.</span><span class="sxs-lookup"><span data-stu-id="875df-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="875df-110">O PNRP usa três "escopos" de nuvem, nos quais um escopo é um agrupamento de computadores capazes de localizar uns aos outros:</span><span class="sxs-lookup"><span data-stu-id="875df-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="875df-111">A nuvem global corresponde ao escopo de endereço IPv6 global e endereços globais e representa todos os computadores em toda a Internet IPv6.</span><span class="sxs-lookup"><span data-stu-id="875df-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="875df-112">Há apenas uma única nuvem global.</span><span class="sxs-lookup"><span data-stu-id="875df-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="875df-113">A nuvem de link local corresponde ao escopo de endereço IPv6 link local e endereços de link local.</span><span class="sxs-lookup"><span data-stu-id="875df-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="875df-114">Uma nuvem de link local é para um link específico, que normalmente é o mesmo que a sub-rede conectada localmente.</span><span class="sxs-lookup"><span data-stu-id="875df-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="875df-115">Pode haver várias nuvens de link local.</span><span class="sxs-lookup"><span data-stu-id="875df-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="875df-116">Uma terceira nuvem, a nuvem específica do site, corresponde ao escopo de endereço IPv6 do site e a endereços de site local.</span><span class="sxs-lookup"><span data-stu-id="875df-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="875df-117">Essa nuvem foi preterida, embora ela ainda tenha suporte em PNRP.</span><span class="sxs-lookup"><span data-stu-id="875df-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="875df-118">Nuvens</span><span class="sxs-lookup"><span data-stu-id="875df-118">Clouds</span></span>  
 <span data-ttu-id="875df-119">Nuvens PNRP são representados por instâncias da classe <xref:System.Net.PeerToPeer.Cloud>.</span><span class="sxs-lookup"><span data-stu-id="875df-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="875df-120">Grupos de nuvens usadas por um par são representados por instâncias da classe enumerável <xref:System.Net.PeerToPeer.CloudCollection>.</span><span class="sxs-lookup"><span data-stu-id="875df-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="875df-121">Coleções de nuvens PNRP conhecidas para o par atual podem ser obtidas chamando o método estático <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A>.</span><span class="sxs-lookup"><span data-stu-id="875df-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="875df-122">Nuvens individuais têm nomes exclusivos, representados como uma cadeia de caracteres Unicode de 256 caracteres.</span><span class="sxs-lookup"><span data-stu-id="875df-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="875df-123">Esses nomes, junto com o escopo mencionado acima, são usados para construir instâncias exclusivas de classe Cloud.</span><span class="sxs-lookup"><span data-stu-id="875df-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="875df-124">Essas instâncias podem ser serializadas e reconstruídas para uso persistente.</span><span class="sxs-lookup"><span data-stu-id="875df-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="875df-125">Depois que uma instância de nuvem é criada ou obtida, nomes de par podem ser registrados com ele para criar uma malha de pares conhecidos.</span><span class="sxs-lookup"><span data-stu-id="875df-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875df-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="875df-126">See Also</span></span>  
 <span data-ttu-id="875df-127"><xref:System.Net.PeerToPeer.Cloud></span><span class="sxs-lookup"><span data-stu-id="875df-127"><xref:System.Net.PeerToPeer.Cloud></span></span>   
 [<span data-ttu-id="875df-128">Protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="875df-128">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
