---
title: Migrando serviços Web de WSE 3.0 para o WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7e7187eb6ed444ba2c28aa301ce4b3b16129030
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrando serviços Web de WSE 3.0 para o WCF
Os benefícios da migração de serviços Web do WSE 3.0 para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] incluem melhor desempenho e suporte a transportes adicionais, cenários de segurança adicional e WS-* especificações. Um serviço Web que é migrado de WSE 3.0 para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ter até uma melhoria de desempenho de 200 a 400%. Para obter mais informações sobre os transportes suportados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Para obter uma lista dos cenários com suporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Para obter uma lista das especificações que são suportados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [guia de interoperabilidade de protocolos de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 As seções a seguir fornecem orientação sobre como migrar um recurso específico de um serviço WSE 3.0 Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general"></a>Geral  
 WSE 3.0 e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos incluem um conjunto comum de terminologia e interoperabilidade de nível de transmissão. WSE 3.0 e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos são o nível de transmissão interoperável com base no conjunto de WS-* especificações que dão suporte a ambos. Quando um WSE 3.0 ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo é desenvolvido há um conjunto comum de terminologia, como os nomes das declarações de segurança completa em WSE e os modos de autenticação.  
  
 Embora haja muitos aspectos semelhantes entre o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e ASP.NET ou WSE 3.0 modelos de programação, eles são diferentes. Para obter detalhes sobre o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação, consulte [ciclo de vida de programação básico](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Para migrar um serviço Web de WSE para WCF a [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta pode ser usada para gerar um cliente. No entanto, esse cliente contém interfaces e classes que podem ser usados como um valor inicial para um serviço WCF muito. As interfaces que são geradas têm o <xref:System.ServiceModel.OperationContractAttribute> atributo aplicado aos membros do contrato com o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade definida como `*`. Quando um cliente WSE chama um serviço Web com essa configuração, a seguinte exceção: **Web.Services3.ResponseProcessingException: WSE910: Ocorreu um erro durante o processamento de uma mensagem de resposta, e você pode encontrar o erro no interna exceção**. Para atenuar isso, defina o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade o <xref:System.ServiceModel.OperationContractAttribute> atributo não`null` valor, como `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Segurança  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Serviços Web do WSE 3.0 que são protegidos usando um arquivo de política  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem usar um arquivo de configuração para proteger um serviço e esse mecanismo é semelhante a um arquivo de política de WSE 3.0. WSE 3.0 ao proteger um serviço Web usando um arquivo de política, você pode usar uma asserção de segurança completa ou uma declaração de política personalizada. As declarações de segurança completa mapeiam com precisão até o modo de autenticação de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elemento de associação de segurança. Não apenas o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modos de autenticação e declarações de segurança completa de WSE 3.0 o mesmo nome ou da mesma forma, proteger as mensagens usando os mesmos tipos de credencial. Por exemplo, o `usernameForCertificate` asserção de segurança completa WSE 3.0 é mapeado para o `UsernameForCertificate` modo de autenticação no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Os exemplos de código a seguir demonstram como uma política mínimo que usa o `usernameForCertificate` asserção de segurança completa WSE 3.0 é mapeado para um `UsernameForCertificate` modo de autenticação no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em uma associação personalizada.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Para migrar as configurações de segurança de um serviço WSE 3.0 Web que são especificadas em um arquivo de política para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uma associação personalizada deve ser criada em um arquivo de configuração e a asserção de segurança completa deve ser definida para o modo de autenticação equivalente. Além disso, a associação personalizada deve ser configurada para usar o agosto de 2004 especificação WS-Addressing quando os clientes WSE 3.0 se comunicar com o serviço. Quando o migrados [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] o serviço não requer comunicação com clientes WSE 3.0 e só deve manter a paridade de segurança, considere o uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações definidas pelo sistema com configurações de segurança apropriadas em vez de criar um personalizado associação.  
  
 A tabela a seguir lista o mapeamento entre um arquivo de política de WSE 3.0 e o equivalente personalizado de associação no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Asserção do WSE 3.0 segurança completa|Configuração de associação personalizada do WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Para obter mais informações sobre como criar associações personalizadas no WCF, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Serviços Web do WSE 3.0 que são protegidos usando o código do aplicativo  
 Se WSE 3.0 ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é usado, os requisitos de segurança podem ser especificados no código do aplicativo em vez de na configuração. WSE 3.0, isso é feito criando uma classe que deriva de `Policy` classe e, em seguida, adicionando os requisitos de chamar o `Add` método. Para obter mais detalhes sobre como especificar os requisitos de segurança no código, consulte [como: proteger um Web serviço sem usando um arquivo de política](http://go.microsoft.com/fwlink/?LinkId=73747). Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], para especificar os requisitos de segurança no código, crie uma instância do <xref:System.ServiceModel.Channels.BindingElementCollection> classe e adicionar uma instância de um <xref:System.ServiceModel.Channels.SecurityBindingElement> para o <xref:System.ServiceModel.Channels.BindingElementCollection>. Os requisitos de asserção de segurança são definidos usando os métodos de auxiliares de modo de autenticação estático do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. Para obter mais detalhes sobre como especificar os requisitos de segurança no código usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) e [como: criar um SecurityBindingElement para um Especificado um modo de autenticação](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Asserção do WSE 3.0 política personalizada  
 Há dois tipos de declarações de política personalizada do WSE 3.0: aqueles que proteger uma mensagem SOAP e aqueles que não proteger uma mensagem SOAP. Declarações de política que proteger mensagens SOAP derivam WSE 3.0 `SecurityPolicyAssertion` classe e o equivalente conceitual em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é o <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
 Um ponto importante a observar é que as declarações de segurança completa de WSE 3.0 são um subconjunto do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modos de autenticação. Se você tiver criado uma declaração de política personalizada do WSE 3.0, pode haver um equivalente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modo de autenticação. Por exemplo, WSE 3.0 não fornecer uma asserção de segurança de CertificateOverTransport equivale a `UsernameOverTransport` asserção de segurança completa, mas usa um certificado x. 509 para fins de autenticação de cliente. Se você tiver definido sua própria declaração de política personalizada para este cenário, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] facilita a migração. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] define um modo de autenticação para esse cenário, portanto, você pode tirar proveito da autenticação estático métodos auxiliares de modo para configurar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Quando não há um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modo de autenticação que é equivalente a uma declaração de política personalizada que protege mensagens SOAP, derive uma classe de <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classes e especificar a associação equivalente elemento. Para obter mais detalhes, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Para converter uma declaração de política personalizada que não proteger uma mensagem SOAP, consulte [filtragem](../../../../docs/framework/wcf/feature-details/filtering.md) e o exemplo [Interceptor de mensagem personalizado](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Token de segurança personalizada 3.0 WSE  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação para criar um token personalizado é diferente de WSE 3.0. Para obter detalhes sobre como criar um token personalizado no WSE, consulte [criar Tokens de segurança personalizados](http://go.microsoft.com/fwlink/?LinkID=73750). Para obter detalhes sobre como criar um token personalizado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 Gerenciador de Token personalizado  
 O modelo de programação para criar um Gerenciador de token personalizado é diferente no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de WSE 3.0. Para obter detalhes sobre como criar um Gerenciador de token personalizado e os outros componentes que são necessários para um token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Se você tiver criado um personalizado `UsernameToken` Gerenciador de token de segurança, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece um mecanismo mais fácil para especificar a lógica de autenticação que a criação de Gerenciador de token de segurança personalizado. Para obter mais detalhes, consulte [como: usar um nome de usuário personalizada e validação de senha](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Serviços de WSE 3.0 Web que usam MTOM codificado mensagens SOAP  
 Como um aplicativo de 3 WSE, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo pode especificar a mensagem MTOM codificação na configuração. Para migrar a essa configuração, adicione o [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) para a associação para o serviço. O exemplo de código a seguir demonstra como a codificação de MTOM é especificado no WSE 3.0 para um serviço que é equivalente em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 3.0 aplicativos que usam a API de mensagens do WSE  
 Quando a API de mensagens do WSE é usada para obter acesso direto ao XML trocadas entre o cliente e o serviço Web, o aplicativo pode ser convertido para usar "Plain Old XML" (POX). Para obter mais detalhes sobre POX, consulte [interoperabilidade com aplicativos de POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Para obter mais detalhes sobre a API de mensagens do WSE, consulte [de envio e recebimento de mensagens usando WSE mensagens API SOAP](http://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transportes  
  
### <a name="tcp"></a>TCP  
 Por padrão, os clientes WSE 3.0 e serviços da Web que enviam mensagens SOAP usando o transporte TCP não interoperam com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes e serviços Web. Essa incompatibilidade ocorre devido a diferenças no enquadramento usado no protocolo TCP e por motivos de desempenho. No entanto, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplo fornece detalhes sobre como implementar uma sessão TCP personalizada que interopera com WSE 3.0. Para obter detalhes sobre esse exemplo, consulte [transporte: interoperabilidade de TCP do WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Para especificar que uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo usa o transporte TCP, use o [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transporte personalizado  
 O equivalente de um transporte personalizado WSE 3.0 em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é uma extensão de canal. Para obter detalhes sobre como criar uma extensão de canal, consulte [estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Ciclo de vida de programação básica](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
