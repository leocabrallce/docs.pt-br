---
title: Habilitando e desabilitando o IPv6
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
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dee5dd53a88bdd108b84d05cfb75799630836033
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="bcbd1-102">Habilitando e desabilitando o IPv6</span><span class="sxs-lookup"><span data-stu-id="bcbd1-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="bcbd1-103">Para usar o protocolo IPv6, verifique se você está executando uma versão do sistema operacional que dá suporte ao IPv6 e se o sistema operacional e as classes de rede estão configuradas corretamente.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="bcbd1-104">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="bcbd1-104">Configuration Steps</span></span>  
 <span data-ttu-id="bcbd1-105">A tabela a seguir lista várias configurações</span><span class="sxs-lookup"><span data-stu-id="bcbd1-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="bcbd1-106">Sistema operacional habilitado para IPv6?</span><span class="sxs-lookup"><span data-stu-id="bcbd1-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="bcbd1-107">Classes de rede habilitadas para IPv6?</span><span class="sxs-lookup"><span data-stu-id="bcbd1-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="bcbd1-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcbd1-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="bcbd1-109">Não</span><span class="sxs-lookup"><span data-stu-id="bcbd1-109">No</span></span>|<span data-ttu-id="bcbd1-110">Não</span><span class="sxs-lookup"><span data-stu-id="bcbd1-110">No</span></span>|<span data-ttu-id="bcbd1-111">Pode analisar endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="bcbd1-112">Não</span><span class="sxs-lookup"><span data-stu-id="bcbd1-112">No</span></span>|<span data-ttu-id="bcbd1-113">Sim</span><span class="sxs-lookup"><span data-stu-id="bcbd1-113">Yes</span></span>|<span data-ttu-id="bcbd1-114">Pode analisar endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="bcbd1-115">Sim</span><span class="sxs-lookup"><span data-stu-id="bcbd1-115">Yes</span></span>|<span data-ttu-id="bcbd1-116">Não</span><span class="sxs-lookup"><span data-stu-id="bcbd1-116">No</span></span>|<span data-ttu-id="bcbd1-117">Pode analisar endereços IPv6 e resolver endereços IPv6 usando métodos de resolução de nomes não marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="bcbd1-118">Sim</span><span class="sxs-lookup"><span data-stu-id="bcbd1-118">Yes</span></span>|<span data-ttu-id="bcbd1-119">Sim</span><span class="sxs-lookup"><span data-stu-id="bcbd1-119">Yes</span></span>|<span data-ttu-id="bcbd1-120">Pode analisar e resolver endereços IPv6 usando todos os métodos, incluindo aqueles marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="bcbd1-121">Lembre-se de que, para habilitar o suporte ao IPv6 em todas as classes no namespace System.Net, é necessário modificar o arquivo de configuração do computador ou o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="bcbd1-122">O arquivo de configuração de um aplicativo tem precedência sobre o arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="bcbd1-123">Para obter um exemplo de como modificar o arquivo de configuração do computador, *machine.config*, para habilitar o suporte ao IPv6, consulte [Como modificar o arquivo de configuração do computador para habilitar o suporte ao IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="bcbd1-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="bcbd1-124">Além disso, verifique se o suporte ao IPv6 está habilitado no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="bcbd1-125">O .NET Framework tem uma opção de configuração definida em um arquivo de configuração da seguinte maneira</span><span class="sxs-lookup"><span data-stu-id="bcbd1-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 <span data-ttu-id="bcbd1-126">Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=fullName> retornam endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=fullName> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="bcbd1-127">Para o .NET Framework versão 2.0 e posterior, se o Windows der suporte ao IPv6, os membros da classe <xref:System.Net.Dns?displayProperty=fullName>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName>), retornarão endereços IPv6 com uma limitação.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=fullName> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="bcbd1-128">Os membros obsoletos do DNS <xref:System.Net.Dns?displayProperty=fullName> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName>) lerão e reconhecerão o valor no arquivo de configuração para a configuração ipv6 enabled.</span><span class="sxs-lookup"><span data-stu-id="bcbd1-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=fullName> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbd1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcbd1-129">See Also</span></span>  
 <span data-ttu-id="bcbd1-130">[Protocolo IP versão 6](../../../docs/framework/network-programming/internet-protocol-version-6.md) </span><span class="sxs-lookup"><span data-stu-id="bcbd1-130">[Internet Protocol Version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md) </span></span>  
 <span data-ttu-id="bcbd1-131">[Soquetes](../../../docs/framework/network-programming/sockets.md) </span><span class="sxs-lookup"><span data-stu-id="bcbd1-131">[Sockets](../../../docs/framework/network-programming/sockets.md) </span></span>  
 <span data-ttu-id="bcbd1-132">[Esquema de configurações de rede](../../../docs/framework/configure-apps/file-schema/network/index.md) </span><span class="sxs-lookup"><span data-stu-id="bcbd1-132">[Network Settings Schema](../../../docs/framework/configure-apps/file-schema/network/index.md) </span></span>  
 [<span data-ttu-id="bcbd1-133">\<Elemento ipv6> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="bcbd1-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
