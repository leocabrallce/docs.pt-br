---
title: "Criação de extensibilidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbee2fb24b9acf9bc2512b399e3a74e66720cc3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="0539a-102">Criação de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="0539a-102">Designing for Extensibility</span></span>
<span data-ttu-id="0539a-103">Um aspecto importante da criação de uma estrutura é verificar se que a extensibilidade do framework foram considerada com cuidado.</span><span class="sxs-lookup"><span data-stu-id="0539a-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="0539a-104">Isso requer que você entenda os custos e os benefícios associados a vários mecanismos de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="0539a-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="0539a-105">Este capítulo ajuda você a decidir qual dos mecanismos de extensibilidade — subclassificação, eventos, membros virtuais, retornos de chamada e assim por diante — melhor pode atender aos requisitos da sua estrutura.</span><span class="sxs-lookup"><span data-stu-id="0539a-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="0539a-106">Há várias maneiras para permitir a extensibilidade em estruturas.</span><span class="sxs-lookup"><span data-stu-id="0539a-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="0539a-107">Elas variam de menos eficiente, mas menos dispendiosa para muito eficientes, mas caros.</span><span class="sxs-lookup"><span data-stu-id="0539a-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="0539a-108">Para qualquer requisito de extensibilidade de determinado, você deve escolher o mecanismo de extensibilidade menos dispendioso que atenda aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="0539a-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="0539a-109">Tenha em mente que é possível adicionar mais extensibilidade posteriormente, mas você pode nunca tirá-lo sem introduzir alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="0539a-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0539a-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0539a-110">In This Section</span></span>  
 [<span data-ttu-id="0539a-111">Classes não lacradas</span><span class="sxs-lookup"><span data-stu-id="0539a-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="0539a-112">Membros protegidos</span><span class="sxs-lookup"><span data-stu-id="0539a-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="0539a-113">Eventos e retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="0539a-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="0539a-114">Membros virtuais</span><span class="sxs-lookup"><span data-stu-id="0539a-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="0539a-115">Abstrações (tipos abstratos e Interfaces)</span><span class="sxs-lookup"><span data-stu-id="0539a-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="0539a-116">Classes base para implementar abstrações</span><span class="sxs-lookup"><span data-stu-id="0539a-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="0539a-117">Lacrar</span><span class="sxs-lookup"><span data-stu-id="0539a-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="0539a-118">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="0539a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0539a-119">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0539a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0539a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0539a-120">See Also</span></span>  
 [<span data-ttu-id="0539a-121">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="0539a-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)