---
title: "Integração de cache ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d56c435088be383821d17250e230cae848d2bab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-caching-integration"></a>Integração de cache ASP.NET
Este exemplo demonstra como utilizar o cache de saída do ASP.NET com o modelo de programação WCF WEB HTTP. Consulte o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo para uma versão auto-hospedado deste cenário que aborda a implementação de serviço em camadas. Este tópico enfoca o recurso de integração de cache de saída do ASP.NET.  
  
## <a name="demonstrates"></a>Demonstra  
 Integração com o Cache de saída ASP.NET  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Discussão  
 O exemplo usa o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET de utilizar o cache de saída com o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service. O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é aplicada às operações de serviço e fornece o nome de um perfil de cache em um arquivo de configuração que deve ser aplicado às respostas da operação de determinada.  
  
 No arquivo Service.cs do projeto de serviço de exemplo, tanto o `GetCustomer` e `GetCustomers` operações são marcadas com o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, que fornece o nome do perfil de cache "CacheFor60Seconds". No arquivo Web. config do projeto de serviço, o perfil de cache "CacheFor60Seconds" é fornecido com o <`caching`> elemento <`system.web`>. Para este perfil de cache, o valor de `duration` atributo é "60", que as respostas associadas ao perfil são armazenados em cache no cache de saída ASP.NET por 60 segundos. Além disso, para este perfil de cache, o `varmByParam` atributo é definido como "formato" caso solicitações com valores diferentes para o `format` consulta parâmetro de cadeia de caracteres, suas respostas em cache separadamente. Por fim, o perfil de cache `varyByHeader` atributo é definido como "Aceitar", para solicitações com diferentes valores de cabeçalho Accept tenham suas respostas em cache separadamente.  
  
 Program.cs no projeto do cliente demonstra como o cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço usando outras classes do .NET Framework, como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fábrica de canais e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) ilustram como usar essas classes para se comunicar com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
## <a name="to-run-the-sample"></a>Para executar a amostra  
 O exemplo consiste em três projetos:  
  
-   **Serviço**: projeto de um aplicativo da Web que inclui um serviço HTTP do WCF hospedado no ASP.NET.  
  
-   **Cliente**: um projeto de aplicativo de console que faz chamadas ao serviço.  
  
-   **Comuns**: uma biblioteca compartilhada que contém o tipo de cliente usado pelo cliente e serviço.  
  
 Quando o aplicativo de console do cliente é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo de integração de cache ASP.NET.  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Se o **Solution Explorer** janela não ainda estiver aberta, pressione CTRL + W + S.  
  
4.  Do **Solution Explorer** janela, o botão direito do mouse o **Service** do projeto e selecione **iniciar uma nova instância**. Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5.  Do **Solution Explorer** janela, o botão direito do mouse o **cliente** do projeto e selecione **iniciar uma nova instância**.  
  
6.  A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução. A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador.  
  
7.  Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
8.  Pressione qualquer tecla para fechar o aplicativo de console de cliente.  
  
9. Pressione SHIFT + F5 para parar a depuração de serviço.  
  
10. Na área de notificação do Windows, clique com botão direito no ícone do servidor de desenvolvimento ASP.NET e selecione **parar**.
