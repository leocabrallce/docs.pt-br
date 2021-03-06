---
title: "Provedor de reflexão (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 617754fcd9515f080dc6cf8ae923c2c6fc34ad3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="reflection-provider-wcf-data-services"></a>Provedor de reflexão (WCF Data Services)
Além de expor os dados de um modelo de dados por meio do Entity Framework, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pode expor dados que não é estritamente definidos em um modelo baseado na entidade. O provedor de reflexão expõe dados em classes que retornam tipos que implementam o <xref:System.Linq.IQueryable%601> interface. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]usa reflexão para deduzir um modelo de dados para essas classes e pode traduzir consultas de endereço com base em recursos em consulta integrada à linguagem (LINQ)-com base em consultas em relação a exposto <xref:System.Linq.IQueryable%601> tipos.  
  
> [!NOTE]
>  Você pode usar o <xref:System.Linq.Queryable.AsQueryable%2A> método para retornar um <xref:System.Linq.IQueryable%601> interface de qualquer classe que implementa o <xref:System.Collections.Generic.IEnumerable%601> interface. Isso permite que os tipos de coleção mais genéricos ser usado como uma fonte de dados para o serviço de dados.  
  
 O provedor de reflexão oferece suporte a hierarquias de tipo. Para obter mais informações, consulte [como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Inferindo o modelo de dados  
 Quando você cria o serviço de dados, o provedor deduz o modelo de dados por meio de reflexão. A lista a seguir mostra como o provedor de reflexão infere o modelo de dados:  
  
-   Contêiner de entidade - a classe que expõe dados como propriedades que retornam um <xref:System.Linq.IQueryable%601> instância. Quando você resolver um modelo de dados com base em reflexão, o contêiner de entidade representa a raiz do serviço. Classe de contêiner de apenas uma entidade tem suporte para um namespace específico.  
  
-   Define a entidade - propriedades que retornam <xref:System.Linq.IQueryable%601> instâncias são tratadas como conjuntos de entidades. Conjuntos de entidades são tratados diretamente como recursos na consulta. Apenas uma propriedade no contêiner de entidade pode retornar um <xref:System.Linq.IQueryable%601> instância de um determinado tipo.  
  
-   Tipos de entidade - o tipo `T` do <xref:System.Linq.IQueryable%601> que o conjunto de entidades retorna. Classes que fazem parte de uma hierarquia de herança são convertidas pelo provedor de reflexão em uma hierarquia de tipo de entidade equivalente.  
  
-   As chaves da entidade - cada classe de dados que é um tipo de entidade deve ter uma propriedade de chave. Essa propriedade é atribuída com o <xref:System.Data.Services.Common.DataServiceKeyAttribute> atributo (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Você só deve aplicar o <xref:System.Data.Services.Common.DataServiceKeyAttribute> atributo a uma propriedade que pode ser usada para identificar exclusivamente uma instância do tipo de entidade. Esse atributo é ignorado quando aplicado a uma propriedade de navegação.  
  
-   Propriedades do tipo de entidade - diferente de chave da entidade, o provedor de reflexão trata as propriedades acessíveis, o indexador não de uma classe que é um tipo de entidade da seguinte maneira:  
  
    -   Se a propriedade retorna um tipo primitivo, em seguida, a propriedade deve para ser uma propriedade de um tipo de entidade.  
  
    -   Se a propriedade retorna um tipo que também é um tipo de entidade, em seguida, a propriedade é considerada uma propriedade de navegação que representa o fim "um" de uma relação muitos-para-um ou um.  
  
    -   Se a propriedade retorna um <xref:System.Collections.Generic.IEnumerable%601> de um tipo de entidade, em seguida, a propriedade é considerada como uma propriedade de navegação que representa o fim "muitos" de uma relação um-para-muitos ou muitos-para-muitos.  
  
    -   Se o tipo de retorno da propriedade é um tipo de valor, a propriedade representa um tipo complexo.  
  
> [!NOTE]
>  Ao contrário de um modelo de dados com base no modelo de entidade relacional, modelos com base no provedor de reflexão não entendem dados relacionais. Você deve usar o Entity Framework para expor dados relacionais por meio de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Mapeamento de tipo de dados  
 Quando um modelo de dados é inferido a partir de classes do .NET Framework, os tipos primitivos no modelo de dados são mapeados para tipos de dados do .NET Framework da seguinte maneira:  
  
|Tipo de dados do .NET Framework|Tipo do modelo de dados|  
|------------------------------|---------------------|  
|<xref:System.Byte> `[]`|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  Tipos de valor anuláveis do .NET framework são mapeados para os mesmos tipos de modelo de dados como os tipos de valor correspondente que não podem ser atribuídos um valor nulo.  
  
## <a name="enabling-updates-in-the-data-model"></a>Habilitar atualizações no modelo de dados  
 Para permitir atualizações para os dados que são expostos por meio desse tipo de modelo de dados, o provedor de reflexão define um <xref:System.Data.Services.IUpdatable> interface. Essa interface instrui o serviço de dados sobre como manter atualizações para os tipos expostos. Para habilitar as atualizações para recursos que são definidos pelo modelo de dados, a classe de contêiner de entidade deve implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter um exemplo de implementação do <xref:System.Data.Services.IUpdatable> interface, consulte [como: criar um serviço de dados usando uma fonte de dados SQL do LINQ](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 O <xref:System.Data.Services.IUpdatable> interface requer que os seguintes membros ser implementado para que as atualizações podem ser propagadas para a fonte de dados usando o provedor de reflexão:  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Fornece a funcionalidade para adicionar um objeto para uma coleção de objetos relacionados que são acessados a partir de uma propriedade de navegação.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Fornece a funcionalidade que cancela as alterações aos dados pendentes.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Fornece a funcionalidade para criar um novo recurso no contêiner especificado.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Fornece a funcionalidade para excluir um recurso.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Fornece a funcionalidade para recuperar um recurso identificado por um nome de consulta e o tipo específico.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Fornece a funcionalidade para retornar o valor de uma propriedade de um recurso.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Fornece a funcionalidade para remover um objeto para uma coleção de objetos relacionados acessados a partir de uma propriedade de navegação.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Fornece a funcionalidade para atualizar um recurso especificado.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Fornece a funcionalidade para retornar o recurso que é representado por uma instância de objeto específico.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Fornece a funcionalidade para salvar todas as alterações pendentes.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Fornece a funcionalidade para definir uma referência de objeto relacionado por meio de uma propriedade de navegação.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Fornece a funcionalidade para definir o valor da propriedade de um recurso.|  
  
## <a name="handling-concurrency"></a>Tratamento de simultaneidade  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]oferece suporte a um modelo de simultaneidade otimista, permitindo que você defina um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. O <xref:System.Data.Services.ETagAttribute> é aplicado a um tipo de entidade para definir um token de simultaneidade no provedor de reflexão. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualizar o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Usando o LINQ to SQL com o provedor de reflexão  
 Como o Entity Framework tem suporte nativo por padrão, é o provedor de dados recomendado para usar dados relacionais com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. No entanto, você pode usar o provedor de reflexão para usar o LINQ para classes do SQL com um serviço de dados. O <xref:System.Data.Linq.Table%601> retornado por métodos de conjuntos de resultados de <xref:System.Data.Linq.DataContext> gerado pelo LINQ para implementar SQL Object Relational Designer (O/R Designer) a <xref:System.Linq.IQueryable%601> interface. Isso permite que o provedor de reflexão acessar esses métodos e retornar dados de entidade do SQL Server usando o gerado classes LINQ to SQL. No entanto, porque o LINQ to SQL não implementa o <xref:System.Data.Services.IUpdatable> interface, você precisa adicionar uma classe parcial que estende o existente <xref:System.Data.Linq.DataContext> classe parcial para adicionar o <xref:System.Data.Services.IUpdatable> implementação. Para obter mais informações, consulte [como: criar um serviço de dados usando uma fonte de dados SQL do LINQ](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
