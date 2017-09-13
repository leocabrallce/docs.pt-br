---
title: "Criação de perfil do tempo de execução"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9589e838eacd758d43ac9ceb1442d217e6406a03
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="runtime-profiling"></a><span data-ttu-id="eadaf-102">Criação de perfil do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="eadaf-102">Runtime Profiling</span></span>
<span data-ttu-id="eadaf-103">Criação de perfil é um método de coleta de dados de desempenho em qualquer cenário de desenvolvimento ou de implantação.</span><span class="sxs-lookup"><span data-stu-id="eadaf-103">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="eadaf-104">Esta seção é para desenvolvedores e administradores de sistema que desejam coletar informações sobre o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eadaf-104">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="eadaf-105">Acompanhamento de desempenho usando o Monitor de Desempenho (Perfmon.exe)</span><span class="sxs-lookup"><span data-stu-id="eadaf-105">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  
 <span data-ttu-id="eadaf-106">O Monitor de Desempenho é a ferramenta mais fácil de usar para criar o perfil de seu aplicativo [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eadaf-106">The Performance Monitor is the easiest tool to use to profile your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="eadaf-107">O Monitor de Desempenho representa graficamente os dados encontrados nos contadores de desempenho do .NET Framework que são instalados com o Common Language Runtime e o [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eadaf-107">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="eadaf-108">Esses contadores podem ser usados para monitorar tudo, desde o gerenciamento de memória até o desempenho de compilador JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="eadaf-108">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="eadaf-109">Eles informam sobre os recursos que seu aplicativo usa, o que é uma medida indireta do desempenho desse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eadaf-109">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="eadaf-110">Use esses contadores para entender como o aplicativo funciona internamente.</span><span class="sxs-lookup"><span data-stu-id="eadaf-110">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="eadaf-111">Para executar Perfmon.exe no Windows Vista e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="eadaf-111">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1.  <span data-ttu-id="eadaf-112">No prompt de comando, digite **perfmon**.</span><span class="sxs-lookup"><span data-stu-id="eadaf-112">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="eadaf-113">O console **Monitor de Desempenho** é exibido.</span><span class="sxs-lookup"><span data-stu-id="eadaf-113">The **Performance Monitor** console appears.</span></span>  
  
2.  <span data-ttu-id="eadaf-114">Na pasta **Ferramentas de Monitoramento**, clique em **Monitor de Desempenho**.</span><span class="sxs-lookup"><span data-stu-id="eadaf-114">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3.  <span data-ttu-id="eadaf-115">Na barra de ferramentas do Monitor de Desempenho, clique no ícone **Adicionar** (sinal de adição) se ele estiver presente.</span><span class="sxs-lookup"><span data-stu-id="eadaf-115">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="eadaf-116">Se não estiver presente, clique com o botão direito do mouse na janela do monitor e selecione a opção **Adicionar Contadores**.</span><span class="sxs-lookup"><span data-stu-id="eadaf-116">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="eadaf-117">Isso abre a caixa de diálogo **Adicionar Contadores**.</span><span class="sxs-lookup"><span data-stu-id="eadaf-117">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="eadaf-118">A caixa de listagem **Contadores disponíveis** exibe os objetos de desempenho disponíveis.</span><span class="sxs-lookup"><span data-stu-id="eadaf-118">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="eadaf-119">Há um número de objetos predefinidos para aplicativos do .NET Framework, incluindo aqueles para gerenciamento de memória (**Memória do .NET CLR**), interoperabilidade (**Interoperabilidade do .NET CLR**), tratamento de exceção (**Exceções do .NET CLR**) e multithreading (**.NET CLR LocksAndThreads**).</span><span class="sxs-lookup"><span data-stu-id="eadaf-119">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="eadaf-120">Cada objeto de desempenho inclui uma série de contadores de desempenho individuais.</span><span class="sxs-lookup"><span data-stu-id="eadaf-120">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="eadaf-121">Para obter uma lista de contadores de desempenho disponíveis no Monitor de Desempenho, consulte [Contadores de desempenho](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="eadaf-121">For a list of the performance counters available in Performance Monitor, see [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
4.  <span data-ttu-id="eadaf-122">Selecione a caixa de seleção ao lado do nome de um objeto de desempenho para exibir a lista de contadores de desempenho individuais aos quais ele dá suporte.</span><span class="sxs-lookup"><span data-stu-id="eadaf-122">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5.  <span data-ttu-id="eadaf-123">Clique no contador de desempenho que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="eadaf-123">Click the performance counter you want to view.</span></span>  
  
6.  <span data-ttu-id="eadaf-124">Na caixa de listagem **Instâncias do objeto selecionado**, clique em **\<Todas as instâncias>** para especificar que você deseja monitorar o contador de desempenho para o Common Language Runtime globalmente (ou seja, em todo o sistema).</span><span class="sxs-lookup"><span data-stu-id="eadaf-124">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="eadaf-125">-ou-</span><span class="sxs-lookup"><span data-stu-id="eadaf-125">-or-</span></span>  
  
     <span data-ttu-id="eadaf-126">Na caixa de listagem **Instâncias do objeto selecionado**, clique em um nome do aplicativo para monitorar o contador de desempenho para esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eadaf-126">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="eadaf-127">Para diferenciar as várias versões do tempo de execução ou para desfazer a ambiguidade entre vários aplicativos com o mesmo nome, você também deve modificar uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="eadaf-127">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="eadaf-128">Para obter mais informações, consulte [Contadores de desempenho e aplicativos lado a lado em processo](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span><span class="sxs-lookup"><span data-stu-id="eadaf-128">For more information, see [Performance Counters and In-Process Side-By-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eadaf-129">Quando novos contadores de desempenho são instalados enquanto o console de desempenho está em execução, pare e reinicie o console de desempenho para tornar os novos contadores visíveis.</span><span class="sxs-lookup"><span data-stu-id="eadaf-129">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="eadaf-130">Se você deseja criar o perfil de um assembly que existe em uma zona ou em um compartilhamento remoto, verifique se o assembly remoto tem confiança total no computador que executa os contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="eadaf-130">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="eadaf-131">Se o assembly não tiverem confiança suficiente, os contadores de desempenho não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="eadaf-131">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="eadaf-132">Para obter informações sobre como conceder confiança em zonas diferentes, consulte [Caspol.exe (ferramenta de política de segurança de acesso do código)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span><span class="sxs-lookup"><span data-stu-id="eadaf-132">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eadaf-133">Em sistemas em que o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] é instalado, o Monitor de Desempenho poderá não exibir os dados dos contadores de desempenho em algumas categorias, tais como **Dados do .NET CLR** e **Rede do .NET CLR**, para aplicativos que foram desenvolvidos usando o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eadaf-133">On systems on which the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span></span> <span data-ttu-id="eadaf-134">Se esse for o caso, você pode configurar o Monitor de Desempenho para exibir esses dados, adicionando o elemento [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) ao arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eadaf-134">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="eadaf-135">Ler e criar contadores de desempenho de forma programática</span><span class="sxs-lookup"><span data-stu-id="eadaf-135">Reading and Creating Performance Counters Programmatically</span></span>  
 <span data-ttu-id="eadaf-136">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece classes que você pode usar para acessar de forma programática as mesmas informações de desempenho que estão disponíveis no console de desempenho.</span><span class="sxs-lookup"><span data-stu-id="eadaf-136">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="eadaf-137">Você também pode usar essas classes para criar contadores de desempenho personalizados.</span><span class="sxs-lookup"><span data-stu-id="eadaf-137">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="eadaf-138">A tabela a seguir descreve algumas das classes de monitoramento de desempenho que são fornecidas no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eadaf-138">The following table describes some of the performance monitoring classes that are provided in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
|<span data-ttu-id="eadaf-139">Classe</span><span class="sxs-lookup"><span data-stu-id="eadaf-139">Class</span></span>|<span data-ttu-id="eadaf-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="eadaf-140">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>|<span data-ttu-id="eadaf-141">Representa um componente do contador de desempenho do Windows NT.</span><span class="sxs-lookup"><span data-stu-id="eadaf-141">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="eadaf-142">Use essa classe para ler contadores existentes predefinidos ou personalizados e publicar dados de desempenho (gravação) em contadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="eadaf-142">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=fullName>|<span data-ttu-id="eadaf-143">Fornece vários métodos para interagir com os contadores e categorias de contadores no computador.</span><span class="sxs-lookup"><span data-stu-id="eadaf-143">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=fullName>|<span data-ttu-id="eadaf-144">Especifica um instalador para o componente `PerformanceCounter`.</span><span class="sxs-lookup"><span data-stu-id="eadaf-144">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=fullName>|<span data-ttu-id="eadaf-145">Especifica a fórmula para calcular o método `NextValue` para uma `PerformanceCounter`.</span><span class="sxs-lookup"><span data-stu-id="eadaf-145">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eadaf-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eadaf-146">See Also</span></span>  
 [<span data-ttu-id="eadaf-147">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="eadaf-147">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)
