---
title: "O que há de novo no c# 6 - guia c#"
description: "Aprenda os novos recursos da versão 6 do C#"
keywords: .NET, .NET Core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f3e7a515b1dde52461ab6abf8a9adbe84d27b7c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="e5181-104">Novidades no C# 6</span><span class="sxs-lookup"><span data-stu-id="e5181-104">What's New in C# 6</span></span>

<span data-ttu-id="e5181-105">A versão 6.0 do C# tinha muitos recursos para melhorar a produtividade para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="e5181-105">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="e5181-106">Os recursos nesta versão incluem:</span><span class="sxs-lookup"><span data-stu-id="e5181-106">Features in this release include:</span></span>

* <span data-ttu-id="e5181-107">[Propriedades automáticas somente leitura](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="e5181-107">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="e5181-108">Você pode criar propriedades automáticas somente leitura que podem ser definidas apenas em construtores.</span><span class="sxs-lookup"><span data-stu-id="e5181-108">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="e5181-109">[Inicializadores de propriedade automática](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="e5181-109">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="e5181-110">Você pode escrever expressões de inicialização para definir o valor inicial de uma propriedade automática.</span><span class="sxs-lookup"><span data-stu-id="e5181-110">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="e5181-111">[Membros de função aptos para expressão](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="e5181-111">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="e5181-112">Você pode criar métodos de uma linha usando expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="e5181-112">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="e5181-113">[using static](#using-static):</span><span class="sxs-lookup"><span data-stu-id="e5181-113">[using static](#using-static):</span></span>
    - <span data-ttu-id="e5181-114">Você pode importar todos os métodos de uma única classe para o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="e5181-114">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="e5181-115">[Null – operadores condicionais](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="e5181-115">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="e5181-116">Você pode acessar membros de um objeto com segurança e de forma concisa, durante a verificação de null, com o operador condicional null.</span><span class="sxs-lookup"><span data-stu-id="e5181-116">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="e5181-117">[Interpolação de cadeia de caracteres](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="e5181-117">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="e5181-118">Você pode escrever expressões de formatação de cadeias de caracteres, usando expressões embutidas em vez de argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="e5181-118">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="e5181-119">[Filtros de exceção](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="e5181-119">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="e5181-120">Você pode capturar expressões com base nas propriedades da exceção ou outro estado do programa.</span><span class="sxs-lookup"><span data-stu-id="e5181-120">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="e5181-121">[Expressões nameof](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="e5181-121">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="e5181-122">Você pode deixar que o compilador gere representações de cadeia de caracteres de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e5181-122">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="e5181-123">[await em blocos catch e finally](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="e5181-123">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="e5181-124">Você pode usar expressões `await` em locais que antes não era permitido.</span><span class="sxs-lookup"><span data-stu-id="e5181-124">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="e5181-125">[Inicializadores de índice](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="e5181-125">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="e5181-126">Você pode criar expressões de inicialização para contêineres associativos, bem como para contêineres de sequência.</span><span class="sxs-lookup"><span data-stu-id="e5181-126">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="e5181-127">[Métodos de extensão para inicializadores de coleção](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="e5181-127">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="e5181-128">Os inicializadores de coleção podem depender de métodos de extensão acessíveis, além dos métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="e5181-128">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="e5181-129">[Resolução de sobrecarga aprimorada](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="e5181-129">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="e5181-130">Alguns constructos, que antes geravam chamadas de método ambíguas, agora resolvem corretamente.</span><span class="sxs-lookup"><span data-stu-id="e5181-130">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="e5181-131">O efeito geral desses recursos é que você escreve código mais conciso e também mais legível.</span><span class="sxs-lookup"><span data-stu-id="e5181-131">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="e5181-132">A sintaxe contém menos cerimônia para várias práticas comuns.</span><span class="sxs-lookup"><span data-stu-id="e5181-132">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="e5181-133">É mais fácil de ver a intenção do design com menos cerimônia.</span><span class="sxs-lookup"><span data-stu-id="e5181-133">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="e5181-134">Aprenda bem esses recursos e você será mais produtivo, escreverá um código mais legível e se concentrará mais em seus recursos principais que nos constructos da linguagem.</span><span class="sxs-lookup"><span data-stu-id="e5181-134">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="e5181-135">O restante deste tópico fornece detalhes sobre cada um desses recursos.</span><span class="sxs-lookup"><span data-stu-id="e5181-135">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="e5181-136">Aprimoramentos de propriedade automática</span><span class="sxs-lookup"><span data-stu-id="e5181-136">Auto-Property enhancements</span></span> 

<span data-ttu-id="e5181-137">A sintaxe para propriedades implementadas automaticamente (geralmente conhecidas como 'propriedades automáticas ') facilitou muito a criação de propriedades que tinham acessadores simples get e set:</span><span class="sxs-lookup"><span data-stu-id="e5181-137">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="e5181-138">No entanto, essa sintaxe simplificada limitava os tipos de design que tinham suporte com o uso de propriedades automáticas.</span><span class="sxs-lookup"><span data-stu-id="e5181-138">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="e5181-139">O C# 6 aprimora os recursos das propriedades automáticas para que você possa usá-las em mais cenários.</span><span class="sxs-lookup"><span data-stu-id="e5181-139">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="e5181-140">Você não precisará voltar à sintaxe mais detalhada de declaração e manipulação do campo de suporte manualmente com tanta frequência.</span><span class="sxs-lookup"><span data-stu-id="e5181-140">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="e5181-141">A nova sintaxe abrange cenários para propriedades somente leitura e para inicializar o armazenamento de variável por trás de uma auto propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5181-141">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="e5181-142">Propriedades automáticas somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5181-142">Read-only auto-properties</span></span>

<span data-ttu-id="e5181-143">As *Propriedades automáticas somente leitura* fornecem uma sintaxe mais concisa para criar tipos imutáveis.</span><span class="sxs-lookup"><span data-stu-id="e5181-143">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="e5181-144">O mais próximo você chegava em relação a tipos imutáveis nas versões anteriores do C# era para declarar setters particulares:</span><span class="sxs-lookup"><span data-stu-id="e5181-144">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="e5181-145">Ao usar esta sintaxe, o compilador não garante que o tipo é realmente imutável.</span><span class="sxs-lookup"><span data-stu-id="e5181-145">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="e5181-146">Ele somente impõe que as propriedades `FirstName` e `LastName` não são modificadas de qualquer código fora da classe.</span><span class="sxs-lookup"><span data-stu-id="e5181-146">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="e5181-147">As propriedades automáticas somente leitura habilitam o verdadeiro comportamento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="e5181-147">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="e5181-148">Você declara a propriedade automática apenas com um acessador get:</span><span class="sxs-lookup"><span data-stu-id="e5181-148">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="e5181-149">As propriedades `FirstName` e `LastName` só podem ser definidas no corpo de um construtor:</span><span class="sxs-lookup"><span data-stu-id="e5181-149">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="e5181-150">A tentativa de definir `LastName` em outro método gera um erro de compilação `CS0200`:</span><span class="sxs-lookup"><span data-stu-id="e5181-150">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="e5181-151">Esse recurso habilita o suporte real à linguagem para criar tipos imutáveis e usar a sintaxe de propriedade automática mais concisa e conveniente.</span><span class="sxs-lookup"><span data-stu-id="e5181-151">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="e5181-152">Inicializadores de propriedade automática</span><span class="sxs-lookup"><span data-stu-id="e5181-152">Auto-Property Initializers</span></span>

<span data-ttu-id="e5181-153">Os *Inicializadores de propriedade automática* permitem que você declare o valor inicial de uma propriedade automática como parte da declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5181-153">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="e5181-154">Em versões anteriores, essas propriedades precisariam de setters e você teria que usar esse setter para inicializar o armazenamento de dados usado pelo campo de suporte.</span><span class="sxs-lookup"><span data-stu-id="e5181-154">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="e5181-155">Considere essa classe para um aluno que contém o nome e uma lista das notas do aluno:</span><span class="sxs-lookup"><span data-stu-id="e5181-155">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="e5181-156">Conforme essa classe cresce, você pode incluir outros construtores.</span><span class="sxs-lookup"><span data-stu-id="e5181-156">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="e5181-157">Cada construtor precisa inicializar este campo ou você introduzirá erros.</span><span class="sxs-lookup"><span data-stu-id="e5181-157">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="e5181-158">O C# 6 permite que você atribua um valor inicial para o armazenamento usado por uma propriedade automática na declaração da propriedade automática:</span><span class="sxs-lookup"><span data-stu-id="e5181-158">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="e5181-159">O membro `Grades` é inicializado no local em que é declarado.</span><span class="sxs-lookup"><span data-stu-id="e5181-159">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="e5181-160">Isso facilita realizar a inicialização exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="e5181-160">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="e5181-161">A inicialização faz parte da declaração de propriedade, tornando mais fácil igualar a alocação de armazenamento com a interface pública para objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="e5181-161">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="e5181-162">Inicializadores de propriedade podem ser usados com propriedades de leitura/gravação, bem como propriedades somente leitura, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="e5181-162">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="e5181-163">Membros de função aptos para expressão</span><span class="sxs-lookup"><span data-stu-id="e5181-163">Expression-bodied function members</span></span>

<span data-ttu-id="e5181-164">O corpo de muitos membros que escrevemos consiste em apenas uma instrução, que pode ser representada como uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e5181-164">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="e5181-165">Você pode reduzir essa sintaxe, escrevendo um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="e5181-165">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="e5181-166">Ele funciona para métodos e propriedades somente leitura.</span><span class="sxs-lookup"><span data-stu-id="e5181-166">It works for methods and read-only properties.</span></span> <span data-ttu-id="e5181-167">Por exemplo, uma substituição de `ToString()` é, geralmente, uma ótima candidata:</span><span class="sxs-lookup"><span data-stu-id="e5181-167">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="e5181-168">Você também pode usar membros bodied expressão nas propriedades somente leitura também:</span><span class="sxs-lookup"><span data-stu-id="e5181-168">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="e5181-169">usando estático</span><span class="sxs-lookup"><span data-stu-id="e5181-169">using static</span></span>

<span data-ttu-id="e5181-170">O aprimoramento *using static* permite que você importe os métodos estáticos de uma única classe.</span><span class="sxs-lookup"><span data-stu-id="e5181-170">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="e5181-171">Anteriormente, a instrução `using` importava todos os tipos de um namespace.</span><span class="sxs-lookup"><span data-stu-id="e5181-171">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="e5181-172">Com frequência usamos métodos estáticos de uma classe em todo o nosso código.</span><span class="sxs-lookup"><span data-stu-id="e5181-172">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="e5181-173">Digitar o nome de classe repetidamente pode obscurecer o significado do seu código.</span><span class="sxs-lookup"><span data-stu-id="e5181-173">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="e5181-174">Um exemplo comum é quando você escreve classes que realizam muitos cálculos numéricos.</span><span class="sxs-lookup"><span data-stu-id="e5181-174">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="e5181-175">Seu código ficará repleto <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> e outras chamadas a métodos diferentes na classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="e5181-175">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="e5181-176">A nova sintaxe `using static` pode deixar essas classes muito mais limpas para serem lidas.</span><span class="sxs-lookup"><span data-stu-id="e5181-176">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="e5181-177">Você especifica a classe que está usando:</span><span class="sxs-lookup"><span data-stu-id="e5181-177">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="e5181-178">E agora, você pode usar qualquer método estático na classe <xref:System.Math> sem qualificar a classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="e5181-178">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="e5181-179">A classe <xref:System.Math> é um ótimo caso de uso desse recurso, porque ela não contém nenhum método de instância.</span><span class="sxs-lookup"><span data-stu-id="e5181-179">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="e5181-180">Você também pode usar `using static` para importar os métodos estáticos de uma classe para uma classe que tem os métodos estáticos e de instância.</span><span class="sxs-lookup"><span data-stu-id="e5181-180">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="e5181-181">Um dos exemplos mais úteis é <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="e5181-181">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="e5181-182">Você deve usar o nome de classe totalmente qualificado `System.String` em uma instrução static using.</span><span class="sxs-lookup"><span data-stu-id="e5181-182">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="e5181-183">Não é possível usar a palavra-chave `string` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e5181-183">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="e5181-184">Agora você pode chamar métodos estáticos definidos na classe <xref:System.String> sem qualificar esses métodos como membros dessa classe:</span><span class="sxs-lookup"><span data-stu-id="e5181-184">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="e5181-185">O recurso `static using` e os métodos de extensão interagem de maneiras interessantes e o design de linguagem incluiu algumas regras que tratam especificamente dessas interações.</span><span class="sxs-lookup"><span data-stu-id="e5181-185">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="e5181-186">A meta é minimizar qualquer possibilidade de alterações significativas nas bases de código existentes, incluindo a sua.</span><span class="sxs-lookup"><span data-stu-id="e5181-186">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="e5181-187">Os métodos de extensão só estão no escopo quando chamados usando a sintaxe de invocação do método de extensão e não quando chamados como um método estático.</span><span class="sxs-lookup"><span data-stu-id="e5181-187">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="e5181-188">Você verá isso com frequência em consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="e5181-188">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="e5181-189">Você pode importar o padrão LINQ importando <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="e5181-189">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="e5181-190">Isso importa todos os métodos na classe <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="e5181-190">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="e5181-191">No entanto, os métodos de extensão somente estão no escopo quando chamados como métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="e5181-191">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="e5181-192">Eles não estão no escopo se chamados usando a sintaxe de método estático:</span><span class="sxs-lookup"><span data-stu-id="e5181-192">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="e5181-193">Essa decisão foi tomada porque os métodos de extensão são geralmente chamados usando expressões de invocação de método de extensão.</span><span class="sxs-lookup"><span data-stu-id="e5181-193">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="e5181-194">No caso raro em que eles são chamados usando a sintaxe de chamada ao método estático, é para resolver a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="e5181-194">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="e5181-195">Parece prudente exigir o nome de classe como parte da invocação.</span><span class="sxs-lookup"><span data-stu-id="e5181-195">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="e5181-196">Há um último recurso de `static using`.</span><span class="sxs-lookup"><span data-stu-id="e5181-196">There's one last feature of `static using`.</span></span> <span data-ttu-id="e5181-197">A diretiva `static using` também importa todos tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="e5181-197">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="e5181-198">Isso habilita você a referenciar qualquer tipo aninhado sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="e5181-198">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="e5181-199">Operadores condicionais null</span><span class="sxs-lookup"><span data-stu-id="e5181-199">Null-conditional operators</span></span>

<span data-ttu-id="e5181-200">Os valores null complicam o código.</span><span class="sxs-lookup"><span data-stu-id="e5181-200">Null values complicate code.</span></span> <span data-ttu-id="e5181-201">É necessário verificar cada acesso de variáveis para garantir que você não está desreferenciando `null`.</span><span class="sxs-lookup"><span data-stu-id="e5181-201">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="e5181-202">O *operador condicional null* torna essas verificações muito mais fáceis e fluidas.</span><span class="sxs-lookup"><span data-stu-id="e5181-202">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="e5181-203">Basta substituir o acesso de membro `.` por `?.`:</span><span class="sxs-lookup"><span data-stu-id="e5181-203">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="e5181-204">No exemplo anterior, a variável `first` é atribuída como `null` se o objeto person é `null`.</span><span class="sxs-lookup"><span data-stu-id="e5181-204">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="e5181-205">Caso contrário, ela é atribuída com o valor da propriedade `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="e5181-205">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="e5181-206">Mais importante, o `?.` significa que essa linha de código não gerará um `NullReferenceException` quando a variável `person` for `null`.</span><span class="sxs-lookup"><span data-stu-id="e5181-206">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="e5181-207">Em vez disso, ela encurta o caminho e produz `null`.</span><span class="sxs-lookup"><span data-stu-id="e5181-207">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="e5181-208">Além disso, observe que essa expressão retorna uma `string`, independentemente do valor de `person`.</span><span class="sxs-lookup"><span data-stu-id="e5181-208">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="e5181-209">No caso de encurtar o caminho, o valor `null` retornado é tipado para corresponder à expressão completa.</span><span class="sxs-lookup"><span data-stu-id="e5181-209">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="e5181-210">Você também pode usar esse constructo com o operador *null coalescing* para atribuir valores padrão quando uma das propriedades é `null`:</span><span class="sxs-lookup"><span data-stu-id="e5181-210">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="e5181-211">O operando do lado direito do operador `?.` não está limitado a campos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="e5181-211">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="e5181-212">Você também pode usá-lo para invocar métodos de maneira condicional.</span><span class="sxs-lookup"><span data-stu-id="e5181-212">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="e5181-213">O uso mais comum de funções membro com o operador condicional null é para invocar delegados com segurança (ou manipuladores de eventos) que podem ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e5181-213">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="e5181-214">Você fará isso chamando o método `Invoke` do delegado, usando o operador `?.` para acessar o membro.</span><span class="sxs-lookup"><span data-stu-id="e5181-214">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="e5181-215">Você pode ver um exemplo no</span><span class="sxs-lookup"><span data-stu-id="e5181-215">You can see an example in the</span></span>  
<span data-ttu-id="e5181-216">tópico [padrões delegados](../delegates-patterns.md#handling-null-delegates).</span><span class="sxs-lookup"><span data-stu-id="e5181-216">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="e5181-217">As regras do operador `?.` garantem que o lado esquerdo do operador é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e5181-217">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="e5181-218">Isso é importante e habilita muitas expressões, incluindo o exemplo com o uso de manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="e5181-218">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="e5181-219">Vamos começar com o uso do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e5181-219">Let's start with the event handler usage.</span></span> <span data-ttu-id="e5181-220">Nas versões anteriores do C#, você era incentivado a escrever código assim:</span><span class="sxs-lookup"><span data-stu-id="e5181-220">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="e5181-221">Isso era preferível em relação a uma sintaxe mais simples:</span><span class="sxs-lookup"><span data-stu-id="e5181-221">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="e5181-222">O exemplo anterior introduz uma condição de corrida.</span><span class="sxs-lookup"><span data-stu-id="e5181-222">The preceding example introduces a race condition.</span></span> <span data-ttu-id="e5181-223">O evento `SomethingHappened` pode ter assinantes quando verificado em relação a `null` e esses assinantes podem ter sido removidos antes de o evento ser acionado.</span><span class="sxs-lookup"><span data-stu-id="e5181-223">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="e5181-224">Isso poderia causar o lançamento de uma <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="e5181-224">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="e5181-225">Nesta segunda versão, o manipulador de eventos `SomethingHappened` pode ser não nulo quando testado, mas se outro código remover um manipulador, ele ainda poderia ser null quando o manipulador de eventos foi chamado.</span><span class="sxs-lookup"><span data-stu-id="e5181-225">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="e5181-226">O compilador gera um código para o operador `?.`, que garante que o lado esquerdo (`this.SomethingHappened`) da expressão `?.` é avaliado uma vez e o resultado é armazenado em cache:</span><span class="sxs-lookup"><span data-stu-id="e5181-226">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="e5181-227">Garantir que o lado esquerdo seja avaliado apenas uma vez também habilita você a usar qualquer expressão, inclusive chamadas de método, no lado esquerdo do `?.`. Mesmo que elas tenham efeitos colaterais, elas serão avaliadas uma vez e os efeitos colaterais ocorrerão apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e5181-227">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="e5181-228">Você pode ver um exemplo em nosso conteúdo em [eventos](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="e5181-228">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="e5181-229">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e5181-229">String Interpolation</span></span>

<span data-ttu-id="e5181-230">O C# 6 contém uma nova sintaxe para compor cadeias de caracteres de uma cadeia de caracteres de formato e de expressões que podem ser avaliadas para produzir outros valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e5181-230">C# 6 contains new syntax for composing strings from a format string and expressions that can be evaluated to produce other string values.</span></span>

<span data-ttu-id="e5181-231">Tradicionalmente, você precisava usar parâmetros posicionais em um método como `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="e5181-231">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="e5181-232">Com o C# 6, o novo recurso de interpolação de cadeia de caracteres permite que você insira as expressões na cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="e5181-232">With C# 6, the new string interpolation feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="e5181-233">Basta preceder a cadeia de caracteres com `$`:</span><span class="sxs-lookup"><span data-stu-id="e5181-233">Simple preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="e5181-234">Este exemplo inicial usou expressões variáveis para as expressões substituídas.</span><span class="sxs-lookup"><span data-stu-id="e5181-234">This initial example used variable expressions for the substituted expressions.</span></span> <span data-ttu-id="e5181-235">Você pode expandir esta sintaxe para usar qualquer expressão.</span><span class="sxs-lookup"><span data-stu-id="e5181-235">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="e5181-236">Por exemplo, você pode calcular a média do aluno como parte da interpolação:</span><span class="sxs-lookup"><span data-stu-id="e5181-236">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="e5181-237">Ao executar o exemplo anterior, você veria que a saída de `Grades.Average()` pode ter mais casas decimais do que o desejado.</span><span class="sxs-lookup"><span data-stu-id="e5181-237">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="e5181-238">A sintaxe de interpolação de cadeia de caracteres dá suporte a todas as cadeias de caracteres de formato disponíveis que usam métodos de formatação anteriores.</span><span class="sxs-lookup"><span data-stu-id="e5181-238">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="e5181-239">Você adiciona as cadeias de caracteres de formato dentro de chaves.</span><span class="sxs-lookup"><span data-stu-id="e5181-239">You add the format strings inside the braces.</span></span> <span data-ttu-id="e5181-240">Adicione um `:` seguido da expressão a ser formatada:</span><span class="sxs-lookup"><span data-stu-id="e5181-240">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="e5181-241">A linha de código anterior formatará o valor de `Grades.Average()` como um número de ponto flutuante com duas casas decimais.</span><span class="sxs-lookup"><span data-stu-id="e5181-241">The preceding line of code will format the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="e5181-242">O `:` é sempre interpretado como o separador entre a expressão que está sendo formatada e a cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="e5181-242">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="e5181-243">Isso pode causar problemas quando a expressão usa um `:` de outra forma, como um operador condicional:</span><span class="sxs-lookup"><span data-stu-id="e5181-243">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="e5181-244">No exemplo anterior, o `:` é analisado como o início da cadeia de caracteres de formato e não como parte do operador condicional.</span><span class="sxs-lookup"><span data-stu-id="e5181-244">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="e5181-245">Em todos os casos em que isso ocorre, você pode colocar a expressão entre parênteses para forçar o compilador a interpretar a expressão como você deseja:</span><span class="sxs-lookup"><span data-stu-id="e5181-245">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="e5181-246">Não há limitações em expressões que você pode colocar entre as chaves.</span><span class="sxs-lookup"><span data-stu-id="e5181-246">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="e5181-247">Você pode executar uma consulta LINQ complexa dentro de uma cadeia de caracteres interpolada para realizar cálculos e exibir o resultado:</span><span class="sxs-lookup"><span data-stu-id="e5181-247">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="e5181-248">Neste exemplo você pode ver que é até mesmo possível aninhar uma expressão de interpolação de cadeia de caracteres dentro de outra expressão de interpolação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e5181-248">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="e5181-249">É muito provável que este exemplo seja mais complexo do que você desejaria no código de produção.</span><span class="sxs-lookup"><span data-stu-id="e5181-249">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="e5181-250">No entanto, ele serve para ilustrar abrangência do recurso.</span><span class="sxs-lookup"><span data-stu-id="e5181-250">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="e5181-251">Qualquer expressão de C# pode ser colocada entre as chaves de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="e5181-251">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="e5181-252">Interpolação de cadeia de caracteres e culturas específicas</span><span class="sxs-lookup"><span data-stu-id="e5181-252">String interpolation and specific cultures</span></span>

<span data-ttu-id="e5181-253">Todos os exemplos mostrados na seção anterior formatarão as cadeias de caracteres usando a cultura e o idioma atuais do computador em que o código é executado.</span><span class="sxs-lookup"><span data-stu-id="e5181-253">All the examples shown in the preceding section will format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="e5181-254">Com frequência, talvez seja necessário formatar a cadeia de caracteres gerada, usando uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="e5181-254">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="e5181-255">O objeto produzido de uma interpolação de cadeia de caracteres é um tipo que tem uma conversão implícita para <xref:System.String> ou <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="e5181-255">The object produced from a string interpolation is a type that has an implicit conversion to either <xref:System.String> or <xref:System.FormattableString>.</span></span>

<span data-ttu-id="e5181-256">O tipo <xref:System.FormattableString> contém a cadeia de caracteres de formato e os resultados da avaliação de argumentos antes de convertê-los em cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e5181-256">The <xref:System.FormattableString> type contains the format string, and the results of evaluating the arguments before converting them to strings.</span></span> <span data-ttu-id="e5181-257">Você pode usar métodos públicos de <xref:System.FormattableString> para especificar a cultura ao formatar uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e5181-257">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="e5181-258">O exemplo a seguir produzirá uma cadeia de caracteres usando o alemão como o idioma e a cultura.</span><span class="sxs-lookup"><span data-stu-id="e5181-258">For example, the following will produce a string using German as the language and culture.</span></span> <span data-ttu-id="e5181-259">(Ele usará o caractere ',' para o separador decimal e o caractere '.' como separador de milhares).</span><span class="sxs-lookup"><span data-stu-id="e5181-259">(It will use the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = string.Format(null, 
    System.Globalization.CultureInfo.CreateSpecificCulture("de-de"),
    str.GetFormat(), str.GetArguments());
```

> [!NOTE]
> <span data-ttu-id="e5181-260">Não há suporte para o exemplo anterior na versão 1.0.1 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5181-260">The preceding example is not supported in .NET Core version 1.0.1.</span></span> <span data-ttu-id="e5181-261">Somente há suporte no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5181-261">It is only supported in the .NET Framework.</span></span>

<span data-ttu-id="e5181-262">Em geral, as expressões de interpolação de cadeia de caracteres geram cadeias de caracteres como saída.</span><span class="sxs-lookup"><span data-stu-id="e5181-262">In general, string interpolation expressions produce strings as their output.</span></span> <span data-ttu-id="e5181-263">No entanto, quando você deseja maior controle sobre a cultura usada para formatar a cadeia de caracteres, você pode determinar uma saída específica.</span><span class="sxs-lookup"><span data-stu-id="e5181-263">However, when you want greater control over the culture used to format the string, you can specify a specific output.</span></span>  <span data-ttu-id="e5181-264">Se essa é uma capacidade que é geralmente necessário, você pode criar métodos de conveniência, como métodos de extensão, para habilitar a formatação fácil com culturas específicas.</span><span class="sxs-lookup"><span data-stu-id="e5181-264">If this is a capability you often need, you can create convenience methods, as extension methods, to enable easy formatting with specific cultures.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="e5181-265">Filtros de exceção</span><span class="sxs-lookup"><span data-stu-id="e5181-265">Exception Filters</span></span>

<span data-ttu-id="e5181-266">Outro recurso novo no C# 6 são os *filtros de exceção*.</span><span class="sxs-lookup"><span data-stu-id="e5181-266">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="e5181-267">Os filtros de exceção são cláusulas que determinam quando uma determinada cláusula catch deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="e5181-267">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="e5181-268">Se a expressão usada para um filtro de exceção é avaliada como `true`, a cláusula catch realiza seu processamento normal em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e5181-268">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="e5181-269">Se a expressão for avaliada como `false`, a cláusula `catch` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="e5181-269">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="e5181-270">Um uso é examinar informações sobre uma exceção para determinar se uma cláusula `catch` pode processar a exceção:</span><span class="sxs-lookup"><span data-stu-id="e5181-270">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="e5181-271">O código gerado pelos filtros de exceção fornece melhores informações sobre uma exceção que é lançada e não é processada.</span><span class="sxs-lookup"><span data-stu-id="e5181-271">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="e5181-272">Antes que os filtros de exceção fossem adicionados à linguagem, era preciso criar código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5181-272">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="e5181-273">O ponto em que a exceção é lançada muda nestes dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="e5181-273">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="e5181-274">No código anterior, em que uma cláusula `throw` é usada, qualquer análise do rastreamento de pilha ou exame de despejos de memória mostrará que a exceção foi lançada da instrução `throw` na cláusula catch.</span><span class="sxs-lookup"><span data-stu-id="e5181-274">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="e5181-275">O objeto de exceção real conterá a pilha de chamadas original, mas todas as outras informações sobre as variáveis na pilha de chamadas, entre este ponto de lançamento e o local do ponto de lançamento original, foram perdidas.</span><span class="sxs-lookup"><span data-stu-id="e5181-275">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="e5181-276">Compare isso com a maneira como o código que usa um filtro de exceção é processado: a expressão do filtro de exceção avalia como `false`.</span><span class="sxs-lookup"><span data-stu-id="e5181-276">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="e5181-277">Portanto, execução nunca insere a cláusula `catch`.</span><span class="sxs-lookup"><span data-stu-id="e5181-277">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="e5181-278">Como a cláusula `catch` não é executada, o desenrolamento de pilha não ocorre.</span><span class="sxs-lookup"><span data-stu-id="e5181-278">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="e5181-279">Isso significa que o local de lançamento original é preservado para qualquer atividade de depuração que aconteceria mais tarde.</span><span class="sxs-lookup"><span data-stu-id="e5181-279">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="e5181-280">Sempre que você precisar avaliar campos ou propriedades de uma exceção, em vez de depender exclusivamente do tipo de exceção, use um filtro de exceção para preservar mais informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="e5181-280">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="e5181-281">Outro padrão recomendado com filtros de exceção é usá-los para rotinas de registro em log.</span><span class="sxs-lookup"><span data-stu-id="e5181-281">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="e5181-282">Esse uso também aproveita a maneira pela qual o ponto de lançamento de exceção é preservado quando um filtro de exceção é avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="e5181-282">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="e5181-283">Um método de registro em log seria um método cujo argumento é a exceção que retorna incondicionalmente `false`:</span><span class="sxs-lookup"><span data-stu-id="e5181-283">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="e5181-284">Sempre que você desejar registrar uma exceção, você pode adicionar uma cláusula catch e usar esse método como o filtro de exceção:</span><span class="sxs-lookup"><span data-stu-id="e5181-284">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="e5181-285">As exceções nunca são capturadas, porque o método `LogException` sempre retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="e5181-285">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="e5181-286">Esse filtro de exceção sempre falso significa que você pode colocar esse manipulador de log antes de qualquer outro manipulador de exceção:</span><span class="sxs-lookup"><span data-stu-id="e5181-286">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="e5181-287">O exemplo anterior destaca uma faceta muito importante dos filtros de exceção.</span><span class="sxs-lookup"><span data-stu-id="e5181-287">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="e5181-288">Os filtros de exceção permitem cenários em que uma cláusula de captura de exceção mais geral pode aparecer antes de uma mais específica.</span><span class="sxs-lookup"><span data-stu-id="e5181-288">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="e5181-289">Também é possível ter o mesmo tipo de exceção aparecendo em várias cláusulas catch:</span><span class="sxs-lookup"><span data-stu-id="e5181-289">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="e5181-290">Outro padrão recomendado ajuda a evitar que cláusulas catch processem exceções quando um depurador é anexado.</span><span class="sxs-lookup"><span data-stu-id="e5181-290">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="e5181-291">Essa técnica permite que você execute um aplicativo com o depurador e interrompa a execução quando uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="e5181-291">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="e5181-292">No seu código, adicione um filtro de exceção para que qualquer código de recuperação seja executado somente quando um depurador não estiver anexado:</span><span class="sxs-lookup"><span data-stu-id="e5181-292">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="e5181-293">Depois de adicionar isso no código, você deve definir o depurador para interromper em todas as exceções sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="e5181-293">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="e5181-294">Execute o programa no depurador e o depurador interromperá sempre que `PerformFailingOperation()` lançar uma `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="e5181-294">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="e5181-295">O depurador interrompe o programa, porque a cláusula catch não será executada devido ao filtro de exceção que retorna false.</span><span class="sxs-lookup"><span data-stu-id="e5181-295">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="e5181-296">Expressões `nameof`</span><span class="sxs-lookup"><span data-stu-id="e5181-296">`nameof` Expressions</span></span>

<span data-ttu-id="e5181-297">A expressão `nameof` é avaliada para o nome de um símbolo.</span><span class="sxs-lookup"><span data-stu-id="e5181-297">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="e5181-298">É uma ótima maneira de fazer com que as ferramentas funcionem sempre que você precisar do nome de uma variável, de uma propriedade ou de um campo de membro.</span><span class="sxs-lookup"><span data-stu-id="e5181-298">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="e5181-299">Um dos usos mais comuns para `nameof` é fornecer o nome de um símbolo que causou uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e5181-299">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="e5181-300">Outro uso é com aplicativos baseados em XAML que implementam a interface `INotifyPropertyChanged`:</span><span class="sxs-lookup"><span data-stu-id="e5181-300">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="e5181-301">A vantagem de usar o operador `nameof` em uma cadeia de caracteres constante é que as ferramentas podem entender o símbolo.</span><span class="sxs-lookup"><span data-stu-id="e5181-301">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="e5181-302">Se você usar ferramentas de refatoração para renomear o símbolo, elas vão renomeá-lo na expressão `nameof`.</span><span class="sxs-lookup"><span data-stu-id="e5181-302">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="e5181-303">As cadeias de caracteres constantes não têm essa vantagem.</span><span class="sxs-lookup"><span data-stu-id="e5181-303">Constant strings don't have that advantage.</span></span> <span data-ttu-id="e5181-304">Experimente você mesmo em seu editor favorito: renomeie uma variável e qualquer expressão `nameof` também atualizará.</span><span class="sxs-lookup"><span data-stu-id="e5181-304">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="e5181-305">A expressão `nameof` produz o nome não qualificado de seu argumento (`LastName` nos exemplos anteriores), mesmo que você use o nome totalmente qualificado para o argumento:</span><span class="sxs-lookup"><span data-stu-id="e5181-305">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="e5181-306">Essa expressão `nameof` produz `FirstName` e não `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="e5181-306">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="e5181-307">Await em blocos catch e finally</span><span class="sxs-lookup"><span data-stu-id="e5181-307">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="e5181-308">O C# 5 tinha várias limitações quanto ao local em que você poderia colocar expressões `await`.</span><span class="sxs-lookup"><span data-stu-id="e5181-308">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="e5181-309">Uma delas foi removida no C# 6.</span><span class="sxs-lookup"><span data-stu-id="e5181-309">One of those has been removed in C# 6.</span></span> <span data-ttu-id="e5181-310">Agora você pode usar `await` em expressões `catch` ou `finally`.</span><span class="sxs-lookup"><span data-stu-id="e5181-310">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="e5181-311">A adição de expressões await em blocos catch e finally pode parecer complicar a maneira como eles são processados.</span><span class="sxs-lookup"><span data-stu-id="e5181-311">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="e5181-312">Vamos adicionar um exemplo para discutir como isso é exibido.</span><span class="sxs-lookup"><span data-stu-id="e5181-312">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="e5181-313">Em qualquer método assíncrono, você pode usar uma expressão await em uma cláusula finally.</span><span class="sxs-lookup"><span data-stu-id="e5181-313">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="e5181-314">Com o C# 6, você também pode aguardar em expressões catch.</span><span class="sxs-lookup"><span data-stu-id="e5181-314">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="e5181-315">Isso geralmente é usado com cenários de registro em log:</span><span class="sxs-lookup"><span data-stu-id="e5181-315">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="e5181-316">Os detalhes de implementação para adicionar suporte ao `await` dentro de cláusulas `catch` e `finally` garante que o comportamento é consistente com o comportamento de código síncrono.</span><span class="sxs-lookup"><span data-stu-id="e5181-316">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="e5181-317">Quando o código que é executado em uma cláusula `catch` ou `finally` realiza o lançamento, a execução procura por uma cláusula `catch` adequada no próximo bloco.</span><span class="sxs-lookup"><span data-stu-id="e5181-317">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="e5181-318">Se houver uma exceção atual, essa exceção será perdida.</span><span class="sxs-lookup"><span data-stu-id="e5181-318">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="e5181-319">O mesmo acontece com expressões aguardadas em cláusulas `catch` e `finally`: um `catch` adequado é pesquisado e a exceção atual, se houver, será perdida.</span><span class="sxs-lookup"><span data-stu-id="e5181-319">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="e5181-320">Esse comportamento é a razão pela qual recomenda-se escrever cláusulas `catch` e `finally` com cuidado, a fim de evitar introduzir novas exceções.</span><span class="sxs-lookup"><span data-stu-id="e5181-320">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="e5181-321">Inicializadores de índice</span><span class="sxs-lookup"><span data-stu-id="e5181-321">Index Initializers</span></span>

<span data-ttu-id="e5181-322">Os *inicializadores de índice* são um dos dois recursos que tornam os inicializadores de coleção mais consistentes.</span><span class="sxs-lookup"><span data-stu-id="e5181-322">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="e5181-323">Em versões anteriores do C#, você podia usar *inicializadores de coleção* apenas com coleções de estilo de sequência:</span><span class="sxs-lookup"><span data-stu-id="e5181-323">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="e5181-324">Agora, você também pode usá-los com coleções <xref:System.Collections.Generic.Dictionary%602> e tipos semelhantes:</span><span class="sxs-lookup"><span data-stu-id="e5181-324">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="e5181-325">Esse recurso significa que os contêineres associativos podem ser inicializados usando uma sintaxe semelhante à que está em vigor para contêineres de sequência de várias versões.</span><span class="sxs-lookup"><span data-stu-id="e5181-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

### <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="e5181-326">Métodos `Add` de extensão em inicializadores de coleção</span><span class="sxs-lookup"><span data-stu-id="e5181-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="e5181-327">Outro recurso que facilita a inicialização de coleção é a capacidade de usar um *método de extensão* para o método `Add`.</span><span class="sxs-lookup"><span data-stu-id="e5181-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="e5181-328">Esse recurso foi adicionado para a paridade com o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5181-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="e5181-329">O recurso é mais útil quando você tem uma classe de coleção personalizada que tem um método com um nome diferente para adicionar novos itens semanticamente.</span><span class="sxs-lookup"><span data-stu-id="e5181-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="e5181-330">Por exemplo, considere uma coleção de alunos como esta:</span><span class="sxs-lookup"><span data-stu-id="e5181-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="e5181-331">O método `Enroll` adiciona um aluno.</span><span class="sxs-lookup"><span data-stu-id="e5181-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="e5181-332">Mas não segue o padrão `Add`.</span><span class="sxs-lookup"><span data-stu-id="e5181-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="e5181-333">Nas versões anteriores do C#, você não podia usar os inicializadores de coleção com um objeto `Enrollment`:</span><span class="sxs-lookup"><span data-stu-id="e5181-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="e5181-334">Agora você pode, mas apenas se você criar um método de extensão que mapeia `Add` para `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="e5181-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="e5181-335">O que você está fazendo com esse recurso é mapear qualquer método que adiciona itens a uma coleção, em um método chamado `Add`, criando um método de extensão:</span><span class="sxs-lookup"><span data-stu-id="e5181-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method:</span></span> 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a><span data-ttu-id="e5181-336">Resolução de sobrecarga aprimorada</span><span class="sxs-lookup"><span data-stu-id="e5181-336">Improved overload resolution</span></span>

<span data-ttu-id="e5181-337">Esse último recurso provavelmente não será notado.</span><span class="sxs-lookup"><span data-stu-id="e5181-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="e5181-338">Havia constructos nos quais a versão anterior do compilador do C# pode ter encontrado algumas chamadas de método que envolviam expressões lambda ambíguas.</span><span class="sxs-lookup"><span data-stu-id="e5181-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="e5181-339">Considere este método:</span><span class="sxs-lookup"><span data-stu-id="e5181-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="e5181-340">Em versões anteriores do C#, haveria uma falha ao chamar esse método usando a sintaxe de grupo de método:</span><span class="sxs-lookup"><span data-stu-id="e5181-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="e5181-341">O compilador anterior não podia distinguir corretamente entre `Task.Run(Action)` e `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="e5181-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="e5181-342">Nas versões anteriores, você precisava usar uma expressão lambda como um argumento:</span><span class="sxs-lookup"><span data-stu-id="e5181-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="e5181-343">O compilador do C# 6 determina corretamente que `Task.Run(Func<Task>())` é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="e5181-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>