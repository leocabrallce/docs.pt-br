---
title: "Alterações na segurança do .NET Framework"
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
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: 52
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b2ee4194f6e6788d99222badeb88e2702247904e
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="83547-102">Alterações na segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83547-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="83547-103">A alteração mais importante para a segurança no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] é referente ao uso de nomenclatura forte.</span><span class="sxs-lookup"><span data-stu-id="83547-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="83547-104">Consulte [Nomenclatura forte aprimorada](../../../docs/framework/app-domains/enhanced-strong-naming.md) para obter uma descrição dessas alterações.</span><span class="sxs-lookup"><span data-stu-id="83547-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="83547-105">O .NET Framework fornece um modelo de duas camadas de segurança para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="83547-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="83547-106">Aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] executados em um contêiner de segurança do Windows que limita o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="83547-106">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="83547-107">Dentro desse contêiner, os aplicativos gerenciados são executados de modo totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="83547-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="83547-108">De uma perspectiva de CAS (segurança de acesso de código), não há nada que um desenvolvedor possa fazer para elevar privilégios.</span><span class="sxs-lookup"><span data-stu-id="83547-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="83547-109">Para obter informações sobre os privilégios concedidos pelo Windows, consulte [Declarações de funcionalidades do aplicativo (Aplicativos da Windows Store)](http://go.microsoft.com/fwlink/?LinkId=230436) no Centro de Desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="83547-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="83547-110">Para obter informações sobre como criar um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, consulte [Criar seu primeiro aplicativo da Windows Store usando C# ou Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="83547-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
