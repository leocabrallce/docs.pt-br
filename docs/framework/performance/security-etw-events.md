---
title: "Eventos ETW de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="security-etw-events"></a><span data-ttu-id="2b64f-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="2b64f-102">Security ETW Events</span></span>
<span data-ttu-id="2b64f-103"><a name="top"></a> Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2b64f-103"><a name="top"></a> Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="2b64f-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="2b64f-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="2b64f-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="2b64f-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="2b64f-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="2b64f-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="2b64f-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="2b64f-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="2b64f-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="2b64f-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="2b64f-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="2b64f-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2b64f-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-110">Keyword for raising the event</span></span>|<span data-ttu-id="2b64f-111">Nível</span><span class="sxs-lookup"><span data-stu-id="2b64f-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2b64f-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="2b64f-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="2b64f-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="2b64f-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="2b64f-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="2b64f-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2b64f-115">Evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-115">Event</span></span>|<span data-ttu-id="2b64f-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-116">Event ID</span></span>|<span data-ttu-id="2b64f-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="2b64f-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="2b64f-118">181</span><span class="sxs-lookup"><span data-stu-id="2b64f-118">181</span></span>|<span data-ttu-id="2b64f-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="2b64f-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="2b64f-120">182</span><span class="sxs-lookup"><span data-stu-id="2b64f-120">182</span></span>|<span data-ttu-id="2b64f-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="2b64f-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="2b64f-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="2b64f-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2b64f-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="2b64f-123">Field name</span></span>|<span data-ttu-id="2b64f-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="2b64f-124">Data type</span></span>|<span data-ttu-id="2b64f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b64f-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2b64f-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="2b64f-126">VerificationFlags</span></span>|<span data-ttu-id="2b64f-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2b64f-127">win:UInt32</span></span>|<span data-ttu-id="2b64f-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="2b64f-128">The verification flags.</span></span>|  
|<span data-ttu-id="2b64f-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="2b64f-129">ErrorCode</span></span>|<span data-ttu-id="2b64f-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2b64f-130">win:UInt32</span></span>|<span data-ttu-id="2b64f-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="2b64f-131">The HResult error code.</span></span>|  
|<span data-ttu-id="2b64f-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="2b64f-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="2b64f-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2b64f-133">win:UnicodeString</span></span>|<span data-ttu-id="2b64f-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="2b64f-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="2b64f-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2b64f-135">ClrInstanceID</span></span>|<span data-ttu-id="2b64f-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2b64f-136">win:UInt16</span></span>|<span data-ttu-id="2b64f-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2b64f-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2b64f-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="2b64f-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="2b64f-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="2b64f-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="2b64f-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="2b64f-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2b64f-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-141">Keyword for raising the event</span></span>|<span data-ttu-id="2b64f-142">Nível</span><span class="sxs-lookup"><span data-stu-id="2b64f-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2b64f-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="2b64f-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="2b64f-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="2b64f-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="2b64f-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="2b64f-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2b64f-146">Evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-146">Event</span></span>|<span data-ttu-id="2b64f-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="2b64f-147">Event ID</span></span>|<span data-ttu-id="2b64f-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="2b64f-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="2b64f-149">183</span><span class="sxs-lookup"><span data-stu-id="2b64f-149">183</span></span>|<span data-ttu-id="2b64f-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2b64f-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="2b64f-151">184</span><span class="sxs-lookup"><span data-stu-id="2b64f-151">184</span></span>|<span data-ttu-id="2b64f-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2b64f-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="2b64f-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="2b64f-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2b64f-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="2b64f-154">Field name</span></span>|<span data-ttu-id="2b64f-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="2b64f-155">Data type</span></span>|<span data-ttu-id="2b64f-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b64f-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2b64f-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="2b64f-157">VerificationFlags</span></span>|<span data-ttu-id="2b64f-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2b64f-158">win:UInt32</span></span>|<span data-ttu-id="2b64f-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="2b64f-159">The verification flags.</span></span>|  
|<span data-ttu-id="2b64f-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="2b64f-160">ErrorCode</span></span>|<span data-ttu-id="2b64f-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2b64f-161">win:UInt32</span></span>|<span data-ttu-id="2b64f-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="2b64f-162">The HResult error code.</span></span>|  
|<span data-ttu-id="2b64f-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="2b64f-163">ModulePath</span></span>|<span data-ttu-id="2b64f-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2b64f-164">win:UnicodeString</span></span>|<span data-ttu-id="2b64f-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="2b64f-165">The module path.</span></span>|  
|<span data-ttu-id="2b64f-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2b64f-166">ClrInstanceID</span></span>|<span data-ttu-id="2b64f-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2b64f-167">win:UInt16</span></span>|<span data-ttu-id="2b64f-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2b64f-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b64f-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b64f-169">See Also</span></span>  
 [<span data-ttu-id="2b64f-170">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="2b64f-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
