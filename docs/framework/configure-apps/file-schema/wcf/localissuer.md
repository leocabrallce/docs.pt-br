---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c7e5c28325326d838da851ff4add12f8ae612c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
seção endpointBehaviors  
\<comportamento >  
\<clientCredentials >  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Cadeia de caracteres obrigatória. Especifica o URI do emissor local.|  
|associação|Cadeia de caracteres opcional. Uma das associações fornecidas pelo sistema. Para obter uma lista, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Cadeia de caracteres opcional. Especifica uma configuração de associação encontrada no arquivo de configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica informações de identidade para o emissor local.|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalhos de endereço são necessárias para tratar corretamente o emissor local. Você pode usar o `add` palavra-chave para adicionar um cabeçalho para esta coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Especifica um token personalizado usado para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Ao obter um token emitido de um Token de segurança Service (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a ser usada para se comunicar com o STS. Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornecer uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada é http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`, o cliente [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] canal usa os valores especificados pelo `address` e `binding` para se comunicar com o STS para obter o token emitido. Para obter mais informações sobre como configurar um emissor local, consulte [como: configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o `address`, `binding`, e `bindingConfiguration` atributos de uma `localIssuer` elemento.  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Como configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Como criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
