---
title: Referência do F# Interativo (fsi.exe)
description: 'Saiba como F # interativo (fsi.exe) é usado para executar código F # interativamente no console ou para executar scripts do F #.'
keywords: visual f#, f#, programação funcional
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36af8d1b-dc08-4a37-9497-d23c0a0ac11c
ms.openlocfilehash: a18f339d898374a59858cd774154b3846594d183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="interactive-programming-with-f"></a>Programação interativa com F# #

> [!NOTE]
Atualmente, este artigo descreve somente a experiência para Windows.  Ele será reescrito.

> [!NOTE]
O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O F# interativo (fsi.exe) é usado para executar o código do F# de forma interativa no console ou executar scripts do F#. Em outras palavras, o F# interativo executa um REPL (Ler, Avaliar, Imprimir Loop) para a linguagem F#.

Para executar o F# interativo a partir do console, execute fsi.exe.  Você encontrará fsi.exe em "c:\Program arquivos (x86) \Microsoft SDKs\F#\<versão > \Framework\<versão >\". Para saber mais sobre as opções de linha de comando disponíveis, veja [Opções de F# Interativo](../../language-reference/fsharp-interactive-options.md).

Para executar o F# Interativo por meio do Visual Studio, você pode clicar no botão de barra de ferramentas apropriado rotulado como **F# Interativo** ou usar as teclas **Ctrl+Alt+F**. Isso abrirá a janela interativa, uma janela da ferramenta que executa uma sessão de F# interativo. Você pode também selecionar algum código que deseja executar na janela interativa e pressionar a combinação de teclas **ALT+ENTER**. O F# interativo é iniciado em uma janela da ferramenta rotulada como **F# Interativo**. Quando você usar essa combinação de teclas, certifique-se de que a janela do editor tenha o foco.

Se você estiver usando o console ou o Visual Studio, será exibido um prompt de comando e o interpretador aguardará a entrada. Você pode inserir o código como faria em um arquivo de código. Para compilar e executar o código, insira dois sinais de ponto e vírgula (**;;**) para terminar uma linha ou várias linhas de entrada.

O F# interativo tenta compilar o código e, se tiver êxito, executará o código e imprimirá a assinatura dos tipos e valores que ele compilou. Se ocorrerem erros, o interpretador imprime as mensagens de erro.

O código digitado na mesma sessão tem acesso a quaisquer construções inseridas anteriormente, para poder criar os programas. Um buffer extensivo na janela da ferramenta permite que você copie o código para um arquivo, se necessário.

Quando executado no Visual Studio, o F# interativo é executado independentemente do seu projeto, então, por exemplo, não é possível usar construções definidas em seu projeto em F# interativo, a menos que você copie o código para a função na janela interativa.

Se você tiver um projeto aberto que faça referência a algumas bibliotecas, poderá fazer referência em F# interativo por meio do **Gerenciador de Soluções**. Para fazer referência a uma biblioteca de F# Interativo, expanda o nó **Referências**, abra o menu de atalho da biblioteca e escolha **Enviar para F# Interativo**.

Você pode controlar os argumentos de linha de comando do F# interativo (opções) ajustando as configurações. No menu **Ferramentas**, selecione **Opções...** e expanda **Ferramentas do F#**. As duas configurações que podem ser alteradas são as opções do F# interativo e a configuração do **F# Interativo de 64 bits**, que é relevante apenas se você estiver executando o F# interativo em uma máquina de 64 bits. Essa configuração determina se você deseja executar a versão de 64 bits dedicada do fsi.exe ou do fsianycpu.exe, que usa a arquitetura de máquina para determinar se deve ser executada como um processo de 32 ou 64 bits.


## <a name="scripting-with-f"></a>Scripts com F# #
Os scripts usam a extensão de arquivo **.fsx** ou **.fsscript**. Em vez de compilar o código-fonte e executar o conjunto compilado posteriormente, é possível executar apenas **fsi.exe** e especificar o nome do arquivo do script de código-fonte do F# e o F# interativo lerá o código e o executará em tempo real.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Diferenças entre os ambientes interativo, de script e compilado
Quando você está compilando código em F# interativo, se estiver executando de forma interativa ou executando um script, o símbolo **INTERACTIVE** será definido. Quando você está compilando código no compilador, o símbolo **COMPILED** é definido. Assim, se o código precisar ser diferente nos modos compilados e interativos, você poderá usar diretivas de pré-processador para compilação condicional para determinar qual você deseja usar.

Algumas diretivas estão disponíveis durante a execução de scripts no F# interativo, mas não estão disponíveis quando você está executando o compilador. A tabela a seguir resume as diretivas que estão disponíveis quando você estiver usando o F# interativo.

|Diretiva|Descrição|
|---------|-----------|
|**#help**|Exibe informações sobre as diretivas disponíveis.|
|**#I**|Especifica um caminho de pesquisa de assembly entre aspas.|
|**#load**|Lê um arquivo de origem, compila e o executa.|
|**#quit**|Finaliza uma sessão do F# interativo.|
|**#r**|Faz referência a um assembly.|
|**#time ["on"&#124;"off"]**|Por si só, **#time** alterna se deve exibir informações sobre o desempenho. Quando habilitado, o F# interativo mede informações em tempo real, em tempo de CPU e de coleta de lixo de cada seção do código que é interpretado e executado.|

Quando você especificar arquivos ou caminhos em F# interativo, uma sequência literal é esperada. Portanto, arquivos e caminhos devem estar entre aspas e os caracteres de escape comuns se aplicam. Além disso, você pode usar o caractere @ para fazer com que o F# interativo interprete uma cadeia de caracteres que contenha um caminho como uma cadeia de caracteres textuais. Isso faz com que o F# interativo ignore quaisquer caracteres de escape.

Uma das diferenças entre o modo interativo e compilado é a maneira como você acessa argumentos da linha de comando. No modo compilado, use **System.Environment.GetCommandLineArgs**. Em scripts, use **fsi.CommandLineArgs**.

O código a seguir ilustra como criar uma função que lê os argumentos da linha de comando em um script e também demonstra como fazer referência a outro conjunto por meio de um script. O primeiro arquivo de código, **MyAssembly.fs**, é o código do assembly que está sendo referenciado. Compile esse arquivo com a linha de comando: **fsc -a MyAssembly.fs** e, em seguida, execute o segundo arquivo como um script com a linha de comando: **fsi --exec file1.fsx** test

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

A saída é a seguinte:

```
Command line arguments: 
file1.fsx
test
60
```

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Opções do F# Interativo](../../language-reference/fsharp-interactive-options.md)|Descreve a sintaxe de linha de comando e as opções de F # interativo, fsi.exe.|
|[Referência da biblioteca do F# Interativo](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Descreve a funcionalidade de biblioteca disponível ao executar o código em F# interativo.|
