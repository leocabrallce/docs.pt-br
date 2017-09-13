---
title: Empacotando um assembly para o COM
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
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 73866ddc1e8199dfad188179dc668bc31ab3c93d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="d0a9d-102">Empacotando um assembly para o COM</span><span class="sxs-lookup"><span data-stu-id="d0a9d-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="d0a9d-103">Desenvolvedores COM podem aproveitar as informações a seguir sobre os tipos gerenciados que pretendem incorporar em seus aplicativos:</span><span class="sxs-lookup"><span data-stu-id="d0a9d-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="d0a9d-104">Uma lista de tipos que aplicativos COM podem consumir</span><span class="sxs-lookup"><span data-stu-id="d0a9d-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="d0a9d-105">Alguns tipos gerenciados são visíveis para COM; alguns são visíveis, mas não instanciável; e alguns são visíveis e instanciáveis.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="d0a9d-106">Um assembly pode incluir qualquer combinação de tipos invisíveis, visíveis, não instanciáveis e instanciáveis.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="d0a9d-107">Para fins de integridade, identifique os tipos em um assembly que você pretende expor ao COM, especialmente quando esses tipos são um subconjunto dos tipos expostos ao .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="d0a9d-108">Para obter mais informações, consulte [Qualificando tipos do .NET para interoperação](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="d0a9d-108">For additional information, see [Qualifying .NET Types for Interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="d0a9d-109">Instruções de controle de versão</span><span class="sxs-lookup"><span data-stu-id="d0a9d-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="d0a9d-110">Classes gerenciadas que implementam a interface de classe (uma interface gerada por interoperabilidade COM) estão sujeitas a restrições de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="d0a9d-111">Para obter diretrizes sobre como usar a interface de classe, consulte [Introdução à interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="d0a9d-111">For guidelines on using the class interface, see [Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
-   <span data-ttu-id="d0a9d-112">Instruções de implantação</span><span class="sxs-lookup"><span data-stu-id="d0a9d-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="d0a9d-113">Assemblies de nome forte que são assinados por um editor podem ser instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="d0a9d-114">Assemblies não assinados devem ser instalados no computador do usuário como assemblies particulares.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="d0a9d-115">Para obter mais informações, consulte [Considerações sobre segurança de assembly](../../../docs/framework/app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="d0a9d-115">For additional information, see [Assembly Security Considerations](../../../docs/framework/app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="d0a9d-116">Inclusão de biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="d0a9d-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="d0a9d-117">A maioria dos tipos requerem uma biblioteca de tipos quando consumidos por um aplicativo COM.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="d0a9d-118">Você pode gerar uma biblioteca de tipos ou fazer com que desenvolvedores COM executem essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="d0a9d-119">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fornece as opções a seguir para gerar uma biblioteca de tipos:</span><span class="sxs-lookup"><span data-stu-id="d0a9d-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="d0a9d-120">Exportador da Biblioteca de Tipos</span><span class="sxs-lookup"><span data-stu-id="d0a9d-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="d0a9d-121">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="d0a9d-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="d0a9d-122">Ferramenta de Registro de Assembly</span><span class="sxs-lookup"><span data-stu-id="d0a9d-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="d0a9d-123">Ferramenta de Instalação de Serviços .NET</span><span class="sxs-lookup"><span data-stu-id="d0a9d-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="d0a9d-124">Independentemente do mecanismo escolhido, somente os tipos públicos definidos no assembly que você fornecer são incluídos na biblioteca de tipos gerada.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="d0a9d-125">Você pode empacotar uma biblioteca de tipos como um arquivo separado ou inseri-la como arquivo de recurso Win32 dentro de um aplicativo baseado em .NET.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="d0a9d-126">Microsoft Visual Basic 6.0 executou essa tarefa para você automaticamente. No entanto, ao usar [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], você deve inserir manualmente sua biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="d0a9d-127">Para obter instruções, consulte [Como inserir bibliotecas de tipos como recursos do Win32 em aplicativos baseados em .NET](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span><span class="sxs-lookup"><span data-stu-id="d0a9d-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="d0a9d-128">Exportador da Biblioteca de Tipos</span><span class="sxs-lookup"><span data-stu-id="d0a9d-128">Type Library Exporter</span></span>  
 <span data-ttu-id="d0a9d-129">O [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-129">The [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d0a9d-130">Quando as informações de tipo da classe estão disponíveis, os clientes COM podem criar uma instância da classe do .NET e chamar os métodos da instância, como se fosse um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="d0a9d-131">Tlbexp.exe converte um assembly inteiro de uma vez.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="d0a9d-132">Não é possível usar Tlbexp.exe para gerar informações de tipo para um subconjunto dos tipos definidos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="d0a9d-133">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="d0a9d-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="d0a9d-134">A classe <xref:System.Runtime.InteropServices.TypeLibConverter>, localizada no namespace **System.Runtime.Interop**, converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d0a9d-135">Essa API produz as mesmas informações que o Exportador da Biblioteca de Tipos, descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="d0a9d-136">A **classe TypeLibConverter** implementa o <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="d0a9d-137">Ferramenta de Registro de Assembly</span><span class="sxs-lookup"><span data-stu-id="d0a9d-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="d0a9d-138">A [Ferramenta de Registro de Assembly (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) pode gerar e registrar uma biblioteca de tipos quando você aplica a opção **/tlb:**.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-138">The [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="d0a9d-139">Clientes COM exigem que as bibliotecas de tipos sejam instaladas no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="d0a9d-140">Sem essa opção, o Regasm.exe registra somente os tipos em um assembly, mas não a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="d0a9d-141">Registrar os tipos em um assembly e registrando a biblioteca de tipos são atividades distintas.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="d0a9d-142">Ferramenta de Instalação de Serviços .NET</span><span class="sxs-lookup"><span data-stu-id="d0a9d-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="d0a9d-143">A [ferramenta de instalação de serviços .NET (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) adiciona classes gerenciadas para Serviços do Componente do Windows 2000 e combina várias tarefas em uma única ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-143">The [.NET Services Installation Tool (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="d0a9d-144">Além de carregar e registrar um assembly, Regsvcs.exe pode gerar, registrar e instalar a biblioteca de tipos em um aplicativo COM+ 1.0 existente.</span><span class="sxs-lookup"><span data-stu-id="d0a9d-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a9d-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0a9d-145">See Also</span></span>  
 <span data-ttu-id="d0a9d-146"><xref:System.Runtime.InteropServices.TypeLibConverter></span><span class="sxs-lookup"><span data-stu-id="d0a9d-146"><xref:System.Runtime.InteropServices.TypeLibConverter></span></span>   
 <span data-ttu-id="d0a9d-147"><xref:System.Runtime.InteropServices.ITypeLibConverter></span><span class="sxs-lookup"><span data-stu-id="d0a9d-147"><xref:System.Runtime.InteropServices.ITypeLibConverter></span></span>   
 <span data-ttu-id="d0a9d-148">[Expondo componentes do .NET Framework para COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-148">[Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span></span>  
 <span data-ttu-id="d0a9d-149">[Qualificando tipos do .NET para interoperação](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-149">[Qualifying .NET Types for Interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md) </span></span>  
 <span data-ttu-id="d0a9d-150">[Introdução à Interface de Classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-150">[Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) </span></span>  
 <span data-ttu-id="d0a9d-151">[Considerações sobre segurança de assembly](../../../docs/framework/app-domains/assembly-security-considerations.md) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-151">[Assembly Security Considerations](../../../docs/framework/app-domains/assembly-security-considerations.md) </span></span>  
 <span data-ttu-id="d0a9d-152">[Tlbexp.exe (Exportador da Biblioteca de Tipos)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-152">[Tlbexp.exe (Type Library Exporter)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) </span></span>  
 <span data-ttu-id="d0a9d-153">[Registrando assemblies usando COM](../../../docs/framework/interop/registering-assemblies-with-com.md) </span><span class="sxs-lookup"><span data-stu-id="d0a9d-153">[Registering Assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md) </span></span>  
 [<span data-ttu-id="d0a9d-154">Como inserir bibliotecas de tipo como recursos do Win32 em aplicativos</span><span class="sxs-lookup"><span data-stu-id="d0a9d-154">How to: Embed Type Libraries as Win32 Resources in Applications</span></span>](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)
