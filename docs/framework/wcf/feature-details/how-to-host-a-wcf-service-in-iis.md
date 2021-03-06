---
title: "Como hospedar um serviço WCF no IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b23d3f69d52299fcf3ca8b5ff56d0c4673026b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Como hospedar um serviço WCF no IIS
Este tópico descreve as etapas básicas necessárias para criar um serviço [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que é hospedado por um IIS (Serviços de Informações da Internet). Este tópico pressupõe que você está familiarizado com o IIS e compreende como usar a ferramenta de gerenciamento do IIS para criar e gerenciar aplicativos do IIS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte IIS [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449). Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que é executado no ambiente do IIS aproveita os recursos do IIS, como a reciclagem do processo, desligamento ocioso, monitoramento de integridade do processo e a ativação baseada em mensagem. Essa opção de hospedando requer que o IIS esteja configurado corretamente, mas não requer que nenhum código de hospedagem seja escrito como parte do aplicativo. Você pode usar a hospedagem do IIS somente com um transporte HTTP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interagir, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando a segurança, consulte [segurança](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Para a cópia de origem deste exemplo, consulte [IIS hospedagem utilizando código embutido](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Para criar um serviço hospedado pelo IIS  
  
1.  Confirme se o IIS está instalado e em execução no computador. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]instalar e configurar o IIS consulte [instalando e configurando o IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Crie uma nova pasta para os arquivos do aplicativo denominada “IISHostedCalcService”, certifique-se de que o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tenha acesso ao conteúdo da pasta e use a ferramenta de gerenciamento do IIS para criar um novo aplicativo do IIS que esteja fisicamente localizado no diretório do aplicativo. Ao criar um alias para o diretório do aplicativo, use “IISHostedCalc”.  
  
3.  Crie um novo arquivo denominado “service.svc” no diretório do aplicativo. Editar esse arquivo adicionando as seguintes @ServiceHost elemento.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Crie um subdiretório App_Code no diretório do aplicativo.  
  
5.  Crie um novo arquivo de código denominado Service.cs no subdiretório App_Code.  
  
6.  Adicione as seguintes instruções de uso na parte superior do arquivo Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Adicione a seguinte declaração de namespace depois das instruções de uso.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Defina o contrato de serviço na declaração do namespace conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implemente o contrato de serviço depois da definição do contrato de serviço conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Crie um arquivo denominado "Web.config" no diretório do aplicativo e adicione o seguinte código de configuração no arquivo. Em tempo de execução, a infraestrutura do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa as informações para construir um ponto de extremidade com o qual os aplicativos-cliente possam se comunicar.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Este exemplo especifica explicitamente pontos de extremidade no arquivo de configuração. Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte de pontos de extremidade, associações e comportamentos padrão [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Para verificar se o serviço está hospedado corretamente, abra uma instância do Internet Explorer e navegue para a URL do serviço: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Exemplo  
 A listagem a seguir relaciona todo o código do serviço de calculadora hospedado no IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem nos Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Hospedando serviços](../../../../docs/framework/wcf/hosting-services.md)  
 [Serviços do WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
