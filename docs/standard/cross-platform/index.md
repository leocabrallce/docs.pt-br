---
title: Desenvolvendo para várias plataformas com o .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9acceb04ea48ef7d9a99d8a82c63090ee344ea54
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>Desenvolvendo para várias plataformas com o .NET Framework
Você pode desenvolver aplicativos para plataformas Microsoft e não Microsoft usando o .NET Framework e o Visual Studio.  
  
## <a name="options-for-cross-platform-development"></a>Opções para o desenvolvimento de plataforma cruzada  
 Para desenvolver várias plataformas, é possível compartilhar código-fonte ou binários, além de fazer chamadas entre o código do .NET Framework e as APIs do Tempo de Execução do Windows.  
  
|Se desejar...|Use...|  
|-----------------------|------------|  
|Compartilhar código-fonte entre os aplicativos do Windows Phone 8.1 e do Windows 8.1|**Projetos compartilhados** (modelo de aplicativos Universal no Visual Studio 2013 atualização 2).<br /><br /> -No momento, não há suporte do Visual Basic.<br />-Você pode separar o código específico da plataforma usando #`if` instruções.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [Criar aplicativos para Windows e Windows Phone usando o Visual Studio](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (artigo do MSDN)<br />-   [Usando o Visual Studio para criar aplicativos XAML Universal](http://blogs.msdn.com/b/visualstudio/archive/2014/04/14/using-visual-studio-to-build-universal-xaml-apps.aspx) (postagem do blog)<br />-   [Usando o Visual Studio para criar aplicativos do XAML convergido](http://channel9.msdn.com/Events/Build/2014/3-591) (vídeo)|  
|Compartilhar binários entre aplicativos destinados a plataformas diferentes|**Projetos de biblioteca de classes portátil** para o código que é independente de plataforma.<br /><br /> -Essa abordagem geralmente é usada para o código que implementa a lógica de negócios.<br />-Você pode usar o Visual Basic ou c#.<br />-Suporte a API varia por plataforma.<br />-Portáteis projetos de biblioteca de classes que usam o Windows 8.1 e Windows Phone 8.1 oferecem suporte a APIs do Windows Runtime e XAML. Esses recursos não estão disponíveis em versões anteriores da Biblioteca de Classes Portátil.<br />-Se necessário, você pode abstrair o código específico da plataforma usando interfaces ou classes abstratas.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [Biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) (artigo do MSDN)<br />-   [Como fazer trabalhar de bibliotecas de classe portátil para você](http://blogs.msdn.com/b/dsplaisted/archive/2012/08/27/how-to-make-portable-class-libraries-work-for-you.aspx) (postagem do blog)<br />-   [Usando a biblioteca de classes portátil com modelo MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md) (artigo do MSDN)<br />-   [Recursos do aplicativo para bibliotecas que várias plataformas de destino](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md) (artigo do MSDN)<br />-   [Analisador de portabilidade do .NET](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) (extensão do Visual Studio)|  
|Compartilhar código-fonte entre aplicativos para plataformas diferentes do Windows 8.1 e do Windows Phone 8.1|**Adicionar como vínculo** recurso.<br /><br /> -Esta abordagem é adequada para a lógica de aplicativo que é comum para ambos os aplicativos, mas não portátil, por alguma razão. É possível usar esse recurso para o código do C# ou do Visual Basic.<br />     Por exemplo, o Windows Phone 8 e o Windows 8 compartilham as APIs do Tempo de Execução do Windows, mas as Bibliotecas de Classes Portáteis não oferecem suporte ao Tempo de Execução do Windows para essas plataformas. É possível usar `Add as link` para compartilhar o código do Tempo de Execução do Windows entre um aplicativo do Windows Phone 8 e um aplicativo da Windows Store destinado ao Windows 8.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [Compartilhar código com Adicionar como vínculo](http://msdn.microsoft.com/library/windowsphone/develop/jj714082\(v=vs.105\).aspx) (artigo do MSDN)<br />-   [Como: adicionar itens existentes a um projeto](http://msdn.microsoft.com/library/vstudio/9f4t9t92\(v=vs.100\).aspx) (artigo do MSDN)|  
|Gravar aplicativos da Windows Store usando o .NET Framework ou chamar APIs do Tempo de Execução do Windows do código do .NET Framework|**APIs do Windows Runtime** do seu código .NET Framework c# ou Visual Basic e usa o .NET Framework para criar aplicativos da Windows Store. Você deve saber as diferenças de API entre as duas plataformas. Porém, existem classes que ajudam a trabalhar com essas diferenças.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [.NET framework suporte para aplicativos da Windows Store e tempo de execução do Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md) (artigo do MSDN)<br />-   [Passando um URI para o tempo de execução do Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md) (artigo do MSDN)<br />-   <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>-->`System.IO.WindowsRuntimeStreamExtensions` (Página de referência de API do MSDN)<br />-   <!--zz <xref:System.WindowsRuntimeSystemExtensions>-->`System.WindowsRuntimeSystemExtensions` (Página de referência de API do MSDN)|  
|Compilar aplicativos do .NET Framework para plataformas que não sejam da Microsoft|**Assemblies de referência de biblioteca de classes portátil** no .NET Framework e uma ferramenta de terceiros ou extensão do Visual Studio como Xamarin.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [Biblioteca de classes portátil agora está disponível em todas as plataformas.](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx) (publicação de blog)<br />-   [Xamarin](http://xamarin.com/visual-studio) (Xamarin site)|  
|Usar JavaScript e HTML para desenvolvimento de plataforma cruzada|**Modelos de aplicativo universais** no Visual Studio 2013, atualização 2 para desenvolver com APIs do Windows Runtime para Windows 8.1 e Windows Phone 8.1. Atualmente, não é possível usar JavaScript e HTML com APIs do .NET Framework para desenvolver aplicativos de plataforma cruzada.<br /><br /> Para obter detalhes, consulte:<br /><br /> -   [Modelos de projeto de JavaScript](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)<br />-   [Portando um aplicativo de tempo de execução do Windows usando JavaScript para Windows Phone](http://msdn.microsoft.com/library/windows/apps/dn636144.aspx)|
