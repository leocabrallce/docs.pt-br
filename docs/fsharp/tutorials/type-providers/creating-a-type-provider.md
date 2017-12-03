---
title: 'Tutorial: Criando um provedor de tipos (F#)'
description: "Saiba como criar seus próprios provedores de tipos F # em F # 3.0 examinando vários provedores de tipo simples para ilustrar os conceitos básicos."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: a1d6315c2546de12e85efdd06cf2520605cb6e91
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="tutorial-creating-a-type-provider"></a><span data-ttu-id="ede55-104">Tutorial: Criando um provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="ede55-104">Tutorial: Creating a Type Provider</span></span>

> [!NOTE]
<span data-ttu-id="ede55-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="ede55-105">This guide was written for F# 3.0 and will be updated.</span></span>

<span data-ttu-id="ede55-106">O mecanismo de provedor do tipo F # 3.0 é uma parte significativa de seu suporte para programação avançada de informações.</span><span class="sxs-lookup"><span data-stu-id="ede55-106">The type provider mechanism in F# 3.0 is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="ede55-107">Este tutorial explica como criar seus próprios provedores de tipo, você acompanhará o desenvolvimento de vários provedores de tipo simples para ilustrar os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="ede55-107">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="ede55-108">Para obter mais informações sobre o mecanismo de provedor de tipo em F #, consulte [provedores de tipos](index.md).</span><span class="sxs-lookup"><span data-stu-id="ede55-108">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="ede55-109">F # 3.0 contém vários provedores de tipo interno para serviços de dados usados na Internet e enterprise.</span><span class="sxs-lookup"><span data-stu-id="ede55-109">F# 3.0 contains several built-in type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="ede55-110">Esses provedores de tipo concedem acesso simple e regular para bancos de dados relacionais do SQL e serviços OData e WSDL baseados em rede.</span><span class="sxs-lookup"><span data-stu-id="ede55-110">These type providers give simple and regular access to SQL relational databases and network-based OData and WSDL services.</span></span> <span data-ttu-id="ede55-111">Esses provedores também suportam o uso de consultas LINQ F # em relação a essas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="ede55-111">These providers also support the use of F# LINQ queries against these data sources.</span></span>

<span data-ttu-id="ede55-112">Quando necessário, você pode criar provedores de tipo personalizado, ou você pode fazer referência a provedores de tipos que outros criaram.</span><span class="sxs-lookup"><span data-stu-id="ede55-112">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="ede55-113">Por exemplo, sua organização pode ter um serviço de dados que fornece um número grande e crescente de conjuntos de dados nomeados, cada qual com seu próprio esquema de dados estáveis.</span><span class="sxs-lookup"><span data-stu-id="ede55-113">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="ede55-114">Você pode criar um provedor de tipos que lê os esquemas e apresenta os conjuntos de dados atuais para o programador de maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="ede55-114">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="ede55-115">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="ede55-115">Before You Start</span></span>
<span data-ttu-id="ede55-116">O mecanismo de provedor de tipo é projetado principalmente para injeção de dados estáveis e espaços de informações de serviço para o F # experiência em programação.</span><span class="sxs-lookup"><span data-stu-id="ede55-116">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="ede55-117">Esse mecanismo não foi projetado para injeção de espaços de informações cuja esquema é alterado durante a execução do programa de maneiras que são relevantes para a lógica do programa.</span><span class="sxs-lookup"><span data-stu-id="ede55-117">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="ede55-118">Além disso, o mecanismo não foi projetado para intraidioma metaprogramação, mesmo que esse domínio contém alguns usos válidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-118">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="ede55-119">Você deve usar esse mecanismo somente quando necessário e onde o desenvolvimento de um provedor de tipo produz o valor muito alto.</span><span class="sxs-lookup"><span data-stu-id="ede55-119">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="ede55-120">Evite escrever um provedor de tipo em que um esquema não está disponível.</span><span class="sxs-lookup"><span data-stu-id="ede55-120">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="ede55-121">Da mesma forma, evite escrever um provedor de tipo, onde um comum (ou até mesmo uma existente) biblioteca .NET seria suficiente.</span><span class="sxs-lookup"><span data-stu-id="ede55-121">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="ede55-122">Antes de começar, você pode responder às seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="ede55-122">Before you start, you might ask the following questions:</span></span>


- <span data-ttu-id="ede55-123">Você tem um esquema para a fonte de informações?</span><span class="sxs-lookup"><span data-stu-id="ede55-123">Do you have a schema for your information source?</span></span> <span data-ttu-id="ede55-124">Nesse caso, o que é o mapeamento para o F # e sistema de tipo .NET?</span><span class="sxs-lookup"><span data-stu-id="ede55-124">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="ede55-125">Você pode usar uma API (dinamicamente tipada) existente como ponto de partida para sua implementação?</span><span class="sxs-lookup"><span data-stu-id="ede55-125">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="ede55-126">Você e sua organização terá suficiente usa do provedor de tipo para fazer a gravação vale a pena?</span><span class="sxs-lookup"><span data-stu-id="ede55-126">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="ede55-127">Uma biblioteca .NET normal atendem às suas necessidades?</span><span class="sxs-lookup"><span data-stu-id="ede55-127">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="ede55-128">Quanto alterará seu esquema?</span><span class="sxs-lookup"><span data-stu-id="ede55-128">How much will your schema change?</span></span>

- <span data-ttu-id="ede55-129">Ele será alterado durante a codificação?</span><span class="sxs-lookup"><span data-stu-id="ede55-129">Will it change during coding?</span></span>

- <span data-ttu-id="ede55-130">Ele será alterado entre as sessões de codificação?</span><span class="sxs-lookup"><span data-stu-id="ede55-130">Will it change between coding sessions?</span></span>

- <span data-ttu-id="ede55-131">Ele será alterado durante a execução do programa?</span><span class="sxs-lookup"><span data-stu-id="ede55-131">Will it change during program execution?</span></span>

<span data-ttu-id="ede55-132">Provedores de tipos são mais adequados para situações em que o esquema é estável no tempo de execução e durante o tempo de vida do código compilado.</span><span class="sxs-lookup"><span data-stu-id="ede55-132">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="ede55-133">Um provedor de tipo simples</span><span class="sxs-lookup"><span data-stu-id="ede55-133">A Simple Type Provider</span></span>
<span data-ttu-id="ede55-134">Este exemplo é Samples.HelloWorldTypeProvider no `SampleProviders\Providers` diretório do [pacote de exemplo do F # 3.0](http://fsharp3sample.codeplex.com) no site da Codeplex.</span><span class="sxs-lookup"><span data-stu-id="ede55-134">This sample is Samples.HelloWorldTypeProvider in the `SampleProviders\Providers` directory of the [F# 3.0 Sample Pack](http://fsharp3sample.codeplex.com) on the Codeplex website.</span></span> <span data-ttu-id="ede55-135">O provedor torna disponível um "espaço de tipo" que contém 100 tipos apagados, como mostra o seguinte código usando a sintaxe de assinatura do F # e omitir os detalhes para todos, exceto `Type1`.</span><span class="sxs-lookup"><span data-stu-id="ede55-135">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="ede55-136">Para obter mais informações sobre tipos apagados, consulte [detalhes sobre apagados fornecido tipos](#details-about-erased-provided-types) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-136">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    /// This is an instance property.
    nested type NestedType = 
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="ede55-137">Observe que o conjunto de tipos e membros fornecidos estaticamente é conhecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-137">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="ede55-138">Este exemplo não aproveitar a capacidade de provedores para fornecer tipos que dependem de um esquema.</span><span class="sxs-lookup"><span data-stu-id="ede55-138">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="ede55-139">A implementação do provedor de tipo é descrita no código a seguir, e os detalhes são abordados nas seções posteriores deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-139">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="ede55-140">Pode haver algumas pequenas diferenças de nomenclatura entre esse código e as amostras online.</span><span class="sxs-lookup"><span data-stu-id="ede55-140">There may be some small naming differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) = 
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ] 

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

  [<assembly:TypeProviderAssembly>] 
  do()
```

<span data-ttu-id="ede55-141">Para usar esse provedor, abra uma instância separada do Visual Studio 2012, criar um script de F # e, em seguida, adicione uma referência para o provedor do seu script usando #r como o código a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="ede55-141">To use this provider, open a separate instance of Visual Studio 2012, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="ede55-142">Procure os tipos sob o `Samples.HelloWorldTypeProvider` namespace que o provedor de tipos gerado.</span><span class="sxs-lookup"><span data-stu-id="ede55-142">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="ede55-143">Antes de você recompile o provedor, certifique-se de que você fechou todas as instâncias do Visual Studio e F # interativo que estiver usando a DLL do provedor.</span><span class="sxs-lookup"><span data-stu-id="ede55-143">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="ede55-144">Caso contrário, ocorrerá um erro de compilação porque a DLL de saída será bloqueada.</span><span class="sxs-lookup"><span data-stu-id="ede55-144">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="ede55-145">Para depurar este provedor usando as instruções print, faça um script que expõe um problema com o provedor e, em seguida, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ede55-145">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ede55-146">Para depurar este provedor usando o Visual Studio, abra um prompt de comando do Visual Studio com credenciais administrativas e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ede55-146">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ede55-147">Como alternativa, abra o Visual Studio, abra o menu Depurar, escolha `Debug/Attach to process…`e anexar para outro `devenv` processo em que você está editando seu script.</span><span class="sxs-lookup"><span data-stu-id="ede55-147">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="ede55-148">Usando esse método, você pode direcionar mais facilmente a lógica específica no provedor de tipo digitando interativamente expressões na segunda instância (com e outros recursos do IntelliSense completo).</span><span class="sxs-lookup"><span data-stu-id="ede55-148">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="ede55-149">Você pode desabilitar apenas meu código depuração para identificar melhor erros no código gerado.</span><span class="sxs-lookup"><span data-stu-id="ede55-149">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="ede55-150">Para obter informações sobre como habilitar ou desabilitar esse recurso, consulte [navegar pelo código com o depurador](https://msdn.microsoft.com/library/y740d9d3.aspx).</span><span class="sxs-lookup"><span data-stu-id="ede55-150">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](https://msdn.microsoft.com/library/y740d9d3.aspx).</span></span> <span data-ttu-id="ede55-151">Além disso, você também pode definir exceções de primeira chance capturando abrindo o `Debug` menu e, em seguida, escolhendo `Exceptions` ou escolhendo as teclas Ctrl + Alt + E para abrir o `Exceptions` caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ede55-151">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="ede55-152">Na caixa de diálogo, em `Common Language Runtime Exceptions`, selecione o `Thrown` caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="ede55-152">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="ede55-153">Implementação do provedor de tipo</span><span class="sxs-lookup"><span data-stu-id="ede55-153">Implementation of the Type Provider</span></span>
<span data-ttu-id="ede55-154">Esta seção orienta você pelas seções principais da implementação do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-154">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="ede55-155">Primeiro, você define o tipo para o provedor de tipo personalizado próprio:</span><span class="sxs-lookup"><span data-stu-id="ede55-155">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="ede55-156">Esse tipo deve ser público e você deve marcar com o [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) para que o compilador reconhecerá o provedor de tipo quando um projeto separado de F # referencia o assembly que contém o tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="ede55-156">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="ede55-157">O *config* parâmetro é opcional e, se presente, contém informações de configuração contextual para a instância do provedor de tipo que cria o compilador F #.</span><span class="sxs-lookup"><span data-stu-id="ede55-157">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="ede55-158">Em seguida, você implementa o [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span><span class="sxs-lookup"><span data-stu-id="ede55-158">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="ede55-159">Nesse caso, você usa o `TypeProviderForNamespaces` tipo o `ProvidedTypes` API como um tipo base.</span><span class="sxs-lookup"><span data-stu-id="ede55-159">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="ede55-160">Esse tipo de auxiliar pode fornecer um conjunto finito de ansiosamente fornecida namespaces, diretamente, cada uma delas contém um número finito de fixo, ansiosamente tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-160">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="ede55-161">Nesse contexto, o provedor *ansiosamente* gera tipos, mesmo se eles não são necessários ou usados.</span><span class="sxs-lookup"><span data-stu-id="ede55-161">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces()
```

<span data-ttu-id="ede55-162">Em seguida, definir valores particulares locais que especifique o namespace para os tipos fornecidos e localizar o assembly do provedor de tipo em si.</span><span class="sxs-lookup"><span data-stu-id="ede55-162">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="ede55-163">Este assembly é usado posteriormente como o tipo de pai lógico dos tipos apagados que são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-163">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="ede55-164">Em seguida, crie uma função para fornecer a cada um dos tipos Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="ede55-164">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="ede55-165">Essa função é explicada em mais detalhes posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-165">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="ede55-166">Em seguida, gere os 100 tipos fornecidos:</span><span class="sxs-lookup"><span data-stu-id="ede55-166">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="ede55-167">Em seguida, adicione os tipos de um namespace fornecido:</span><span class="sxs-lookup"><span data-stu-id="ede55-167">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="ede55-168">Finalmente, adicione um atributo de assembly que indica que você está criando uma DLL de provedor do tipo:</span><span class="sxs-lookup"><span data-stu-id="ede55-168">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="ede55-169">Fornecendo um tipo e seus membros</span><span class="sxs-lookup"><span data-stu-id="ede55-169">Providing One Type And Its Members</span></span>
<span data-ttu-id="ede55-170">O `makeOneProvidedType` função faz o trabalho real do fornecimento de um dos tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-170">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="ede55-171">Esta etapa explica a implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="ede55-171">This step explains the implementation of this function.</span></span> <span data-ttu-id="ede55-172">Primeiro, crie o tipo fornecido (por exemplo, Type1, quando n = 1 ou Type57, quando n = 57).</span><span class="sxs-lookup"><span data-stu-id="ede55-172">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

<span data-ttu-id="ede55-173">Você deve observar os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="ede55-173">You should note the following points:</span></span>


- <span data-ttu-id="ede55-174">Isso fornecido o tipo é apagado.</span><span class="sxs-lookup"><span data-stu-id="ede55-174">This provided type is erased.</span></span>  <span data-ttu-id="ede55-175">Porque você indicar que o tipo base é `obj`, instâncias serão exibidos como valores do tipo [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) no código compilado.</span><span class="sxs-lookup"><span data-stu-id="ede55-175">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>
<br />

- <span data-ttu-id="ede55-176">Quando você especifica um tipo aninhado não, você deve especificar o assembly e o namespace.</span><span class="sxs-lookup"><span data-stu-id="ede55-176">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="ede55-177">Para tipos apagados, o assembly deve ser o assembly do provedor de tipo em si.</span><span class="sxs-lookup"><span data-stu-id="ede55-177">For erased types, the assembly should be the type provider assembly itself.</span></span>
<br />

<span data-ttu-id="ede55-178">Em seguida, adicione a documentação XML para o tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-178">Next, add XML documentation to the type.</span></span> <span data-ttu-id="ede55-179">Esta documentação está atrasada, ou seja, computados sob demanda, se o compilador host necessitar.</span><span class="sxs-lookup"><span data-stu-id="ede55-179">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="ede55-180">Em seguida, você adiciona uma propriedade de estática fornecida para o tipo:</span><span class="sxs-lookup"><span data-stu-id="ede55-180">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="ede55-181">Obter esta propriedade será sempre avaliada como a cadeia de caracteres "Olá!".</span><span class="sxs-lookup"><span data-stu-id="ede55-181">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="ede55-182">O `GetterCode` para a propriedade usa uma cotação F #, que representa o código que gera o compilador de host para a obtenção da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ede55-182">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="ede55-183">Para obter mais informações sobre cotações, consulte [citações de código (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="ede55-183">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="ede55-184">Adicione documentação XML para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ede55-184">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="ede55-185">Agora, anexe a propriedade fornecida para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-185">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="ede55-186">Você deve anexar um membro fornecido para apenas um tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-186">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="ede55-187">Caso contrário, o membro nunca poderá ser acessado.</span><span class="sxs-lookup"><span data-stu-id="ede55-187">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="ede55-188">Agora, crie um construtor fornecido sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ede55-188">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="ede55-189">O `InvokeCode` para o construtor retorna uma cotação F #, que representa o código que o compilador host gera quando o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="ede55-189">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="ede55-190">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="ede55-190">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="ede55-191">Uma instância do tipo fornecido será criada com os dados subjacentes "Os dados do objeto".</span><span class="sxs-lookup"><span data-stu-id="ede55-191">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="ede55-192">O código entre aspas inclui uma conversão [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) porque esse tipo é a eliminação de tipo isso fornecido (conforme especificado quando você declarou o tipo fornecido).</span><span class="sxs-lookup"><span data-stu-id="ede55-192">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="ede55-193">Adicionar a documentação XML para o construtor e, em seguida, adicione o construtor fornecido para o tipo fornecido:</span><span class="sxs-lookup"><span data-stu-id="ede55-193">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="ede55-194">Crie um segundo construtor fornecido que recebe um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="ede55-194">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="ede55-195">O `InvokeCode` para o construtor novamente retorna uma cotação F #, que representa o código que o compilador host gerado para uma chamada ao método.</span><span class="sxs-lookup"><span data-stu-id="ede55-195">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="ede55-196">Por exemplo, você pode usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="ede55-196">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="ede55-197">Uma instância do tipo fornecido é criada com os dados subjacentes "10".</span><span class="sxs-lookup"><span data-stu-id="ede55-197">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="ede55-198">Você já deve ter notado que o `InvokeCode` função retorna uma citação.</span><span class="sxs-lookup"><span data-stu-id="ede55-198">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="ede55-199">A entrada para esta função é uma lista de expressões, um por um parâmetro de construtor.</span><span class="sxs-lookup"><span data-stu-id="ede55-199">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="ede55-200">Nesse caso, uma expressão que representa o valor do parâmetro único está disponível em `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="ede55-200">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="ede55-201">O código para chamar o construtor converte o valor de retorno para o tipo apagado `obj`.</span><span class="sxs-lookup"><span data-stu-id="ede55-201">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="ede55-202">Depois de adicionar o segundo construtor fornecido para o tipo, você pode criar uma propriedade de instância fornecida:</span><span class="sxs-lookup"><span data-stu-id="ede55-202">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="ede55-203">Obter esta propriedade retornará o comprimento da cadeia de caracteres, que é o objeto de representação.</span><span class="sxs-lookup"><span data-stu-id="ede55-203">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="ede55-204">O `GetterCode` propriedade retorna uma cotação de F # que especifica o código que gera o compilador de host para obter a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ede55-204">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="ede55-205">Como `InvokeCode`, o `GetterCode` função retorna uma citação.</span><span class="sxs-lookup"><span data-stu-id="ede55-205">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="ede55-206">O compilador de host chama essa função com uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="ede55-206">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="ede55-207">Nesse caso, os argumentos incluem a expressão único que representa a instância na qual está sendo chamado getter, que pode ser acessado usando `args.[0]`. A implementação de `GetterCode` une em aspas o resultado no tipo apagado `obj`, e uma conversão é usada para satisfazer o mecanismo do compilador para verificar os tipos de objeto é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ede55-207">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="ede55-208">A próxima parte do `makeOneProvidedType` fornece um método de instância com um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ede55-208">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="ede55-209">Finalmente, crie um tipo aninhado que contém as propriedades aninhadas 100.</span><span class="sxs-lookup"><span data-stu-id="ede55-209">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="ede55-210">A criação deste aninhados tipo e suas propriedades estiver atrasada, ou seja, computados sob demanda.</span><span class="sxs-lookup"><span data-stu-id="ede55-210">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="ede55-211">Detalhes sobre tipos fornecidos apagados</span><span class="sxs-lookup"><span data-stu-id="ede55-211">Details about Erased Provided Types</span></span>
<span data-ttu-id="ede55-212">O exemplo nesta seção fornece apenas *apagados tipos fornecidos*, que são particularmente úteis nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="ede55-212">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>


- <span data-ttu-id="ede55-213">Quando você estiver escrevendo um provedor para um espaço de informações que contém somente os dados e métodos.</span><span class="sxs-lookup"><span data-stu-id="ede55-213">When you are writing a provider for an information space that contains only data and methods.</span></span>
<br />

- <span data-ttu-id="ede55-214">Quando você estiver escrevendo um provedor onde semântica precisa de tipo de tempo de execução não é essencial para o uso prático do espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="ede55-214">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>
<br />

- <span data-ttu-id="ede55-215">Quando você estiver escrevendo um provedor para um espaço de informações é tão grande e interconectadas que não seja tecnicamente possível gerar tipos .NET reais para o espaço de informações.</span><span class="sxs-lookup"><span data-stu-id="ede55-215">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>
<br />

<span data-ttu-id="ede55-216">Neste exemplo, cada fornecida tipo será apagado para o tipo `obj`, e todos os usos do tipo aparecerão como tipo `obj` no código compilado.</span><span class="sxs-lookup"><span data-stu-id="ede55-216">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="ede55-217">Na verdade, os objetos subjacentes nesses exemplos são cadeias de caracteres, mas o tipo será exibido como `System.Object` no .NET código compilado.</span><span class="sxs-lookup"><span data-stu-id="ede55-217">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="ede55-218">Como com todos os usos de eliminação de tipo, você pode usar a conversão explícita, unboxing e conversão de subverter apagados tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-218">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="ede55-219">Nesse caso, uma exceção de conversão não é válida pode resultar quando o objeto é usado.</span><span class="sxs-lookup"><span data-stu-id="ede55-219">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="ede55-220">Um provedor de tempo de execução pode definir seu próprio tipo de representação privada para ajudar a proteger contra representações falsas.</span><span class="sxs-lookup"><span data-stu-id="ede55-220">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="ede55-221">Você não pode definir tipos apagados em F # em si.</span><span class="sxs-lookup"><span data-stu-id="ede55-221">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="ede55-222">Apenas tipos fornecidos poderão ser apagados.</span><span class="sxs-lookup"><span data-stu-id="ede55-222">Only provided types may be erased.</span></span> <span data-ttu-id="ede55-223">Você deve entender as implicações, ambas as práticas e apagados apagados tipos para o provedor de tipo ou um provedor que fornece semântica, usando um tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-223">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="ede55-224">Um tipo apagado não tem nenhum tipo real do .NET.</span><span class="sxs-lookup"><span data-stu-id="ede55-224">An erased type has no real .NET type.</span></span> <span data-ttu-id="ede55-225">Portanto, não é possível fazer o reflexo preciso sobre o tipo e você pode subverter tipos apagados se você usar outras técnicas que dependem de semântica do tipo de tempo de execução exata e conversões de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ede55-225">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="ede55-226">Subversão dos tipos apagados frequentemente resulta em exceções de conversão de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ede55-226">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="ede55-227">Escolher representações para apagados fornecido tipos</span><span class="sxs-lookup"><span data-stu-id="ede55-227">Choosing Representations for Erased Provided Types</span></span>
<span data-ttu-id="ede55-228">Para alguns usos de tipos fornecidos apagados, nenhuma representação é necessária.</span><span class="sxs-lookup"><span data-stu-id="ede55-228">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="ede55-229">Por exemplo, o apagados fornecido tipo pode conter apenas as propriedades estáticas e membros e nenhum construtor e sem propriedades ou métodos retorna uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-229">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="ede55-230">Se você pode acessar instâncias de um apagados tipo fornecido, você deve considerar as seguintes perguntas:</span><span class="sxs-lookup"><span data-stu-id="ede55-230">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>


- <span data-ttu-id="ede55-231">O que é a eliminação de um tipo fornecido?</span><span class="sxs-lookup"><span data-stu-id="ede55-231">What is the erasure of a provided type?</span></span>
<br />
  - <span data-ttu-id="ede55-232">A eliminação de um tipo fornecido é como o tipo é exibido no código compilado do .NET.</span><span class="sxs-lookup"><span data-stu-id="ede55-232">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>
<br />

  - <span data-ttu-id="ede55-233">A eliminação de um tipo de classe apagados fornecido é sempre o primeiro não apagados tipo base na cadeia de herança do tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-233">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>
<br />

  - <span data-ttu-id="ede55-234">A eliminação de um tipo de interface apagados fornecida é sempre `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="ede55-234">The erasure of a provided erased interface type is always `System.Object`.</span></span>
<br />

- <span data-ttu-id="ede55-235">Quais são as representações de um tipo fornecido?</span><span class="sxs-lookup"><span data-stu-id="ede55-235">What are the representations of a provided type?</span></span>
<br />
  - <span data-ttu-id="ede55-236">O conjunto de objetos possíveis para um tipo fornecido apagados são chamados de suas representações.</span><span class="sxs-lookup"><span data-stu-id="ede55-236">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="ede55-237">O exemplo neste documento, as representações de todos os fornecidos o apagados tipos `Type1..Type100` sempre são objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ede55-237">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>
<br />

<span data-ttu-id="ede55-238">Todas as representações de um tipo fornecido devem ser compatíveis com a eliminação do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-238">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="ede55-239">(Caso contrário, o compilador F # fornecerão um erro para uso do provedor de tipo, ou será gerado o código .NET não verificado que não é válido.</span><span class="sxs-lookup"><span data-stu-id="ede55-239">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="ede55-240">Um provedor de tipo não é válido se ele retorna o código que fornece uma representação que não é válida.)</span><span class="sxs-lookup"><span data-stu-id="ede55-240">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="ede55-241">Você pode escolher uma representação para objetos fornecidos usando qualquer um dos procedimentos a seguir, que são muito comuns:</span><span class="sxs-lookup"><span data-stu-id="ede55-241">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>


- <span data-ttu-id="ede55-242">Se você simplesmente fornece um wrapper com rigidez de tipos em um tipo .NET existente, geralmente faz sentido para o seu tipo apagar a esse tipo, use instâncias desse tipo como representações, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="ede55-242">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="ede55-243">Essa abordagem é apropriada quando a maioria dos métodos existentes no tipo ainda faz sentido ao usar a versão fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="ede55-243">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>
<br />

- <span data-ttu-id="ede55-244">Se você quiser criar uma API que difere significativamente da API .NET existentes, faz sentido criar tipos de tempo de execução serão a eliminação de tipo e representações para os tipos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-244">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>
<br />

<span data-ttu-id="ede55-245">O exemplo neste documento usa cadeias de caracteres como representações de objetos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-245">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="ede55-246">Com frequência, é apropriado usar outros objetos para representações.</span><span class="sxs-lookup"><span data-stu-id="ede55-246">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="ede55-247">Por exemplo, você pode usar um dicionário como um recipiente de propriedades:</span><span class="sxs-lookup"><span data-stu-id="ede55-247">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="ede55-248">Como alternativa, você pode definir um tipo no seu provedor de tipo que será usado em tempo de execução para formar a representação, juntamente com uma ou mais operações de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="ede55-248">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="ede55-249">Membros fornecidos, em seguida, podem construir instâncias deste tipo de objeto:</span><span class="sxs-lookup"><span data-stu-id="ede55-249">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="ede55-250">(Nesse caso, você pode opcionalmente) use esse tipo como a eliminação de tipo ao especificar esse tipo como o `baseType` ao construir o `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="ede55-250">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

<span data-ttu-id="ede55-251">A seção anterior explicou como criar um provedor de tipo apagar simples que fornece uma variedade de tipos, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="ede55-251">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="ede55-252">Esta seção também explicado o conceito de eliminação de tipo, incluindo algumas das vantagens e desvantagens de fornecer tipos apagados de um provedor de tipo e discutido representações de tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="ede55-252">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="ede55-253">Um provedor de tipo que usa parâmetros estáticos</span><span class="sxs-lookup"><span data-stu-id="ede55-253">A Type Provider That Uses Static Parameters</span></span>
<span data-ttu-id="ede55-254">A capacidade de parametrizar os provedores de tipos por dados estáticos permite muitos cenários interessantes, mesmo em casos em que o provedor não precisa acessar os dados locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="ede55-254">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="ede55-255">Nesta seção, você aprenderá algumas técnicas básicas de reunir esse provedor.</span><span class="sxs-lookup"><span data-stu-id="ede55-255">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="ede55-256">Tipo verificado provedor Regex</span><span class="sxs-lookup"><span data-stu-id="ede55-256">Type Checked Regex Provider</span></span>
<span data-ttu-id="ede55-257">Imagine que você deseja implementar um provedor de tipos de expressões regulares que encapsula o .NET `System.Text.RegularExpressions.Regex` bibliotecas em uma interface que fornece as seguintes garantias do tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="ede55-257">Imagine that you want to implement a type provider for regular expressions that wraps the .NET `System.Text.RegularExpressions.Regex` libraries in an interface that provides the following compile-time guarantees:</span></span>


- <span data-ttu-id="ede55-258">Verificando se uma expressão regular é válida.</span><span class="sxs-lookup"><span data-stu-id="ede55-258">Verifying whether a regular expression is valid.</span></span>
<br />

- <span data-ttu-id="ede55-259">Fornecendo propriedades nomeadas em correspondências com base em quaisquer nomes de grupo na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="ede55-259">Providing named properties on matches that are based on any group names in the regular expression.</span></span>
<br />

<span data-ttu-id="ede55-260">Esta seção mostra como usar provedores de tipos para criar um `RegExProviderType` tipo que o padrão de expressão regular parametriza para fornecer esses benefícios.</span><span class="sxs-lookup"><span data-stu-id="ede55-260">This section shows you how to use type providers to create a `RegExProviderType` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="ede55-261">O compilador relatará um erro se o padrão fornecido não é válido, e o provedor de tipo pode extrair os grupos do padrão para que você pode acessá-los usando propriedades de correspondências nomeados.</span><span class="sxs-lookup"><span data-stu-id="ede55-261">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="ede55-262">Quando você cria um provedor de tipos, você deve considerar deve ser a aparência de sua API exposto aos usuários finais e como esse design se traduzirá em código .NET.</span><span class="sxs-lookup"><span data-stu-id="ede55-262">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="ede55-263">O exemplo a seguir mostra como usar esse uma API para obter os componentes do código de área:</span><span class="sxs-lookup"><span data-stu-id="ede55-263">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="ede55-264">O exemplo a seguir mostra como o provedor de tipos converte essas chamadas:</span><span class="sxs-lookup"><span data-stu-id="ede55-264">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="ede55-265">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="ede55-265">Note the following points:</span></span>


- <span data-ttu-id="ede55-266">O tipo padrão de Regex representa o parametrizadas `RegexTyped` tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-266">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>
<br />

- <span data-ttu-id="ede55-267">O `RegexTyped` construtor resulta em uma chamada para o construtor de Regex, passando o argumento de tipo estático para o padrão.</span><span class="sxs-lookup"><span data-stu-id="ede55-267">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>
<br />

- <span data-ttu-id="ede55-268">Os resultados de `Match` método são representados pelo padrão `System.Text.RegularExpressions.Match` tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-268">The results of the `Match` method are represented by the standard `System.Text.RegularExpressions.Match` type.</span></span>
<br />

- <span data-ttu-id="ede55-269">Cada grupo denominado resulta em uma propriedade fornecida e acessar a propriedade resulta em um uso de um indexador em uma correspondência `Groups` coleção.</span><span class="sxs-lookup"><span data-stu-id="ede55-269">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>
<br />

<span data-ttu-id="ede55-270">O código a seguir é o núcleo da lógica de implementar esse provedor, e este exemplo omite a adição de todos os membros para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-270">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="ede55-271">Para obter informações sobre cada membro adicionado, consulte a seção apropriada mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-271">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="ede55-272">Para o código completo, baixe o exemplo da [pacote de exemplo do F # 3.0](http://fsharp3sample.codeplex.com) no site da Codeplex.</span><span class="sxs-lookup"><span data-stu-id="ede55-272">For the full code, download the sample from the [F# 3.0 Sample Pack](http://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
inherit TypeProviderForNamespaces()

// Get the assembly and namespace used to house the provided types
let thisAssembly = Assembly.GetExecutingAssembly()
let rootNamespace = "Samples.FSharp.RegexTypeProvider"
let baseTy = typeof<obj>
let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

do regexTy.DefineStaticParameters(
parameters=staticParams, 
instantiationFunction=(fun typeName parameterValues ->

match parameterValues with 
| [| :? string as pattern|] -> 
// Create an instance of the regular expression. 
//
// This will fail with System.ArgumentException if the regular expression is not valid. 
// The exception will escape the type provider and be reported in client code.
let r = System.Text.RegularExpressions.Regex(pattern)            

// Declare the typed regex provided type.
// The type erasure of this type is 'obj', even though the representation will always be a Regex
// This, combined with hiding the object methods, makes the IntelliSense experience simpler.
let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

...

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="ede55-273">Observe os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="ede55-273">Note the following points:</span></span>


- <span data-ttu-id="ede55-274">O provedor de tipo utiliza dois parâmetros estáticos: o `pattern`, que é obrigatório e o `options`, que são opcional (como um valor padrão é fornecido).</span><span class="sxs-lookup"><span data-stu-id="ede55-274">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>
<br />

- <span data-ttu-id="ede55-275">Depois que os argumentos estáticos são fornecidos, você cria uma instância da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="ede55-275">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="ede55-276">Esta instância lançará uma exceção se a Regex está mal formado, e esse erro será relatado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="ede55-276">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>
<br />

- <span data-ttu-id="ede55-277">Dentro de `DefineStaticParameters` retorno de chamada, você define o tipo que será retornado após os argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-277">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>
<br />

- <span data-ttu-id="ede55-278">Esse código define `HideObjectMethods` como verdadeiro para que a experiência IntelliSense permanecerá simplificada.</span><span class="sxs-lookup"><span data-stu-id="ede55-278">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="ede55-279">Esse atributo faz com que o `Equals`, `GetHashCode`, `Finalize`, e `GetType` membros a serem suprimidos de listas do IntelliSense para um objeto fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-279">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>
<br />

- <span data-ttu-id="ede55-280">Você usa `obj` como o tipo base do método, mas você usará uma `Regex` objeto como a representação de tempo de execução desse tipo, como mostra o exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="ede55-280">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>
<br />

- <span data-ttu-id="ede55-281">A chamada para o `Regex` construtor lança um `System.ArgumentException` quando uma expressão regular não é válida.</span><span class="sxs-lookup"><span data-stu-id="ede55-281">The call to the `Regex` constructor throws a `System.ArgumentException` when a regular expression isn’t valid.</span></span> <span data-ttu-id="ede55-282">O compilador captura essa exceção e reportará uma mensagem de erro para o usuário em tempo de compilação ou no editor do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ede55-282">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="ede55-283">Essa exceção permite que as expressões regulares a ser validado sem executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ede55-283">This exception enables regular expressions to be validated without running an application.</span></span>
<br />

<span data-ttu-id="ede55-284">O tipo definido acima ainda não está útil porque ele não contém quaisquer propriedades ou métodos significativos.</span><span class="sxs-lookup"><span data-stu-id="ede55-284">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="ede55-285">Primeiro, adicione um estático `IsMatch` método:</span><span class="sxs-lookup"><span data-stu-id="ede55-285">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

<span data-ttu-id="ede55-286">O código anterior define um método `IsMatch`, que usa uma cadeia de caracteres como entrada e retorna um `bool`.</span><span class="sxs-lookup"><span data-stu-id="ede55-286">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="ede55-287">A única parte complicada é o uso do `args` argumento dentro de `InvokeCode` definição.</span><span class="sxs-lookup"><span data-stu-id="ede55-287">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="ede55-288">Neste exemplo, `args` é uma lista de aspas que representa os argumentos para esse método.</span><span class="sxs-lookup"><span data-stu-id="ede55-288">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="ede55-289">Se o método é um método de instância, o primeiro argumento representa o `this` argumento.</span><span class="sxs-lookup"><span data-stu-id="ede55-289">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="ede55-290">No entanto, para um método estático, os argumentos são todos apenas os argumentos explícitos para o método.</span><span class="sxs-lookup"><span data-stu-id="ede55-290">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="ede55-291">Observe que o tipo do valor entre aspas deve corresponder ao tipo de retorno especificado (nesse caso, `bool`).</span><span class="sxs-lookup"><span data-stu-id="ede55-291">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="ede55-292">Observe também que esse código usa o `AddXmlDoc` método para certificar-se de que o método fornecido também possui documentação útil que você pode fornecer por meio do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ede55-292">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="ede55-293">Em seguida, adicione uma instância de método de correspondência.</span><span class="sxs-lookup"><span data-stu-id="ede55-293">Next, add an instance Match method.</span></span> <span data-ttu-id="ede55-294">No entanto, esse método deve retornar um valor de um fornecido `Match` tipo de forma que os grupos podem ser acessados de forma fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="ede55-294">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="ede55-295">Assim, você primeiro declarar a `Match` tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-295">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="ede55-296">Como esse tipo depende do padrão que foi fornecido como argumento estático, esse tipo deve estar aninhado dentro da definição de tipo com parâmetros:</span><span class="sxs-lookup"><span data-stu-id="ede55-296">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="ede55-297">Você, em seguida, adicionar uma propriedade para o tipo de correspondência para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="ede55-297">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="ede55-298">Em tempo de execução, uma correspondência é representada como um `System.Text.RegularExpressions.Match` valor, portanto, as aspas que define a propriedade devem usar o `System.Text.RegularExpressions.Match.Groups` propriedade para o grupo relevantes indexada.</span><span class="sxs-lookup"><span data-stu-id="ede55-298">At runtime, a match is represented as a `System.Text.RegularExpressions.Match` value, so the quotation that defines the property must use the `System.Text.RegularExpressions.Match.Groups` indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

<span data-ttu-id="ede55-299">Novamente, observe que você está adicionando documentação XML para a propriedade fornecida.</span><span class="sxs-lookup"><span data-stu-id="ede55-299">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="ede55-300">Observe também que uma propriedade pode ser lidos se um `GetterCode` função é fornecida, e a propriedade pode ser gravada se um `SetterCode` função é fornecida para a propriedade resultante é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="ede55-300">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="ede55-301">Agora você pode criar um método de instância que retorna um valor `Match` tipo:</span><span class="sxs-lookup"><span data-stu-id="ede55-301">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

<span data-ttu-id="ede55-302">Porque você está criando um método de instância, `args.[0]` representa o `RegexTyped` instância na qual o método está sendo chamado, e `args.[1]` é o argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="ede55-302">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="ede55-303">Por fim, forneça um construtor para que a instância do tipo fornecido pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="ede55-303">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="ede55-304">Simplesmente apaga o construtor para a criação de uma instância de Regex .NET padrão, que é convertida novamente para um objeto porque `obj` é a eliminação do tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-304">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="ede55-305">Com essa alteração, o exemplo de uso de API especificado anteriormente no tópico funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="ede55-305">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="ede55-306">O código a seguir é concluída e final:</span><span class="sxs-lookup"><span data-stu-id="ede55-306">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
inherit TypeProviderForNamespaces()

// Get the assembly and namespace used to house the provided types.
let thisAssembly = Assembly.GetExecutingAssembly()
let rootNamespace = "Samples.FSharp.RegexTypeProvider"
let baseTy = typeof<obj>
let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

do regexTy.DefineStaticParameters(
parameters=staticParams, 
instantiationFunction=(fun typeName parameterValues ->

match parameterValues with 
| [| :? string as pattern|] -> 
// Create an instance of the regular expression. 




let r = System.Text.RegularExpressions.Regex(pattern)            

// Declare the typed regex provided type.



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

<span data-ttu-id="ede55-307">Esta seção explica como criar um provedor de tipos que opera em seus parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="ede55-307">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="ede55-308">O provedor verifica se o parâmetro static e fornece operações com base em seu valor.</span><span class="sxs-lookup"><span data-stu-id="ede55-308">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="ede55-309">Um provedor de tipo que é apoiado por dados locais</span><span class="sxs-lookup"><span data-stu-id="ede55-309">A Type Provider That Is Backed By Local Data</span></span>
<span data-ttu-id="ede55-310">Com frequência, convém provedores de tipo para apresentar as APIs com base em não apenas parâmetros estáticos, mas também informações de sistemas locais ou remotos.</span><span class="sxs-lookup"><span data-stu-id="ede55-310">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="ede55-311">Esta seção discute os provedores de tipos que se baseiam em dados locais, como arquivos de dados locais.</span><span class="sxs-lookup"><span data-stu-id="ede55-311">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="ede55-312">Provedor de arquivo CSV simples</span><span class="sxs-lookup"><span data-stu-id="ede55-312">Simple CSV File Provider</span></span>
<span data-ttu-id="ede55-313">Como um exemplo simples, considere um provedor de tipo para acessar dados científicos no formato de valor separado por vírgula (CSV).</span><span class="sxs-lookup"><span data-stu-id="ede55-313">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="ede55-314">Esta seção pressupõe que os arquivos CSV contém uma linha de cabeçalho seguida pelos dados de ponto flutuante, como mostra a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-314">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>



|<span data-ttu-id="ede55-315">Distância (medidor)</span><span class="sxs-lookup"><span data-stu-id="ede55-315">Distance (meter)</span></span>|<span data-ttu-id="ede55-316">Hora (segundos)</span><span class="sxs-lookup"><span data-stu-id="ede55-316">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="ede55-317">50.0</span><span class="sxs-lookup"><span data-stu-id="ede55-317">50.0</span></span>|<span data-ttu-id="ede55-318">3.7</span><span class="sxs-lookup"><span data-stu-id="ede55-318">3.7</span></span>|
|<span data-ttu-id="ede55-319">100.0</span><span class="sxs-lookup"><span data-stu-id="ede55-319">100.0</span></span>|<span data-ttu-id="ede55-320">5.2</span><span class="sxs-lookup"><span data-stu-id="ede55-320">5.2</span></span>|
|<span data-ttu-id="ede55-321">150.0</span><span class="sxs-lookup"><span data-stu-id="ede55-321">150.0</span></span>|<span data-ttu-id="ede55-322">6.4</span><span class="sxs-lookup"><span data-stu-id="ede55-322">6.4</span></span>|
<span data-ttu-id="ede55-323">Esta seção mostra como fornecer um tipo que você pode usar para obter as linhas com um `Distance` propriedade do tipo `float<meter>` e um `Time` propriedade do tipo `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="ede55-323">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="ede55-324">Para simplificar, as seguintes suposições são feitas:</span><span class="sxs-lookup"><span data-stu-id="ede55-324">For simplicity, the following assumptions are made:</span></span>


- <span data-ttu-id="ede55-325">Nomes de cabeçalho são sem unidade ou ter o formato "Nome (unidade)" e não conter vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ede55-325">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>
<br />

- <span data-ttu-id="ede55-326">As unidades são todas as unidades de Systeme internacional (SI) como o [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames módulo (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) módulo define.</span><span class="sxs-lookup"><span data-stu-id="ede55-326">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>
<br />

- <span data-ttu-id="ede55-327">As unidades são todos simples (por exemplo, monitorar) em vez de composta (por exemplo, o medidor/segundo).</span><span class="sxs-lookup"><span data-stu-id="ede55-327">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>
<br />

- <span data-ttu-id="ede55-328">Todas as colunas contêm dados de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="ede55-328">All columns contain floating point data.</span></span>
<br />

<span data-ttu-id="ede55-329">Um provedor mais completo seria solte essas restrições.</span><span class="sxs-lookup"><span data-stu-id="ede55-329">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="ede55-330">Novamente, a primeira etapa é considerar a aparência de API.</span><span class="sxs-lookup"><span data-stu-id="ede55-330">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="ede55-331">Dado um `info.csv` arquivo com o conteúdo da tabela anterior (no formato delimitado por vírgula), os usuários do provedor devem ser capazes de gravar o código semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-331">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="ede55-332">Nesse caso, o compilador deve converter essas chamadas em algo parecido com o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-332">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="ede55-333">A conversão ideal exigirá o provedor de tipo para definir um real `CsvFile` tipo no assembly do provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-333">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="ede55-334">Provedores de tipos geralmente dependem de alguns tipos de auxiliar e métodos para encapsular a lógica de importante.</span><span class="sxs-lookup"><span data-stu-id="ede55-334">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="ede55-335">Como as medidas são apagadas em tempo de execução, você pode usar um `float[]` como o tipo apagado para uma linha.</span><span class="sxs-lookup"><span data-stu-id="ede55-335">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="ede55-336">O compilador tratará colunas diferentes têm tipos de medida diferente.</span><span class="sxs-lookup"><span data-stu-id="ede55-336">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="ede55-337">Por exemplo, a primeira coluna em nosso exemplo tem tipo `float<meter>`, e o segundo tem `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="ede55-337">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="ede55-338">No entanto, a representação apagada pode permanecer muito simple.</span><span class="sxs-lookup"><span data-stu-id="ede55-338">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="ede55-339">O código a seguir mostra os principais da implementação.</span><span class="sxs-lookup"><span data-stu-id="ede55-339">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
// Cache the sequence of all data lines (all lines but the first)
let data = 
seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
yield line.Split(',') |> Array.map float }
|> Seq.cache
member __.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
inherit TypeProviderForNamespaces()

// Get the assembly and namespace used to house the provided types.
let asm = System.Reflection.Assembly.GetExecutingAssembly()
let ns = "Samples.FSharp.MiniCsvProvider"

// Create the main provided type.
let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

// Parameterize the type by the file to use as a template.
let filename = ProvidedStaticParameter("filename", typeof<string>)
do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

// Resolve the filename relative to the resolution folder.
let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

// Get the first line from the file.
let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

// Define a provided type for each row, erasing to a float[].
let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

// Extract header names from the file, splitting on commas.
// use Regex matching to get the position in the row at which the field occurs
let headers = Regex.Matches(headerLine, "[^,]+")

// Add one property per CSV field.
for i in 0 .. headers.Count - 1 do
let headerText = headers.[i].Value

// Try to decompose this header into a name and unit.
let fieldName, fieldTy =
let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
if m.Success then


let unitName = m.Groups.["unit"].Value
let units = ProvidedMeasureBuilder.Default.SI unitName
m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])


else
// no units, just treat it as a normal float
headerText, typeof<float>

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="ede55-340">Observe os seguintes pontos sobre a implementação:</span><span class="sxs-lookup"><span data-stu-id="ede55-340">Note the following points about the implementation:</span></span>


- <span data-ttu-id="ede55-341">Construtores sobrecarregados permitem que o arquivo original ou um que tenha um esquema idêntico a ser lido.</span><span class="sxs-lookup"><span data-stu-id="ede55-341">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="ede55-342">Esse padrão é comum quando você escrever um provedor de tipos de fontes de dados local ou remoto e esse padrão permite que um arquivo local a ser usado como o modelo de dados remotos.</span><span class="sxs-lookup"><span data-stu-id="ede55-342">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>
<br />  <span data-ttu-id="ede55-343">Você pode usar o [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) valor que é passado para o construtor do provedor de tipo para resolver nomes de arquivo relativo.</span><span class="sxs-lookup"><span data-stu-id="ede55-343">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>
<br />

- <span data-ttu-id="ede55-344">Você pode usar o `AddDefinitionLocation` método para definir o local das propriedades fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-344">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="ede55-345">Portanto, se você usar `Go To Definition` em uma propriedade fornecida, o arquivo CSV será aberto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ede55-345">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>
<br />

- <span data-ttu-id="ede55-346">Você pode usar o `ProvidedMeasureBuilder` tipo para pesquisar as unidades de SI e gerar relevante `float<_>` tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-346">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>
<br />

`Key Lessons`

<span data-ttu-id="ede55-347">Esta seção explica como criar um provedor de tipo para uma fonte de dados local com um esquema simple que está contido na fonte de dados em si.</span><span class="sxs-lookup"><span data-stu-id="ede55-347">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="ede55-348">Continuar</span><span class="sxs-lookup"><span data-stu-id="ede55-348">Going Further</span></span>
<span data-ttu-id="ede55-349">As seções a seguir incluem sugestões para estudar em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="ede55-349">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="ede55-350">Examinar o código compilado para tipos apagados</span><span class="sxs-lookup"><span data-stu-id="ede55-350">A Look at the Compiled Code for Erased Types</span></span>
<span data-ttu-id="ede55-351">Para dar uma ideia de como o uso do provedor de tipo corresponde ao código que é emitido, examine a seguinte função usando o `HelloWorldTypeProvider` que é usada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-351">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
obj1.InstanceProperty
```

<span data-ttu-id="ede55-352">Aqui está uma imagem do código resultante descompilado usando ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="ede55-352">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="ede55-353">Como mostra o exemplo, todos os menções do tipo `Type1` e `InstanceProperty` propriedade foi apagado, deixando apenas operações nos tipos de tempo de execução envolvidos.</span><span class="sxs-lookup"><span data-stu-id="ede55-353">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="ede55-354">Design e convenções de nomenclatura para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="ede55-354">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="ede55-355">Observe as convenções a seguir ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-355">Observe the following conventions when authoring type providers.</span></span>


- `Providers for Connectivity Protocols`
<br />  <span data-ttu-id="ede55-356">Em geral, os nomes de provedor a maioria das DLLs para protocolos de conectividade de dados e serviços, como conexões do OData ou SQL, devem terminar em `TypeProvider` ou `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="ede55-356">In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="ede55-357">Por exemplo, use um nome DLL que é semelhante a cadeia de caracteres a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-357">For example, use a DLL name that resembles the following string:</span></span>
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  <span data-ttu-id="ede55-358">Certifique-se de que seus tipos fornecidos são membros do namespace correspondente e indicam o protocolo de conectividade implementadas:</span><span class="sxs-lookup"><span data-stu-id="ede55-358">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  <span data-ttu-id="ede55-359">Para um provedor de tipos de utilitário como expressões regulares, o provedor de tipo pode ser parte de uma biblioteca de base, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-359">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  <span data-ttu-id="ede55-360">Nesse caso, o tipo fornecido apareceria em um ponto apropriado de acordo com as convenções de design normais .NET:</span><span class="sxs-lookup"><span data-stu-id="ede55-360">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  <span data-ttu-id="ede55-361">Alguns provedores de tipo se conectar a uma fonte de dados dedicado e fornecem apenas os dados.</span><span class="sxs-lookup"><span data-stu-id="ede55-361">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="ede55-362">Nesse caso, você deve descartar o `TypeProvider` sufixo e use normais convenções de nomenclatura do .NET:</span><span class="sxs-lookup"><span data-stu-id="ede55-362">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  <span data-ttu-id="ede55-363">Para obter mais informações, consulte o `GetConnection` design convenção é descrita posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ede55-363">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>
<br />


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="ede55-364">Padrões de design para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="ede55-364">Design Patterns for Type Providers</span></span>
<span data-ttu-id="ede55-365">As seções a seguir descrevem os padrões de design, que você pode usar ao criar provedores de tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-365">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="ede55-366">O padrão de Design de GetConnection</span><span class="sxs-lookup"><span data-stu-id="ede55-366">The GetConnection Design Pattern</span></span>
<span data-ttu-id="ede55-367">A maioria dos provedores de tipo deve ser gravado para usar o `GetConnection` padrão que é usado pelos provedores de tipo em FSharp.Data.TypeProviders.dll, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-367">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="ede55-368">Provedores de tipos com o apoio de serviços e dados remotos</span><span class="sxs-lookup"><span data-stu-id="ede55-368">Type Providers Backed By Remote Data and Services</span></span>
<span data-ttu-id="ede55-369">Antes de criar um provedor de tipo que é apoiado por serviços e dados remotos, você deve considerar uma variedade de problemas inerentes a programação conectada.</span><span class="sxs-lookup"><span data-stu-id="ede55-369">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="ede55-370">Esses problemas incluem as seguintes considerações:</span><span class="sxs-lookup"><span data-stu-id="ede55-370">These issues include the following considerations:</span></span>


- <span data-ttu-id="ede55-371">Mapeamento de esquema</span><span class="sxs-lookup"><span data-stu-id="ede55-371">schema mapping</span></span>
<br />

- <span data-ttu-id="ede55-372">alocação e invalidação na presença de alteração de esquema</span><span class="sxs-lookup"><span data-stu-id="ede55-372">liveness and invalidation in the presence of schema change</span></span>
<br />

- <span data-ttu-id="ede55-373">cache de esquemas</span><span class="sxs-lookup"><span data-stu-id="ede55-373">schema caching</span></span>
<br />

- <span data-ttu-id="ede55-374">implementações assíncronas de operações de acesso de dados</span><span class="sxs-lookup"><span data-stu-id="ede55-374">asynchronous implementations of data access operations</span></span>
<br />

- <span data-ttu-id="ede55-375">suporte a consultas, inclusive consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="ede55-375">supporting queries, including LINQ queries</span></span>
<br />

- <span data-ttu-id="ede55-376">autenticação e credenciais</span><span class="sxs-lookup"><span data-stu-id="ede55-376">credentials and authentication</span></span>
<br />

<span data-ttu-id="ede55-377">Este tópico não explorar ainda mais esses problemas.</span><span class="sxs-lookup"><span data-stu-id="ede55-377">This topic doesn't explore these issues further.</span></span>


### <a name="additional-authoring-techniques"></a><span data-ttu-id="ede55-378">Técnicas de criação adicionais</span><span class="sxs-lookup"><span data-stu-id="ede55-378">Additional Authoring Techniques</span></span>
<span data-ttu-id="ede55-379">Quando você escrever seus próprios provedores de tipo, você talvez queira usar as seguintes técnicas adicionais.</span><span class="sxs-lookup"><span data-stu-id="ede55-379">When you write your own type providers, you might want to use the following additional techniques.</span></span>


- `Creating Types and Members On-Demand`
<br />  <span data-ttu-id="ede55-380">A API ProvidedType adiou a versões do AddMember.</span><span class="sxs-lookup"><span data-stu-id="ede55-380">The ProvidedType API has delayed versions of AddMember.</span></span>
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  <span data-ttu-id="ede55-381">Essas versões são usadas para criar espaços de sob demanda de tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-381">These versions are used to create on-demand spaces of types.</span></span>
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  <span data-ttu-id="ede55-382">Tornar membros fornecidos (cujas assinaturas incluem tipos de matriz byref tipos e instâncias de tipos genéricos) usando o normal `MakeArrayType`, `MakePointerType`, e `MakeGenericType` em qualquer instância de System. Type, incluindo `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="ede55-382">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of System.Type, including `ProvidedTypeDefinitions`.</span></span>
<br />

- `Providing Unit of Measure Annotations`
<br />  <span data-ttu-id="ede55-383">A API ProvidedTypes fornece auxiliares para criar anotações de medida.</span><span class="sxs-lookup"><span data-stu-id="ede55-383">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="ede55-384">Por exemplo, para fornecer o tipo `float<kg>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ede55-384">For example, to provide the type `float<kg>`, use the following code:</span></span>
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="ede55-385">Para fornecer o tipo `Nullable<decimal<kg/m^2>>`, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ede55-385">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  <span data-ttu-id="ede55-386">Cada instância de um provedor de tipo pode ser fornecida um `TypeProviderConfig` valor durante a construção.</span><span class="sxs-lookup"><span data-stu-id="ede55-386">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="ede55-387">Esse valor contém a pasta"Resolução" para o provedor (ou seja, a pasta de projeto para a compilação ou o diretório que contém um script), a lista de assemblies referenciados e outras informações.</span><span class="sxs-lookup"><span data-stu-id="ede55-387">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>
<br />

- `Invalidation`
<br />  <span data-ttu-id="ede55-388">Provedores podem gerar sinais de invalidação para notificar o serviço de linguagem F # que as suposições de esquema podem ter sido alterado.</span><span class="sxs-lookup"><span data-stu-id="ede55-388">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="ede55-389">Quando ocorre a invalidação, um typecheck é refeito se o provedor está sendo hospedado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ede55-389">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="ede55-390">Este sinal será ignorado quando o provedor é hospedado em F # interativo ou pelo compilador F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="ede55-390">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>
<br />

- `Caching Schema Information`
<br />  <span data-ttu-id="ede55-391">Provedores geralmente devem armazenar em cache acesso às informações de esquema.</span><span class="sxs-lookup"><span data-stu-id="ede55-391">Providers must often cache access to schema information.</span></span> <span data-ttu-id="ede55-392">Os dados armazenados em cache devem ser armazenados usando um nome de arquivo que é fornecido como um parâmetro estático ou como dados de usuário.</span><span class="sxs-lookup"><span data-stu-id="ede55-392">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="ede55-393">Um exemplo de cache de esquema é o `LocalSchemaFile` os provedores de tipo no parâmetro de `FSharp.Data.TypeProviders` assembly.</span><span class="sxs-lookup"><span data-stu-id="ede55-393">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="ede55-394">A implementação desses provedores, esse parâmetro estático instrui o provedor de tipo para usar as informações de esquema no arquivo local especificado em vez de acessar a fonte de dados pela rede.</span><span class="sxs-lookup"><span data-stu-id="ede55-394">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="ede55-395">Para usar as informações de esquema em cache, você também deve definir o parâmetro static `ForceUpdate` para `false`.</span><span class="sxs-lookup"><span data-stu-id="ede55-395">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="ede55-396">Você pode usar uma técnica semelhante para habilitar o acesso de dados online e offline.</span><span class="sxs-lookup"><span data-stu-id="ede55-396">You could use a similar technique to enable online and offline data access.</span></span>
<br />

- `Backing Assembly`
<br />  <span data-ttu-id="ede55-397">Quando você compila um arquivo. dll ou .exe, o arquivo. dll de apoio para tipos gerados está estaticamente vinculado o assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="ede55-397">When you compile a .dll or .exe file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="ede55-398">Esse link é criado, copiando as definições de tipo de linguagem intermediária (IL) e todos os recursos gerenciados do conjunto de backup no assembly final.</span><span class="sxs-lookup"><span data-stu-id="ede55-398">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="ede55-399">Quando você usar o F # interativo, o arquivo. dll de backup não é copiado e em vez disso, é carregado diretamente no processo de F # interativo.</span><span class="sxs-lookup"><span data-stu-id="ede55-399">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  <span data-ttu-id="ede55-400">Todos os usos de todos os membros de tipos fornecidos podem ocasionar exceções.</span><span class="sxs-lookup"><span data-stu-id="ede55-400">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="ede55-401">Em todos os casos, se um provedor de tipo lança uma exceção, o compilador host atributos o erro para um provedor de tipo específico.</span><span class="sxs-lookup"><span data-stu-id="ede55-401">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>
<br />
  - <span data-ttu-id="ede55-402">Exceções de provedor de tipo nunca devem resultar em erros do compilador interno.</span><span class="sxs-lookup"><span data-stu-id="ede55-402">Type provider exceptions should never result in internal compiler errors.</span></span>
<br />

  - <span data-ttu-id="ede55-403">Provedores de tipos não podem relatar avisos.</span><span class="sxs-lookup"><span data-stu-id="ede55-403">Type providers can't report warnings.</span></span>
<br />

  - <span data-ttu-id="ede55-404">Quando um provedor de tipo é hospedado no compilador F #, um ambiente de desenvolvimento do F # ou F # interativo, todas as exceções do provedor são capturadas.</span><span class="sxs-lookup"><span data-stu-id="ede55-404">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="ede55-405">A propriedade de mensagem sempre é o texto de erro e nenhum rastreamento de pilha é exibida.</span><span class="sxs-lookup"><span data-stu-id="ede55-405">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="ede55-406">Se você vai lançar uma exceção, você pode lançar os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="ede55-406">If you’re going to throw an exception, you can throw the following examples:</span></span>
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a><span data-ttu-id="ede55-407">Fornece tipos gerados</span><span class="sxs-lookup"><span data-stu-id="ede55-407">Providing Generated Types</span></span>
<span data-ttu-id="ede55-408">Até agora, este documento explicou como fornecer tipos apagados.</span><span class="sxs-lookup"><span data-stu-id="ede55-408">So far, this document has explained how provide erased types.</span></span> <span data-ttu-id="ede55-409">Você também pode usar o mecanismo de provedor de tipo em F # para fornecer tipos gerados, que são adicionados como definições de tipo .NET reais no programa dos usuários.</span><span class="sxs-lookup"><span data-stu-id="ede55-409">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="ede55-410">Você deve se referir a gerado fornecida tipos usando uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-410">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="ede55-411">O código auxiliar 0,2 ProvidedTypes que faz parte da versão do F # 3.0 tem somente suporte limitado para fornecer tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="ede55-411">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="ede55-412">As instruções a seguir devem ser verdadeiras para uma definição de tipo gerado:</span><span class="sxs-lookup"><span data-stu-id="ede55-412">The following statements must be true for a generated type definition:</span></span>


- <span data-ttu-id="ede55-413">IsErased deve ser definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="ede55-413">IsErased must be set to `false`.</span></span>
<br />

- <span data-ttu-id="ede55-414">O provedor deve ter um assembly que tem um arquivo do backup real .NET. dll com um arquivo. dll correspondente no disco.</span><span class="sxs-lookup"><span data-stu-id="ede55-414">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>
<br />

<span data-ttu-id="ede55-415">Você também deve chamar `ConvertToGenerated` em um tipo de raiz fornecido cujos tipos aninhados formam um conjunto fechado de tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="ede55-415">You must also call `ConvertToGenerated` on a root provided type whose nested types form a closed set of generated types.</span></span> <span data-ttu-id="ede55-416">Essa chamada emite a definição de determinado tipo fornecido e suas definições de tipo aninhado em um assembly e ajusta a `Assembly` propriedade de todas as definições de tipo fornecido para retornar a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="ede55-416">This call emits the given provided type definition and its nested type definitions into an assembly and adjusts the `Assembly` property of all provided type definitions to return that assembly.</span></span> <span data-ttu-id="ede55-417">O assembly é emitido somente quando a propriedade do Assembly no tipo de raiz é acessada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ede55-417">The assembly is emitted only when the Assembly property on the root type is accessed for the first time.</span></span> <span data-ttu-id="ede55-418">O compilador F # host acessar essa propriedade quando ele processa uma declaração de tipo produtivas para o tipo.</span><span class="sxs-lookup"><span data-stu-id="ede55-418">The host F# compiler does access this property when it processes a generative type declaration for the type.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="ede55-419">Regras e limitações</span><span class="sxs-lookup"><span data-stu-id="ede55-419">Rules and Limitations</span></span>
<span data-ttu-id="ede55-420">Quando você escreve provedores de tipos, tenha as seguintes regras e limitações em mente.</span><span class="sxs-lookup"><span data-stu-id="ede55-420">When you write type providers, keep the following rules and limitations in mind.</span></span>


- `Provided types must be reachable.`
<br />  <span data-ttu-id="ede55-421">Todos os fornecidos tipos devem ser os tipos aninhados não pode ser acessados.</span><span class="sxs-lookup"><span data-stu-id="ede55-421">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="ede55-422">Os tipos aninhados não são fornecidos na chamada para o `TypeProviderForNamespaces` construtor ou uma chamada para `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="ede55-422">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="ede55-423">Por exemplo, se o provedor fornece um tipo `StaticClass.P : T`, certifique-se de que T é um tipo aninhado não ou aninhados em um.</span><span class="sxs-lookup"><span data-stu-id="ede55-423">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>
<br />  <span data-ttu-id="ede55-424">Por exemplo, alguns provedores têm uma classe estática, como `DataTypes` que contêm esses `T1, T2, T3, ...` tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-424">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="ede55-425">Caso contrário, o erro afirma que uma referência ao tipo T no assembly A foi encontrada, mas não foi possível encontrar o tipo nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="ede55-425">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="ede55-426">Se esse erro aparecer, verifique se todos os seus subtipos podem ser alcançados dos tipos de provedor.</span><span class="sxs-lookup"><span data-stu-id="ede55-426">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="ede55-427">Observação: Essas `T1, T2, T3...` tipos são denominados de *durante a execução* tipos.</span><span class="sxs-lookup"><span data-stu-id="ede55-427">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="ede55-428">Lembre-se de colocá-los em um namespace acessível ou um tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="ede55-428">Remember to put them in an accessible namespace or a parent type.</span></span>
<br />

- `Limitations of the Type Provider Mechanism`
<br />  <span data-ttu-id="ede55-429">O mecanismo de provedor de tipo em F # tem as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="ede55-429">The type provider mechanism in F# has the following limitations:</span></span>
<br />
  - <span data-ttu-id="ede55-430">A infraestrutura subjacente para provedores de tipos em F # não dá suporte a fornecida genérico tipos ou métodos genéricos de fornecido.</span><span class="sxs-lookup"><span data-stu-id="ede55-430">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>
<br />

  - <span data-ttu-id="ede55-431">O mecanismo não dá suporte a tipos aninhados com parâmetros estáticos.</span><span class="sxs-lookup"><span data-stu-id="ede55-431">The mechanism doesn't support nested types with static parameters.</span></span>
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  <span data-ttu-id="ede55-432">O `ProvidedTypes` código de suporte tem as seguintes regras e limitações:</span><span class="sxs-lookup"><span data-stu-id="ede55-432">The `ProvidedTypes` support code has the following rules and limitations:</span></span>
<br />
  1. <span data-ttu-id="ede55-433">As propriedades fornecidas com indexada getters e setters não são implementadas.</span><span class="sxs-lookup"><span data-stu-id="ede55-433">Provided properties with indexed getters and setters aren't implemented.</span></span>
<br />

  2. <span data-ttu-id="ede55-434">Os eventos fornecidos não são implementados.</span><span class="sxs-lookup"><span data-stu-id="ede55-434">Provided events aren't implemented.</span></span>
<br />

  3. <span data-ttu-id="ede55-435">Os objetos de informações e tipos fornecidos deve ser usada somente para o mecanismo de provedor de tipo em F #.</span><span class="sxs-lookup"><span data-stu-id="ede55-435">The provided types and information objects should be used only for the type provider mechanism in F#.</span></span> <span data-ttu-id="ede55-436">Eles não são mais amplamente utilizáveis como objetos System. Type.</span><span class="sxs-lookup"><span data-stu-id="ede55-436">They aren't more generally usable as System.Type objects.</span></span>
<br />

  4. <span data-ttu-id="ede55-437">As construções que você pode usar aspas que definem as implementações de método têm várias limitações.</span><span class="sxs-lookup"><span data-stu-id="ede55-437">The constructs that you can use in quotations that define method implementations have several limitations.</span></span> <span data-ttu-id="ede55-438">Você pode consultar o código-fonte para ProvidedTypes -*versão* para ver quais construções são suportadas com aspas.</span><span class="sxs-lookup"><span data-stu-id="ede55-438">You can refer to the source code for ProvidedTypes-*Version* to see which constructs are supported in quotations.</span></span>
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a><span data-ttu-id="ede55-439">Dicas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ede55-439">Development Tips</span></span>
<span data-ttu-id="ede55-440">Você pode encontrar as seguintes dicas úteis durante o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ede55-440">You might find the following tips helpful during the development process.</span></span>


- <span data-ttu-id="ede55-441">`Run Two Instances of Visual Studio.`Você pode desenvolver o provedor de tipo em uma instância e o provedor de teste nos outros porque o IDE de teste tem um bloqueio no arquivo. dll que impede que o provedor de tipo que está sendo recriado.</span><span class="sxs-lookup"><span data-stu-id="ede55-441">`Run Two Instances of Visual Studio.` You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="ede55-442">Portanto, você deve fechar a segunda instância do Visual Studio enquanto o provedor é criado na primeira ocorrência e, em seguida, você deverá reabri-la a segunda instância depois que o provedor for criado.</span><span class="sxs-lookup"><span data-stu-id="ede55-442">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>
<br />

- <span data-ttu-id="ede55-443">`Debug type providers by using invocations of fsc.exe.`Você pode chamar os provedores de tipos, usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="ede55-443">`Debug type providers by using invocations of fsc.exe.` You can invoke type providers by using the following tools:</span></span>
<br />
  - <span data-ttu-id="ede55-444">FSC.exe (compilador de linha de comando do F #)</span><span class="sxs-lookup"><span data-stu-id="ede55-444">fsc.exe (The F# command line compiler)</span></span>
<br />

  - <span data-ttu-id="ede55-445">FSI.exe (compilador o F # interativo)</span><span class="sxs-lookup"><span data-stu-id="ede55-445">fsi.exe (The F# Interactive compiler)</span></span>
<br />

  - <span data-ttu-id="ede55-446">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ede55-446">devenv.exe (Visual Studio)</span></span>
<br />

  <span data-ttu-id="ede55-447">Geralmente você pode depurar provedores de tipos mais facilmente usando fsc.exe em um arquivo de script de teste (por exemplo, script.fsx).</span><span class="sxs-lookup"><span data-stu-id="ede55-447">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="ede55-448">Você pode iniciar um depurador em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ede55-448">You can launch a debugger from a command prompt.</span></span>
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="ede55-449">Você pode usar o log de impressão para stdout.</span><span class="sxs-lookup"><span data-stu-id="ede55-449">You can use print-to-stdout logging.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="ede55-450">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ede55-450">See Also</span></span>
[<span data-ttu-id="ede55-451">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="ede55-451">Type Providers</span></span>](index.md)