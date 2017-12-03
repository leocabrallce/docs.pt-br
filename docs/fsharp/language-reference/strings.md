---
title: Cadeias de caracteres (F#)
description: "Saiba como o tipo 'string' F # representa texto imutável como uma sequência de caracteres Unicode."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a><span data-ttu-id="895cf-104">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="895cf-104">Strings</span></span>

> [!NOTE]
<span data-ttu-id="895cf-105">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="895cf-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="895cf-106">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="895cf-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="895cf-107">O `string` tipo representa texto imutável como uma sequência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="895cf-107">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="895cf-108">`string` é um alias para `System.String` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="895cf-108">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="895cf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="895cf-109">Remarks</span></span>
<span data-ttu-id="895cf-110">Literais de cadeia de caracteres são delimitados pelo caractere de aspas (").</span><span class="sxs-lookup"><span data-stu-id="895cf-110">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="895cf-111">O caractere de barra invertida (\) é usado para codificar alguns caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="895cf-111">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="895cf-112">A barra invertida e o próximo caractere junto são conhecidos como um *sequência de escape*.</span><span class="sxs-lookup"><span data-stu-id="895cf-112">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="895cf-113">Suportada em F # de cadeia de caracteres literais são mostrados na tabela a seguir de sequências de escape.</span><span class="sxs-lookup"><span data-stu-id="895cf-113">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="895cf-114">Caractere</span><span class="sxs-lookup"><span data-stu-id="895cf-114">Character</span></span>|<span data-ttu-id="895cf-115">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="895cf-115">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="895cf-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="895cf-116">Backspace</span></span>|<span data-ttu-id="895cf-117">\b</span><span class="sxs-lookup"><span data-stu-id="895cf-117">\b</span></span>|
|<span data-ttu-id="895cf-118">Nova linha</span><span class="sxs-lookup"><span data-stu-id="895cf-118">Newline</span></span>|\n|
|<span data-ttu-id="895cf-119">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="895cf-119">Carriage return</span></span>|<span data-ttu-id="895cf-120">\r</span><span class="sxs-lookup"><span data-stu-id="895cf-120">\r</span></span>|
|<span data-ttu-id="895cf-121">Tabulação</span><span class="sxs-lookup"><span data-stu-id="895cf-121">Tab</span></span>|<span data-ttu-id="895cf-122">\t</span><span class="sxs-lookup"><span data-stu-id="895cf-122">\t</span></span>|
|<span data-ttu-id="895cf-123">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="895cf-123">Backslash</span></span>|\\|
|<span data-ttu-id="895cf-124">Aspas</span><span class="sxs-lookup"><span data-stu-id="895cf-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="895cf-125">Apóstrofo</span><span class="sxs-lookup"><span data-stu-id="895cf-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="895cf-126">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="895cf-126">Unicode character</span></span>|<span data-ttu-id="895cf-127">\u*XXXX* ou \U*XXXXXXXX* (onde *X* indica um dígito hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="895cf-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="895cf-128">Se precedido pelo símbolo @, o literal é uma cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="895cf-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="895cf-129">Isso significa que qualquer sequências de escape são ignoradas, exceto pelo fato de dois caracteres de aspas são interpretadas como um aspas caractere.</span><span class="sxs-lookup"><span data-stu-id="895cf-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="895cf-130">Além disso, uma cadeia de caracteres pode ser delimitada por aspas triplos.</span><span class="sxs-lookup"><span data-stu-id="895cf-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="895cf-131">Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="895cf-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="895cf-132">Para especificar uma cadeia de caracteres que contém um inseridos entre aspas, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="895cf-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="895cf-133">Se você usar uma cadeia de caracteres textual, você deve especificar dois caracteres de aspas para indicar um caractere de aspas simples.</span><span class="sxs-lookup"><span data-stu-id="895cf-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="895cf-134">Se você usar uma cadeia de caracteres entre aspas triplas, você pode usar os caracteres de aspas simples sem eles sendo analisada como o fim da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="895cf-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="895cf-135">Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que contêm aspas inseridas.</span><span class="sxs-lookup"><span data-stu-id="895cf-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="895cf-136">No código, cadeias de caracteres que têm quebras de linha são aceitos e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida é o último caractere antes da quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="895cf-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="895cf-137">Espaço em branco na próxima linha é ignorado quando o caractere de barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="895cf-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="895cf-138">O código a seguir produz uma cadeia de caracteres `str1` que tem o valor `"abc\n     def"` e uma cadeia de caracteres `str2` que tem o valor `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="895cf-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="895cf-139">Você pode acessar caracteres individuais em uma cadeia de caracteres usando a sintaxe de matriz, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="895cf-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="895cf-140">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="895cf-140">The output is `b`.</span></span>

<span data-ttu-id="895cf-141">Ou você pode extrair subcadeias de caracteres usando a sintaxe de fatia de matriz, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="895cf-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="895cf-142">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="895cf-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="895cf-143">Você pode representar cadeias de caracteres ASCII, matrizes de bytes não assinados, digite `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="895cf-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="895cf-144">Adicionar o sufixo `B` para uma cadeia de caracteres literal para indicar que é uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="895cf-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="895cf-145">Literais de cadeia de caracteres ASCII usados com matrizes de bytes oferecem suporte a sequências de escape como cadeias de caracteres Unicode, exceto para as sequências de escape Unicode.</span><span class="sxs-lookup"><span data-stu-id="895cf-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="895cf-146">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895cf-146">String Operators</span></span>
<span data-ttu-id="895cf-147">Para concatenar cadeias de caracteres de duas maneiras: usando o `+` operador ou usando o `^` operador.</span><span class="sxs-lookup"><span data-stu-id="895cf-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="895cf-148">O `+` operador mantém a compatibilidade com a cadeia de caracteres do .NET Framework tratamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="895cf-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="895cf-149">O exemplo a seguir ilustra a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="895cf-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="895cf-150">Classe de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895cf-150">String Class</span></span>
<span data-ttu-id="895cf-151">Porque o tipo de cadeia de caracteres em F # é realmente um .NET Framework `System.String` digitar, todo o `System.String` membros estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="895cf-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="895cf-152">Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, o `Length` propriedade e o `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="895cf-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="895cf-153">Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.</span><span class="sxs-lookup"><span data-stu-id="895cf-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="895cf-154">Usando o `Chars` propriedade `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="895cf-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="895cf-155">Módulo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895cf-155">String Module</span></span>
<span data-ttu-id="895cf-156">Funcionalidade adicional para manipulação de cadeia de caracteres está incluída no `String` módulo o `FSharp.Core` namespace.</span><span class="sxs-lookup"><span data-stu-id="895cf-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="895cf-157">Para obter mais informações, consulte [abreviação de módulo](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="895cf-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="895cf-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="895cf-158">See Also</span></span>
[<span data-ttu-id="895cf-159">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="895cf-159">F# Language Reference</span></span>](index.md)