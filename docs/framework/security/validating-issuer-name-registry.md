---
title: Validando Registro do nome do emissor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
caps.latest.revision: 4
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c6c1b72048f1f7cb421e5a19d34c2c2dea5463ce
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="validating-issuer-name-registry"></a><span data-ttu-id="ef1bf-102">Validando Registro do nome do emissor</span><span class="sxs-lookup"><span data-stu-id="ef1bf-102">Validating Issuer Name Registry</span></span>
<span data-ttu-id="ef1bf-103">O VINR (Registro de Validação de Nome do Emissor) para o Windows Identity Foundation permite que aplicativos de vários locatários garantam que um token de entrada seja emitido por um provedor de identidade e locatário confiável.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-103">The Validating Issuer Name Registry (VINR) for Windows Identity Foundation enables multi-tenant applications to ensure that an incoming token has been issued by a trusted tenant and identity provider.</span></span> <span data-ttu-id="ef1bf-104">Essa funcionalidade é particularmente útil para aplicativos de vários locatários que usam o Active Directory do Microsoft Azure porque todos os tokens emitidos pelo AD do Microsoft Azure são assinados usando o mesmo certificado.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-104">This functionality is particularly useful for multi-tenant applications that use Windows Azure Active Directory because all tokens issued by Windows Azure AD are signed using the same certificate.</span></span> <span data-ttu-id="ef1bf-105">Para diferenciar entre solicitações de vários locatários que usam o mesmo certificado – e, consequentemente, têm a mesma impressão digital – seu aplicativo deve persistir no nome do emissor para que cada locatário execute a lógica de validação.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-105">In order to differentiate between requests from multiple tenants that use the same certificate – and consequently have the same thumbprint – your application must persist the issuer name for each tenant to perform validation logic.</span></span> <span data-ttu-id="ef1bf-106">O VINR fornece essa funcionalidade e também permite que você adicione lógica de validação personalizada ou armazene os dados do Registro do emissor em locais diferentes de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-106">The VINR provides this functionality, and it also enables you to add custom validation logic or to store the issuer registry data in locations other than a configuration file.</span></span> <span data-ttu-id="ef1bf-107">A extensão pode ser adicionada ao pipeline WIF do aplicativo ou pode ser usada de modo independente.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-107">The extension can be added to your application’s WIF pipeline or it can be used independently.</span></span>  
  
 <span data-ttu-id="ef1bf-108">O VINR está disponível como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-108">The VINR is available as a NuGet package.</span></span> <span data-ttu-id="ef1bf-109">Consulte [Baixando o pacote do Registro do Nome do Emissor de Validação](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-109">See [Downloading the Validating Issuer Name Registry Package](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) for more information.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="ef1bf-110">Cenários</span><span class="sxs-lookup"><span data-stu-id="ef1bf-110">Scenarios</span></span>  
 <span data-ttu-id="ef1bf-111">O VINR permite o seguinte cenário principal:</span><span class="sxs-lookup"><span data-stu-id="ef1bf-111">The VINR enables the following key scenario:</span></span>  
  
-   <span data-ttu-id="ef1bf-112">**Validar um token em um aplicativo multilocatário**: nesse cenário, uma empresa chamada Litware desenvolveu um aplicativo multilocatário que usa um provedor de identidade como o Microsoft Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-112">**Validate a Token in a Multi-Tenant Application**: In this scenario, a company named Litware has developed a multi-tenant application that uses an identity provider such as Windows Azure AD.</span></span> <span data-ttu-id="ef1bf-113">Esse aplicativo atende dois clientes: Contoso e Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-113">This application serves two customers: Contoso and Fabrikam.</span></span> <span data-ttu-id="ef1bf-114">Quando um usuário da Fabrikam se autentica no aplicativo da Litware, o token resultante do AD do Microsoft Azure é assinado usando seu certificado padrão e a solicitação é emitida pela Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-114">When a user from Fabrikam authenticates to Litware’s application, the resulting token from Windows Azure AD is signed using its standard certificate and the request is issued by Fabrikam.</span></span> <span data-ttu-id="ef1bf-115">O aplicativo precisa verificar se o nome do emissor e o token são válidos, além de diferenciar as solicitações da Contoso que são assinadas usando o mesmo certificado do AD do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-115">The application needs to verify that both the issuer name and the token is valid, and needs to differentiate requests from Contoso that are signed using the same certificate from Windows Azure AD.</span></span> <span data-ttu-id="ef1bf-116">O VINR torna fácil para o aplicativo da Litware diferenciar e validar solicitações de vários locatários, como Contoso e Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-116">The VINR makes it easy for Litware’s application to differentiate and validate requests from multiple tenants such as Contoso and Fabrikam.</span></span>  
  
## <a name="features"></a><span data-ttu-id="ef1bf-117">Recursos</span><span class="sxs-lookup"><span data-stu-id="ef1bf-117">Features</span></span>  
 <span data-ttu-id="ef1bf-118">O VINR oferece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="ef1bf-118">The VINR offers the following features:</span></span>  
  
-   <span data-ttu-id="ef1bf-119">**Validação do nome do emissor e do token para aplicativos multilocatários**: valida o token de entrada verificando o nome do emissor (locatário) e se o token foi assinado usando um certificado válido do provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-119">**Issuer Name and Token Validation for Multi-Tenant Applications**: Validates the incoming token by verifying the issuer name (tenant) and whether the token was signed using a valid certificate from the identity provider.</span></span>  
  
-   <span data-ttu-id="ef1bf-120">**Extensibilidade da lógica de validação personalizada e dos armazenamentos de dados**: oferece extensibilidade para injeção de sua própria lógica de validação e especificação de um armazenamento de dados diferente do arquivo de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="ef1bf-120">**Extensibility for Custom Validation Logic and Data Stores**: Provides extensibility to inject your own validation logic and to specify a data store other than the default configuration file.</span></span>
