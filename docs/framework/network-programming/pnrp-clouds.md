---
title: Nuvens PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a>Nuvens PNRP
A "nuvem" PNRP representa um conjunto de nós que podem se comunicar entre si através da rede. O termo "nuvem" é sinônimo de "malha ponto a ponto" e "grafo ponto a ponto".  
  
 A comunicação entre nós nunca deve cruzar de uma nuvem para outra. Uma instância <xref:System.Net.PeerToPeer.Cloud> é identificada exclusivamente pelo seu nome, que diferencia maiúsculas de minúsculas. Um único par ou nó pode estar conectado a mais de uma nuvem.  
  
 As nuvens estão muito diretamente ligadas a adaptadores de rede.  Em um computador multihomed com duas placas de rede conectadas a diferentes sub-redes, três nuvens serão retornadas: uma para cada um dos endereços locais de link por adaptador e uma única nuvem de escopo global.  
  
 O PNRP usa três "escopos" de nuvem, nos quais um escopo é um agrupamento de computadores capazes de localizar uns aos outros:  
  
-   A nuvem global corresponde ao escopo de endereço IPv6 global e endereços globais e representa todos os computadores em toda a Internet IPv6. Há apenas uma única nuvem global.  
  
-   A nuvem de link local corresponde ao escopo de endereço IPv6 link local e endereços de link local. Uma nuvem de link local é para um link específico, que normalmente é o mesmo que a sub-rede conectada localmente. Pode haver várias nuvens de link local.  
  
 Uma terceira nuvem, a nuvem específica do site, corresponde ao escopo de endereço IPv6 do site e a endereços de site local. Essa nuvem foi preterida, embora ela ainda tenha suporte em PNRP.  
  
## <a name="clouds"></a>Nuvens  
 Nuvens PNRP são representados por instâncias da classe <xref:System.Net.PeerToPeer.Cloud>. Grupos de nuvens usadas por um par são representados por instâncias da classe enumerável <xref:System.Net.PeerToPeer.CloudCollection>. Coleções de nuvens PNRP conhecidas para o par atual podem ser obtidas chamando o método estático <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A>.  
  
 Nuvens individuais têm nomes exclusivos, representados como uma cadeia de caracteres Unicode de 256 caracteres. Esses nomes, junto com o escopo mencionado acima, são usados para construir instâncias exclusivas de classe Cloud. Essas instâncias podem ser serializadas e reconstruídas para uso persistente.  
  
 Depois que uma instância de nuvem é criada ou obtida, nomes de par podem ser registrados com ele para criar uma malha de pares conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.PeerToPeer.Cloud>  
 [Protocolo PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
