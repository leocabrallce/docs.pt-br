---
title: Hospedando na Web um aplicativo em fila
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 38edfcb1363e538295e1fb1a8b8fe0c5b2d34691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="web-hosting-a-queued-application"></a><span data-ttu-id="e7bcc-102">Hospedando na Web um aplicativo em fila</span><span class="sxs-lookup"><span data-stu-id="e7bcc-102">Web Hosting a Queued Application</span></span>
<span data-ttu-id="e7bcc-103">O serviço de ativação de processos do Windows (WAS) gerencia a ativação e a vida útil dos processos de trabalho que contêm aplicativos que hospedam [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-103">The Windows Process Activation Service (WAS) manages the activation and lifetime of the worker processes that contain applications that host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="e7bcc-104">O modelo de processo WAS generaliza o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] modelo de processo para o servidor HTTP, removendo a dependência no HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-104">The WAS process model generalizes the [!INCLUDE[iis601](../../../../includes/iis601-md.md)] process model for the HTTP server by removing the dependency on HTTP.</span></span> <span data-ttu-id="e7bcc-105">Isso permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services para usar HTTP e protocolos não HTTP, como NET. MSMQ e FormatName, em um ambiente de hospedagem que oferece suporte à ativação baseada em mensagem e oferece a capacidade de hospedar um grande número de aplicativos em um determinado computador.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-105">This allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to use both HTTP and non-HTTP protocols, such as net.msmq and msmq.formatname, in a hosting environment that supports message-based activation and offers the ability to host a large number of applications on a given computer.</span></span>  
  
 <span data-ttu-id="e7bcc-106">FOI inclui um serviço de ativação de enfileiramento de mensagens (MSMQ) que ativa um aplicativo em fila quando uma ou mais mensagens são colocadas em uma das filas usadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-106">WAS includes a Message Queuing (MSMQ) activation service that activates a queued application when one or more messages are placed in one of the queues used by the application.</span></span> <span data-ttu-id="e7bcc-107">O serviço de ativação MSMQ é um serviço do NT é iniciado automaticamente por padrão.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-107">The MSMQ activation service is an NT service that is automatically started by default.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e7bcc-108">WAS e seus benefícios, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).</span><span class="sxs-lookup"><span data-stu-id="e7bcc-108"> WAS and its benefits, see [Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e7bcc-109">MSMQ, consulte [visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)</span><span class="sxs-lookup"><span data-stu-id="e7bcc-109"> MSMQ, see [Queues Overview](../../../../docs/framework/wcf/feature-details/queues-overview.md)</span></span>  
  
## <a name="queue-addressing-in-was"></a><span data-ttu-id="e7bcc-110">Fila de endereçamento no WAS</span><span class="sxs-lookup"><span data-stu-id="e7bcc-110">Queue Addressing in WAS</span></span>  
 <span data-ttu-id="e7bcc-111">FOI aplicativos têm endereços de identificador de recurso uniforme (URI).</span><span class="sxs-lookup"><span data-stu-id="e7bcc-111">WAS applications have Uniform Resource Identifier (URI) addresses.</span></span> <span data-ttu-id="e7bcc-112">Endereços de aplicativo têm duas partes: um prefixo URI base e um endereço específico do aplicativo, relativo (caminho).</span><span class="sxs-lookup"><span data-stu-id="e7bcc-112">Application addresses have two parts: a base URI prefix and an application-specific, relative address (path).</span></span> <span data-ttu-id="e7bcc-113">Essas duas partes fornecem o endereço externo para um aplicativo quando unidas.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-113">These two parts provide the external address for an application when joined together.</span></span> <span data-ttu-id="e7bcc-114">O prefixo URI base é construído com a associação do site e é usado para todos os aplicativos sob o site, por exemplo, "net.msmq://localhost", "msmq.formatname://localhost" ou "net.tcp://localhost".</span><span class="sxs-lookup"><span data-stu-id="e7bcc-114">The base URI prefix is constructed from the site binding and is used for all the applications under the site, for example, "net.msmq://localhost", "msmq.formatname://localhost", or "net.tcp://localhost".</span></span> <span data-ttu-id="e7bcc-115">Endereços de aplicativo, em seguida, são construídos colocando os fragmentos de caminho específico do aplicativo (como "/ applicationOne") e anexando-los para o URI de base do prefixo para chegar a todo o aplicativo URI, por exemplo, "net.msmq://localhost/applicationOne".</span><span class="sxs-lookup"><span data-stu-id="e7bcc-115">Application addresses are then constructed by taking application-specific path fragments (such as "/applicationOne") and appending them to the base URI prefix to arrive at the full application URI, for example, "net.msmq://localhost/applicationOne".</span></span>  
  
 <span data-ttu-id="e7bcc-116">O serviço de ativação MSMQ usa o URI do aplicativo para corresponder a fila que o serviço de ativação MSMQ deve monitorar para mensagens.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-116">The MSMQ activation service uses the application URI to match the queue that the MSMQ activation service must monitor for messages.</span></span> <span data-ttu-id="e7bcc-117">Quando o serviço de ativação MSMQ é iniciado, ele enumerará todas as filas públicas e particulares no computador em que ele está configurado para receber e monitorá-los para mensagens.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-117">When the MSMQ activation service starts, it enumerates all public and private queues on the computer it is configured to receive from and monitors them for messages.</span></span> <span data-ttu-id="e7bcc-118">A cada 10 minutos, o serviço de ativação MSMQ atualiza a lista de filas para monitorar.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-118">Every 10 minutes, the MSMQ activation service refreshes the list of queues to monitor.</span></span> <span data-ttu-id="e7bcc-119">Quando uma mensagem é encontrada em uma fila, o serviço de ativação corresponde ao nome de fila para o URI do aplicativo mais longo correspondente para a associação de NET. MSMQ e ativa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-119">When a message is found in a queue, the activation service matches the queue name to the longest matching application URI for the net.msmq binding and activates the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7bcc-120">O aplicativo que está sendo ativado deve corresponder (correspondência mais longa), o prefixo do nome da fila.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-120">The application being activated must match (longest match) the prefix of the queue name.</span></span>  
  
 <span data-ttu-id="e7bcc-121">Por exemplo, um nome de fila é: msmqWebHost/orderProcessing/service.svc.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-121">For example, a queue name is: msmqWebHost/orderProcessing/service.svc.</span></span> <span data-ttu-id="e7bcc-122">Se o aplicativo 1 tem um /msmqWebHost/orderProcessing do diretório virtual com um SVC sob ele, e 2 do aplicativo tiver /msmqWebHost um diretório virtual com um orderProcessing.svc sob ele, 1 de aplicativo está ativado.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-122">If Application 1 has a virtual directory /msmqWebHost/orderProcessing with a service.svc under it, and Application 2 has a virtual directory /msmqWebHost with an orderProcessing.svc under it, Application 1 is activated.</span></span> <span data-ttu-id="e7bcc-123">Se o aplicativo 1 é excluído, 2 de aplicativo está ativado.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-123">If Application 1 is deleted, Application 2 is activated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7bcc-124">Quando uma fila é criada, todas as mensagens enviadas a ele não ativar um aplicativo até que o serviço de ativação MSMQ atualiza a lista de fila, que é, no máximo, 10 minutos da hora em que a fila foi criada.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-124">When a queue is created, any messages sent to it do not activate an application until the MSMQ activation service refreshes the queue list, which is, at most, 10 minutes from the time the queue was created.</span></span> <span data-ttu-id="e7bcc-125">Reiniciar o serviço de ativação atualiza a lista de filas.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-125">Restarting the activation service refreshes the queue list as well.</span></span>  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a><span data-ttu-id="e7bcc-126">O efeito de filas públicas e privadas em tratar</span><span class="sxs-lookup"><span data-stu-id="e7bcc-126">The Effect of Private and Public Queues on Addressing</span></span>  
 <span data-ttu-id="e7bcc-127">O serviço de ativação MSMQ não faz distinção entre o monitoramento de fila pública e privada.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-127">The MSMQ activation service does not distinguish between private and public queue monitoring.</span></span> <span data-ttu-id="e7bcc-128">Como tal, você não pode ter filas públicas e privadas com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-128">As such, you cannot have public and private queues with the same name.</span></span> <span data-ttu-id="e7bcc-129">Se você fizer isso, um aplicativo Web hospedado pode obter ativado lendo de qualquer uma das filas.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-129">If you do, a Web-hosted application may get activated reading from either of the queues.</span></span>  
  
### <a name="queue-configuration-for-activation"></a><span data-ttu-id="e7bcc-130">Configuração de fila para ativação</span><span class="sxs-lookup"><span data-stu-id="e7bcc-130">Queue Configuration for Activation</span></span>  
 <span data-ttu-id="e7bcc-131">O serviço de ativação MSMQ é executado como serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-131">The MSMQ activation service runs as NETWORK SERVICE.</span></span> <span data-ttu-id="e7bcc-132">É o serviço que monitora filas para ativar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-132">It is the service that monitors queues to activate applications.</span></span> <span data-ttu-id="e7bcc-133">Para ele ativar aplicativos da fila, a fila deve fornecer acesso de serviço de rede ao inspecionar mensagens na sua lista de controle de acesso (ACL).</span><span class="sxs-lookup"><span data-stu-id="e7bcc-133">For it to activate applications from the queue, the queue must provide for NETWORK SERVICE access to peek for messages in its access control list (ACL).</span></span>  
  
### <a name="poison-messaging"></a><span data-ttu-id="e7bcc-134">Suspeitas de mensagens</span><span class="sxs-lookup"><span data-stu-id="e7bcc-134">Poison Messaging</span></span>  
 <span data-ttu-id="e7bcc-135">Mensagem suspeita tratamento em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é tratado pelo canal, que não só detecta que uma mensagem é adulterada mas seleciona uma disposição com base na configuração de usuário.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-135">Poison message handling in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is handled by the channel, which not only detects that a message is poisoned but selects a disposition based on user configuration.</span></span> <span data-ttu-id="e7bcc-136">Como resultado, há uma única mensagem na fila.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-136">As a result, there is a single message in the queue.</span></span> <span data-ttu-id="e7bcc-137">O aplicativo Web hospedado anula sucessivas vezes e a mensagem será movida para uma fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-137">The Web-hosted application aborts successive times and the message is moved to a retry queue.</span></span> <span data-ttu-id="e7bcc-138">Em um momento determinado, o atraso de ciclo de repetição, a mensagem é movida da fila de repetição para a fila principal para tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-138">At a point dictated by the retry cycle delay, the message is moved from the retry queue to the main queue to try again.</span></span> <span data-ttu-id="e7bcc-139">Mas isso exige que o canal em fila esteja ativo.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-139">But this requires the queued channel to be active.</span></span> <span data-ttu-id="e7bcc-140">Se o aplicativo é reciclado WAS, em seguida, a mensagem permanece na fila de repetição até que outra mensagem chega na fila principal para ativar o aplicativo na fila.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-140">If the application is recycled by WAS, then the message remains in the retry queue until another message arrives in the main queue to activate the queued application.</span></span> <span data-ttu-id="e7bcc-141">Nesse caso, a solução alternativa é retornar a mensagem manualmente da fila de repetição para a fila principal para reativar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-141">The workaround in this case is to move the message manually from the retry queue back to the main queue to reactivate the application.</span></span>  
  
### <a name="subqueue-and-system-queue-caveat"></a><span data-ttu-id="e7bcc-142">Subfila de mensagens e a limitação de fila do sistema</span><span class="sxs-lookup"><span data-stu-id="e7bcc-142">Subqueue and System Queue Caveat</span></span>  
 <span data-ttu-id="e7bcc-143">Um aplicativo hospedado WAS não pode ser ativado com base em mensagens em uma fila do sistema, como a fila de mensagens mortas de todo o sistema ou filas sub, como filas sub suspeitas.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-143">A WAS-hosted application cannot be activated based on messages in a system queue, such as the system-wide dead-letter queue, or sub-queues, such as poison sub-queues.</span></span> <span data-ttu-id="e7bcc-144">Essa é uma limitação para esta versão do produto.</span><span class="sxs-lookup"><span data-stu-id="e7bcc-144">This is a limitation for this version of the product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bcc-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7bcc-145">See Also</span></span>  
 [<span data-ttu-id="e7bcc-146">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="e7bcc-146">Poison Message Handling</span></span>](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [<span data-ttu-id="e7bcc-147">Pontos de extremidade de serviço e endereçamento de fila</span><span class="sxs-lookup"><span data-stu-id="e7bcc-147">Service Endpoints and Queue Addressing</span></span>](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)