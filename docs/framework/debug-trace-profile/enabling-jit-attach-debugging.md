---
title: "Habilitando a depuração por anexação JIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71b2e95076edbda3a67a84c9185d8b689c158e12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="enabling-jit-attach-debugging"></a>Habilitando a depuração por anexação JIT
A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.  
  
 A depuração de anexação JIT é usada nas seguintes condições de falha:  
  
-   Exceções sem tratamento (no código nativo e gerenciado).  
  
-   Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).  
  
-   Erros fatais de tempo de execução.  
  
 A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:  
  
-   Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.  
  
-   Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.  
  
-   Função [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) (Win32).  
  
 Antes do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework fornecia chaves do Registro separadas para controlar o comportamento dos depuradores nativos e gerenciados. A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o controle é consolidado em uma única chave do Registro: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário. Para obter informações sobre como configurar essa chave do registro, consulte [Configurando depuração automática](http://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Consulte também  
 [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)  
 [Facilitando a depuração de uma imagem](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [Habilitando a criação de perfil](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
