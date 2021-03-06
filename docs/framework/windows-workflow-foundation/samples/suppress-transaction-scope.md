---
title: "Elimina o escopo de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fe13a8aae93548eedac2647e2429d66121377aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="suppress-transaction-scope"></a>Elimina o escopo de transação
O exemplo demonstra como criar uma atividade personalizado de `SuppressTransactionScope` para suprimir a transação ambiente de tempo de execução, se presente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A atividade personalizado é útil impedir que uma transação está fluída para fora a outro serviço se o fluxo de transação é indesejado para o cenário específico. O tempo de execução de fluxo de trabalho possui suporte interno para suprimir a transação ambiente na classe de <xref:System.Activities.NativeActivity> , mas para usar esse suporte que é necessário criar <xref:System.Activities.NativeActivity> personalizado como esse neste exemplo.  
  
 O cenário consiste em três partes. Primeiro, <xref:System.Activities.Statements.TransactionScope> cria uma transação de tempo de execução que se torne ambiente. Isso é verificado por uma atividade personalizado que imprimir o local e os identificadores distribuídos de transação. A transação é fluída a um serviço remoto antes de iniciar a segunda parte. Durante a segunda parte, o fluxo de trabalho entra em `SuppressTransactionScope` e repete novamente o processo de impressão os identificadores de transação e de fluxo a transação. No entanto, a atividade personalizado não encontra uma transação ambiente e a mensagem fluída para o serviço não contém a transação. Como resultado, o serviço cria uma transação, o que significa que o ID distribuído impresso no cliente e o serviço não correspondem. A parte final ocorre depois que `SuppressTransactionScope` sai e a transação de tempo de execução se torna novamente ambiente como verificado por outra mensagem para o serviço distribuído com um identificador que corresponde ao identificador da primeira mensagem.  
  
 A atividade própria deriva de <xref:System.Activities.NativeActivity> porque ele deve agendar uma atividade filho e adicionar uma propriedade de execução. `SuppressTransactionScope` tem <xref:System.Activities.Variable> de tipo <xref:System.Activities.RuntimeTransactionHandle>, que devem ser usados em vez de um campo da instância do tipo <xref:System.Activities.RuntimeTransactionHandle> porque o identificador deve ser inicializada. `Variable<RuntimeTransactionHandle>` é adicionado para metadados de atividade como uma variável de implementação porque ele é usado somente internamente.  
  
 Quando a atividade é executada primeiro verifica para ver se um corpo foi especificado e em caso afirmativo, defina a propriedade de `SuppressTransaction` em <xref:System.Activities.RuntimeTransactionHandle>. Uma vez que a propriedade é definida, é adicionada às propriedades de execução e fica ambiente. Isso significa que quaisquer atividades que é um filho de `SuppressTransactionScope` pode considerar a propriedade e impondo portanto exclusão de transação de tempo de execução e faz com que <xref:System.Activities.Statements.TransactionScope> aninhado gerencia uma exceção. O identificador é adicionada uma vez às propriedades que o corpo de execução é agendada para executar.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução de SuppressTransactionScope.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.  
  
3.  Depois que a compilação foi bem-sucedida, a solução e selecione **definir projetos de inicialização**. Na caixa de diálogo, selecione **vários projetos de inicialização** e certifique-se de que a ação de ambos os projetos é **iniciar**.  
  
4.  Pressione F5 ou selecione **iniciar depuração** do **depurar** menu. Como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** do **depurar** menu para executar sem depuração.  
  
    > [!NOTE]
    >  O servidor deve executar antes de iniciar o cliente. A saída da janela do console que hospeda o serviço indicam quando seguir o iniciarão.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`