---
title: "Armazenando em cache em clientes de automação de interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: cce1890357f5781f1772b6a0aa583e493e2cfa8b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="caching-in-ui-automation-clients"></a>Armazenando em cache em clientes de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta o cache de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades e padrões de controle.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], cache significa pré-leitura de dados. Os dados possam ser acessados sem ainda mais a comunicação entre processos. Cache é normalmente usado por aplicativos clientes de automação de interface do usuário para recuperar as propriedades e padrões de controle em massa. Informações, em seguida, são recuperadas do cache conforme necessário. O aplicativo atualiza o cache periodicamente, geralmente em resposta a eventos significando que algo no [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] foi alterado.  
  
 Os benefícios do armazenamento em cache são mais perceptíveis com [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] controles e personalizadas que têm provedores de automação de interface do usuário do lado do servidor. Há menos benefício ao acessar provedores do lado do cliente, como os provedores padrão para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles.  
  
 Armazenamento em cache ocorre quando o aplicativo ativa um <xref:System.Windows.Automation.CacheRequest> e, em seguida, usa qualquer método ou propriedade que retorna um <xref:System.Windows.Automation.AutomationElement>; por exemplo, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Os métodos do <xref:System.Windows.Automation.TreeWalker> classe são uma exceção; o cache é feito somente se um <xref:System.Windows.Automation.CacheRequest> é especificado como um parâmetro (por exemplo, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Armazenamento em cache também ocorre quando você assina um evento enquanto um <xref:System.Windows.Automation.CacheRequest> está ativa. O <xref:System.Windows.Automation.AutomationElement> passado para o manipulador de eventos como a origem de um evento contém as propriedades armazenadas em cache e os padrões especificados pelo original <xref:System.Windows.Automation.CacheRequest>. Todas as alterações feitas a <xref:System.Windows.Automation.CacheRequest> após assinar o evento não têm nenhum efeito.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades e padrões de controle de um elemento podem ser armazenado em cache.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opções de cache  
 O <xref:System.Windows.Automation.CacheRequest> Especifica as opções a seguir para armazenar em cache.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Propriedades de cache  
 Você pode especificar propriedades para cache chamando <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> para cada propriedade antes de ativar a solicitação.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Padrões de controle para Cache  
 Você pode especificar os padrões de controle para cache chamando <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> para cada padrão antes de ativar a solicitação. Quando um padrão é armazenado em cache, suas propriedades não estão automaticamente em cache; Você deve especificar as propriedades que você deseja armazenar em cache usando <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Escopo e a filtragem de cache  
 Você pode especificar os elementos cujos propriedades e padrões a serem armazenados em cache, definindo o <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> propriedade antes de ativar a solicitação. O escopo é relativo os elementos que são recuperados enquanto a solicitação está ativa. Por exemplo, se você definir somente <xref:System.Windows.Automation.TreeScope.Children>e, em seguida, recuperar um <xref:System.Windows.Automation.AutomationElement>, as propriedades e os padrões de filhos do elemento são armazenados em cache, mas não os do próprio elemento. Para garantir que o cache é feito para o próprio elemento recuperado, você deve incluir <xref:System.Windows.Automation.TreeScope.Element> no <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> propriedade. Não é possível definir o escopo para <xref:System.Windows.Automation.TreeScope.Parent> ou <xref:System.Windows.Automation.TreeScope.Ancestors>. No entanto, um elemento pai pode ser armazenado em cache quando um elemento filho é armazenado em cache; Consulte Recuperando armazenado em cache filhos e pais neste tópico.  
  
 A extensão de armazenamento em cache também é afetada pelo <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> propriedade. Por padrão, o cache é executado somente para elementos que aparecem na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. No entanto, você pode alterar esta propriedade para aplicar o cache para todos os elementos, ou apenas para elementos que aparecem na exibição de conteúdo.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Intensidade das referências de elemento  
 Quando você recuperar um <xref:System.Windows.Automation.AutomationElement>, por padrão, você tem acesso a todas as propriedades e padrões desse elemento, incluindo aqueles que não foram armazenadas em cache. No entanto, para maior eficiência você pode especificar que a referência ao elemento refere-se a dados em cache, definindo o <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> propriedade o <xref:System.Windows.Automation.CacheRequest> para <xref:System.Windows.Automation.AutomationElementMode.None>. Nesse caso, você não tem acesso a todas as propriedades não armazenado em cache e padrões de elementos recuperados. Isso significa que você não pode acessar todas as propriedades por meio de <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou `Current` propriedade <xref:System.Windows.Automation.AutomationElement> ou qualquer padrão de controle; nem pode recuperar um padrão usando <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Em padrões em cache, você pode chamar métodos que recuperam propriedades de array, como <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, mas não os que executem ações no controle, como <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Um exemplo de um aplicativo que talvez não seja necessário completas referências a objetos é um leitor de tela, que faria pré-leitura de <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> e <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> propriedades de elementos em uma janela, mas não será necessário o <xref:System.Windows.Automation.AutomationElement> próprios objetos.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Ativando o CacheRequest  
 Armazenamento em cache é executado somente quando <xref:System.Windows.Automation.AutomationElement> objetos são recuperados enquanto um <xref:System.Windows.Automation.CacheRequest> está ativo para o thread atual. Há duas maneiras de ativar um <xref:System.Windows.Automation.CacheRequest>.  
  
 A maneira usual é chamar <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Este método retorna um objeto que implementa <xref:System.IDisposable>. A solicitação permanece ativa enquanto o <xref:System.IDisposable> objeto existe. A maneira mais fácil de controlar o tempo de vida do objeto é colocar a chamada dentro de um `using` ([!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]) ou `Using` ([!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) bloco. Isso garante que a solicitação vai ser ser removida da pilha mesmo se uma exceção é gerada.  
  
 Outra maneira, que é útil quando você deseja aninhar solicitações de cache, é chamar <xref:System.Windows.Automation.CacheRequest.Push%2A>. Isso coloca a solicitação em uma pilha e ativa. A solicitação permanece ativa até ser removida da pilha por <xref:System.Windows.Automation.CacheRequest.Pop%2A>. A solicitação fica temporariamente inativa se outra solicitação é enviada para a pilha; somente a solicitação superior na pilha está ativa.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Recuperando propriedades em cache  
 Você pode recuperar as propriedades armazenadas em cache de um elemento por meio de métodos e propriedades a seguir.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Uma exceção é gerada se a propriedade solicitada não está no cache.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, como <xref:System.Windows.Automation.AutomationElement.Current%2A>, expõe propriedades individuais como membros de uma estrutura. No entanto, você não precisa recuperar essa estrutura; Você pode acessar diretamente as propriedades individuais. Por exemplo, o <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> propriedade pode ser obtida `element.Cached.Name`, onde `element` é um <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Recuperando em cache padrões de controle  
 Você pode recuperar os padrões de controle em cache de um elemento por meio dos métodos a seguir.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Se o padrão não está no cache, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> gera uma exceção, e <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> retorna `false`.  
  
 Você pode recuperar as propriedades armazenadas em cache de um padrão de controle usando o `Cached` propriedade do objeto padrão. Você também pode recuperar os valores atuais através de `Current` propriedade, mas somente se <xref:System.Windows.Automation.AutomationElementMode.None> não foi especificado quando o <xref:System.Windows.Automation.AutomationElement> foi recuperado. (<xref:System.Windows.Automation.AutomationElementMode.Full> é o valor padrão, e isso permite acesso aos valores atuais.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Recuperando em cache filhos e pais  
 Quando você recuperar um <xref:System.Windows.Automation.AutomationElement> e solicita o cache dos filhos desse elemento através de <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> propriedade da solicitação, é possível obter filho de elementos de posteriormente o <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> propriedade do elemento que você recuperou.  
  
 Se <xref:System.Windows.Automation.TreeScope.Element> foi incluído no escopo da solicitação de cache, o elemento raiz da solicitação está subsequentemente disponível a partir do <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> propriedade de qualquer um dos elementos filho.  
  
> [!NOTE]
>  Você não pode armazenar em cache os pais ou ancestrais do elemento raiz da solicitação.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Atualização do Cache  
 O cache é válido somente quando não há alterações no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. O aplicativo é responsável por atualizar o cache, normalmente em resposta a eventos.  
  
 Se você assinar um evento enquanto um <xref:System.Windows.Automation.CacheRequest> está ativo, obterá um <xref:System.Windows.Automation.AutomationElement> com um cache atualizado como a origem do evento sempre que o delegado do manipulador de eventos é chamado. Você também pode atualizar as informações armazenadas em cache para um elemento chamando <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Você pode transmitir original <xref:System.Windows.Automation.CacheRequest> para atualizar todas as informações que foram armazenadas anteriormente.  
  
 Atualizando o cache não altera as propriedades de qualquer existente <xref:System.Windows.Automation.AutomationElement> referências.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Exemplo de FetchTimer](http://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
