---
title: Armazenados em buffer receber
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7a486d3fbfb520ffe3b32c392566e5147c5dfcc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="buffered-receive"></a>Armazenados em buffer receber
Este exemplo demonstra como configurar e configurar o armazenados em buffer recebe o recurso em [!INCLUDE[wf](../../../../includes/wf-md.md)]. Armazenados em buffer receber permite que o autor de fluxo de trabalho crie um fluxo de trabalho sem ter que se preocupar na ordem em que as mensagens são recebidas. O armazenados em buffer recebe mensagens de buffers de recurso localmente e entrega-as quando o fluxo de trabalho está pronto para as receber.  
  
## <a name="demonstrates"></a>Demonstra  
 Como usar fora do serviço de processamento de mensagem armazenadas em buffer recebe com atividades de mensagem.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Discussão  
 Nesse exemplo, um serviço de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é implementado usando [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e tem uma sequência de atividades de <xref:System.ServiceModel.Activities.Receive> . Este fluxo de trabalho modelos um processo de aprovação simples do empréstimo onde o fluxo de trabalho espere três notificações para um empréstimo é certo. Um aplicativo cliente de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vem com três notificações correlacionadas em ordem inversa do serviço espera. Porque o armazenados em buffer recebe o recurso é ativado no serviço, cada mensagem fora de serviço é armazenada em buffer no serviço e processadas como o fluxo de trabalho se torna pronto para receber.  
  
 O armazenados em buffer recebe o recurso exige o suporte de <xref:System.ServiceModel.Activities.ReceiveContent> de associação, portanto usos <xref:System.ServiceModel.NetMsmqBinding>de serviço. Qualquer configuração especial é necessária para associação, para que as opções são usadas.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 O serviço também expõe metadados para o serviço usando <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Da mesma forma, o ponto final do cliente é configurado usando <xref:System.ServiceModel.NetMsmqBinding>. O código do cliente e a configuração é gerado usando o **adicionar referência de serviço** recurso de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. O exemplo a seguir é o ponto final de cliente gerado no arquivo App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Esse exemplo requer que os seguintes componentes do Windows estão ativados:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  compatibilidade com gerenciamento de[!INCLUDE[iis60](../../../../includes/iis60-md.md)] , Metabase, e a compatibilidade de configuração  
  
3.  Serviços de World Wide Web, recursos de desenvolvimento de aplicativos, e o ASP.NET  
  
4.  Servidor das filas de mensagens da Microsoft (MSMQ)  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar, e compilar o exemplo  
  
1.  Em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , o registro ASP.NET digitando `aspnet_regiis –I` e pressione ENTER.  
  
2.  Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] como um administrador.  
  
3.  LoanService.sln aberto.  
  
4.  Quando for perguntado se você deseja criar os diretórios virtuais para o projeto LoanService, selecione **Sim**.  
  
#### <a name="to-set-up-the-service-queues"></a>Para configurar as filas de serviço  
  
1.  Pressione F5 para executar o aplicativo de LoanClient que cria as filas e ativa o serviço definido em Service1.xamlx.  
  
2.  Abra o **gerenciamento do computador** console executando Compmgmt.msc em um prompt de comando.  
  
3.  No **gerenciamento do computador** de console, expanda **Service**, **aplicativos**, **enfileiramento**, **filas particulares** .  
  
4.  A fila de loanservice/service1.xamlx e selecione **propriedades**.  
  
5.  Selecione o **segurança** guia e adicionar **todos recebe mensagem**, **inspecionar mensagem** e **enviar mensagem** permissões.  
  
6.  Abra o gerenciador de [!INCLUDE[iis60](../../../../includes/iis60-md.md)] .  
  
7.  Navegue até **servidor**, **Sites**, **site da Web padrão**, **privada**, **LoanService** e selecione  **Opções avançadas**  
  
8.  Alterar o **protocolos habilitados** ser **http**, **NET. MSMQ**.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Navegue para http://localhost/private/loanservice/service1.xamlx para garantir que o serviço está sendo executado.  
  
2.  Pressione F5 para executar o aplicativo de LoanClient. Uma vez que o fluxo de trabalho estiver concluída, um arquivo de out.txt deve ser salvo a C:\Inbox que contém o resultado de troca de mensagem.  
  
#### <a name="to-clean-up"></a>Para limpar  
  
1.  Abra o **gerenciamento do computador** console executando Compmgmt.msc em um prompt de comando.  
  
2.  Expanda **Service** e **aplicativos**, **enfileiramento**, **filas particulares**.  
  
3.  Exclua a fila de loanservice/service1.xamlx.  
  
4.  Remova o diretório de C:\Inbox.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
