---
title: Codificador ByteStream
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de6d5fd64046a72eb6a21b43dd977463f5619850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bytestream-encoder"></a>Codificador ByteStream
Este exemplo demonstra como criar um `ByteStreamHttpBinding`, um <xref:System.ServiceModel.Channels.Binding> que demonstra a funcionalidade do codificador de fluxo de bytes.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra como criar um padrão <xref:System.ServiceModel.Channels.Binding> usando os elementos de associação padrão <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Este exemplo mostra como usar o codificador de fluxo de bytes para carregar e baixar uma imagem. O recurso de codificador de fluxo de bytes suporta apenas o transporte HTTP e não dá suporte a recursos como o sistema de mensagens confiável ou segurança. A única <xref:System.ServiceModel.Channels.MessageVersion> com suporte é <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Se você estiver executando esse exemplo [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], certifique-se de que você está executando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios elevados.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o arquivo ByteStreamHttpBinding.sln no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Inicie uma nova instância do projeto ByteStreamHttpBindingServer clicando duas vezes no projeto no Gerenciador de soluções e selecionando **depurar**e, em seguida, **iniciar nova instância** no menu de contexto.  
  
3.  Inicie uma nova instância do projeto ByteStreamHttpBindingClient clicando duas vezes no projeto no Gerenciador de soluções e selecionando **depurar**, **iniciar nova instância** no menu de contexto.
