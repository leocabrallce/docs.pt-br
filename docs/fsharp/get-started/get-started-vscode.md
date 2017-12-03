---
title: "Guia de Introdução com F # em código do Visual Studio com Ionide"
description: "Saiba como usar o F # com o código do Visual Studio e o conjunto de plug-in de Ionide."
keywords: "o Visual f #, f #, funcional de programação, o vscode .NET, o código do Visual Studio, Ionide"
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a><span data-ttu-id="1f24c-104">Guia de Introdução com F # em código do Visual Studio com Ionide</span><span class="sxs-lookup"><span data-stu-id="1f24c-104">Getting Started with F# in Visual Studio Code with Ionide</span></span>

<span data-ttu-id="1f24c-105">Você pode escrever F # em [código do Visual Studio](https://code.visualstudio.com) com o [Ionide plug-in](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), para obter uma ótima experiência IDE de leve e de plataforma cruzada com o IntelliSense e refatorações código básico.</span><span class="sxs-lookup"><span data-stu-id="1f24c-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="1f24c-106">Visite [Ionide.io](http://ionide.io) para saber mais sobre o conjunto de plug-in.</span><span class="sxs-lookup"><span data-stu-id="1f24c-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f24c-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1f24c-107">Prerequisites</span></span>

<span data-ttu-id="1f24c-108">F # 4.0 ou superior deve ser instalado em seu computador para usar Ionide.</span><span class="sxs-lookup"><span data-stu-id="1f24c-108">F# 4.0 or higher must be installed on your machine to use Ionide.</span></span>

<span data-ttu-id="1f24c-109">Você também deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso dos modelos de projeto em Ionide.</span><span class="sxs-lookup"><span data-stu-id="1f24c-109">You must also have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="1f24c-110">Você pode verificar se ele está instalado corretamente, digitando `git` em um pressionamento de prompt.and comando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1f24c-110">You can verify that it is installed correctly by typing `git` at a command prompt.and pressing **Enter**.</span></span>

### <a name="windows"></a><span data-ttu-id="1f24c-111">Windows</span><span class="sxs-lookup"><span data-stu-id="1f24c-111">Windows</span></span>

<span data-ttu-id="1f24c-112">Se você estiver no Windows, você tem duas opções para a instalação do F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-112">If you're on Windows, you have two options for installing F#.</span></span>

<span data-ttu-id="1f24c-113">Se você já tiver instalado o Visual Studio e não tiver F #, você pode [instalar o Visual F # Tools](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="1f24c-113">If you've already installed Visual Studio and don't have F#, you can [Install the Visual F# Tools](get-started-visual-studio.md#installing-f).</span></span>  <span data-ttu-id="1f24c-114">Isso instalará todos os componentes necessários para escrever, compilar e executar código F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-114">This will install all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="1f24c-115">Se você preferir não instalar o Visual Studio, use as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f24c-115">If you prefer not to install Visual Studio, use the following instructions:</span></span>

1. <span data-ttu-id="1f24c-116">Instalar [do .NET Framework 4.5 ou superior](https://www.microsoft.com/en-US/download/details.aspx?id=30653) se você estiver executando o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="1f24c-116">Install [.NET Framework 4.5 or higher](https://www.microsoft.com/en-US/download/details.aspx?id=30653) if you're running Windows 7.</span></span>  <span data-ttu-id="1f24c-117">Se você estiver usando o Windows 8 ou superior, você não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1f24c-117">If you're using Windows 8 or higher, you do not need to do this.</span></span>

2. <span data-ttu-id="1f24c-118">Instale o SDK do Windows para o seu sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="1f24c-118">Install the Windows SDK for your OS:</span></span>

    * [<span data-ttu-id="1f24c-119">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1f24c-119">Windows 10 SDK</span></span>](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [<span data-ttu-id="1f24c-120">Windows 8.1 SDK</span><span class="sxs-lookup"><span data-stu-id="1f24c-120">Windows 8.1 SDK</span></span>](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [<span data-ttu-id="1f24c-121">Windows 8 SDK</span><span class="sxs-lookup"><span data-stu-id="1f24c-121">Windows 8 SDK</span></span>](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [<span data-ttu-id="1f24c-122">Windows 7 SDK</span><span class="sxs-lookup"><span data-stu-id="1f24c-122">Windows 7 SDK</span></span>](http://www.microsoft.com/download/details.aspx?id=8279)

3. <span data-ttu-id="1f24c-123">Instalar o [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span><span class="sxs-lookup"><span data-stu-id="1f24c-123">Install the [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span></span>  <span data-ttu-id="1f24c-124">Você também precisa instalar [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span><span class="sxs-lookup"><span data-stu-id="1f24c-124">You may also need to install [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span></span>

4. <span data-ttu-id="1f24c-125">Instalar o [ferramentas Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span><span class="sxs-lookup"><span data-stu-id="1f24c-125">Install the [Visual F# Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span></span>

<span data-ttu-id="1f24c-126">No Windows de 64 bits, o compilador e ferramentas estão localizadas aqui:</span><span class="sxs-lookup"><span data-stu-id="1f24c-126">On 64-bit Windows, the compiler and tools are located here:</span></span>

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="1f24c-127">No Windows de 32 bits, as ferramentas de compilador estão localizadas aqui:</span><span class="sxs-lookup"><span data-stu-id="1f24c-127">On 32-bit Windows, the compiler tools are located here:</span></span>

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="1f24c-128">Ionide detecta automaticamente o compilador e ferramentas, mas se ele não por algum motivo (por exemplo, o Visual F # Tools foi instalado para um diretório diferente), você pode adicionar manualmente a pasta que contém (`...\Microsoft SDKs\F#\4.0`) ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="1f24c-128">Ionide automatically detects the compiler and tools, but if it doesn't for some reason (for example, the Visual F# Tools were installed to a different directory), you can manually add the containing folder (`...\Microsoft SDKs\F#\4.0`) to your PATH.</span></span>

### <a name="macos"></a><span data-ttu-id="1f24c-129">macOS</span><span class="sxs-lookup"><span data-stu-id="1f24c-129">macOS</span></span>

<span data-ttu-id="1f24c-130">Em macOS, usa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="1f24c-130">On macOS, Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="1f24c-131">A maneira mais fácil de instalar Mono em macOS é por meio de Homebrew.</span><span class="sxs-lookup"><span data-stu-id="1f24c-131">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="1f24c-132">Simplesmente digite o seguinte em seu terminal:</span><span class="sxs-lookup"><span data-stu-id="1f24c-132">Simply type the following into your terminal:</span></span>

```
brew install mono
```

### <a name="linux"></a><span data-ttu-id="1f24c-133">Linux</span><span class="sxs-lookup"><span data-stu-id="1f24c-133">Linux</span></span>

<span data-ttu-id="1f24c-134">No Linux, Ionide também usa [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="1f24c-134">On Linux, Ionide also uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="1f24c-135">Se você estiver em Debian ou Ubuntu, você pode usar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-135">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="1f24c-136">Instalando o plug-in Ionide e código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f24c-136">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="1f24c-137">Você pode instalar o Visual Studio Code do [code.visualstudio.com](https://code.visualstudio.com) site.</span><span class="sxs-lookup"><span data-stu-id="1f24c-137">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>  <span data-ttu-id="1f24c-138">Depois disso, há duas maneiras de localizar o plug-in Ionide:</span><span class="sxs-lookup"><span data-stu-id="1f24c-138">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="1f24c-139">Use a paleta de comando (Ctrl + Shift + P no Windows, ⌘ + Shift + P em macOS, Ctrl + Shift + P no Linux) e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-139">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="1f24c-140">Clique no ícone de extensões e procure "Ionide":</span><span class="sxs-lookup"><span data-stu-id="1f24c-140">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="1f24c-141">O plug-in somente necessário para suporte a F # no código do Visual Studio é [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="1f24c-141">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>  <span data-ttu-id="1f24c-142">No entanto, você também pode instalar [Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) e obter [FORJAR](http://fsharp.github.io/FAKE/) suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter [Paket](https://fsprojects.github.io/Paket/) suporte.</span><span class="sxs-lookup"><span data-stu-id="1f24c-142">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](http://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span>  <span data-ttu-id="1f24c-143">FORJAR e Paket são ferramentas de comunidade adicionais F # para desenvolver projetos e gerenciar as dependências, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1f24c-143">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="1f24c-144">Criando seu primeiro projeto com Ionide</span><span class="sxs-lookup"><span data-stu-id="1f24c-144">Creating your first project with Ionide</span></span>

<span data-ttu-id="1f24c-145">Para criar um novo projeto de F #, abra o código do Visual Studio em uma nova pasta (você pode nomeá-lo como desejar).</span><span class="sxs-lookup"><span data-stu-id="1f24c-145">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="1f24c-146">Em seguida, abra a paleta de comando (Ctrl + Shift + P no Windows, ⌘ + Shift + P em macOS, Ctrl + Shift + P no Linux) e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-146">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="1f24c-147">Isso é alimentado pelo [FORGE](https://github.com/fsharp-editing/Forge) projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-147">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="1f24c-148">Você deve ver algo parecido com isso:</span><span class="sxs-lookup"><span data-stu-id="1f24c-148">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="1f24c-149">Se você não vir o acima, tente atualizar modelos executando o seguinte comando na paleta de comando: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="1f24c-149">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="1f24c-150">Selecione "F #: novo projeto" acessando **Enter**, que levará você para esta etapa:</span><span class="sxs-lookup"><span data-stu-id="1f24c-150">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="1f24c-151">Isso irá selecionar um modelo para um tipo específico de projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-151">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="1f24c-152">Há algumas opções aqui, como um [FsLab](http://fslab.org) modelo para ciência de dados ou [Suave](https://suave.io) modelo de programação da Web.</span><span class="sxs-lookup"><span data-stu-id="1f24c-152">There are quite a few options here, such as an [FsLab](http://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="1f24c-153">Este artigo usa o `classlib` modelo, para realçar que e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1f24c-153">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="1f24c-154">Em seguida, você vai chegar a etapa a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f24c-154">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="1f24c-155">Isso permite que você criar o projeto em um diretório diferente, se desejar.</span><span class="sxs-lookup"><span data-stu-id="1f24c-155">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="1f24c-156">Deixe em branco por enquanto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-156">Leave it blank for now.</span></span>  <span data-ttu-id="1f24c-157">Ele criará o projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1f24c-157">It will create the project in the current directory.</span></span>  <span data-ttu-id="1f24c-158">Depois que você pressionar **Enter**, você vai chegar a etapa a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f24c-158">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="1f24c-159">Permite que você nomeie seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-159">This lets you name your project.</span></span>  <span data-ttu-id="1f24c-160">F # usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para os nomes de projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-160">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="1f24c-161">Este artigo usa `ClassLibraryDemo` como o nome.</span><span class="sxs-lookup"><span data-stu-id="1f24c-161">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="1f24c-162">Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1f24c-162">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="1f24c-163">Se você seguiu as etapas da etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo para algo parecido com isto:</span><span class="sxs-lookup"><span data-stu-id="1f24c-163">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="1f24c-164">Esse modelo gera algumas coisas que você encontrará úteis:</span><span class="sxs-lookup"><span data-stu-id="1f24c-164">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="1f24c-165">O F # projeto em si, sob o `ClassLibraryDemo` pasta.</span><span class="sxs-lookup"><span data-stu-id="1f24c-165">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="1f24c-166">A estrutura de diretório correto para a adição de pacotes por meio de [ `Paket` ](http://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="1f24c-166">The correct directory structure for adding packages via [`Paket`](http://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="1f24c-167">Uma plataforma cruzada criar script com [ `FAKE` ](http://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="1f24c-167">A cross-platform build script with [`FAKE`](http://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="1f24c-168">O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.</span><span class="sxs-lookup"><span data-stu-id="1f24c-168">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="1f24c-169">Um `.gitignore` de arquivo se deseja adicionar este projeto ao controle de origem com base no Git.</span><span class="sxs-lookup"><span data-stu-id="1f24c-169">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="1f24c-170">Escrevendo um código</span><span class="sxs-lookup"><span data-stu-id="1f24c-170">Writing some code</span></span>

<span data-ttu-id="1f24c-171">Abra o *ClassLibraryDemo* pasta.</span><span class="sxs-lookup"><span data-stu-id="1f24c-171">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="1f24c-172">Você deve ver os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="1f24c-172">You should see the following files:</span></span>

1. <span data-ttu-id="1f24c-173">`ClassLibraryDemo.fs`, um arquivo de implementação do F # com uma classe definida.</span><span class="sxs-lookup"><span data-stu-id="1f24c-173">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="1f24c-174">`CassLibraryDemo.fsproj`, um arquivo de projeto F # usado para compilar este projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-174">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="1f24c-175">`Script.fsx`, um arquivo de script F # que carrega o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="1f24c-175">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="1f24c-176">`paket.references`, um arquivo Paket que especifica as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-176">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="1f24c-177">Abra `Script.fsx`e adicione o seguinte código ao final dele:</span><span class="sxs-lookup"><span data-stu-id="1f24c-177">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="1f24c-178">Esta função converte uma palavra em uma forma de [Pig latino](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="1f24c-178">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="1f24c-179">A próxima etapa é avaliar usando F # interativo (FSI).</span><span class="sxs-lookup"><span data-stu-id="1f24c-179">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="1f24c-180">Realce a função inteira (deve ser 11 linhas).</span><span class="sxs-lookup"><span data-stu-id="1f24c-180">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="1f24c-181">Depois de selecioná-la, mantenha o **Alt** chave e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1f24c-181">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="1f24c-182">Você observará que uma janela pop-up abaixo, e ele deverá mostrar algo assim:</span><span class="sxs-lookup"><span data-stu-id="1f24c-182">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="1f24c-183">Isso foi três coisas:</span><span class="sxs-lookup"><span data-stu-id="1f24c-183">This did three things:</span></span>

1. <span data-ttu-id="1f24c-184">Iniciar o processo de FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-184">It started the FSI process.</span></span>
2. <span data-ttu-id="1f24c-185">Ele enviado o código realçado sobre o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-185">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="1f24c-186">O processo FSI avaliado o código enviados pela.</span><span class="sxs-lookup"><span data-stu-id="1f24c-186">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="1f24c-187">Porque foi enviado por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI!</span><span class="sxs-lookup"><span data-stu-id="1f24c-187">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="1f24c-188">Na janela interativa, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-188">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="1f24c-189">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="1f24c-189">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="1f24c-190">Agora, vamos tentar com uma vogal como a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="1f24c-190">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="1f24c-191">Insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-191">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="1f24c-192">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="1f24c-192">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="1f24c-193">A função parece estar funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="1f24c-193">The function appears to be working as expected.</span></span>  <span data-ttu-id="1f24c-194">Parabéns, você criou sua primeira função F # em código do Visual Studio e avaliadas-lo com FSI apenas!</span><span class="sxs-lookup"><span data-stu-id="1f24c-194">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="1f24c-195">Como você pode ter observado, as linhas no FSI são finalizadas com `;;`.</span><span class="sxs-lookup"><span data-stu-id="1f24c-195">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="1f24c-196">Isso ocorre porque FSI permite que você insira várias linhas.</span><span class="sxs-lookup"><span data-stu-id="1f24c-196">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="1f24c-197">O `;;` no final permite FSI saber quando o código for concluído.</span><span class="sxs-lookup"><span data-stu-id="1f24c-197">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="1f24c-198">Explicando o código</span><span class="sxs-lookup"><span data-stu-id="1f24c-198">Explaining the code</span></span>

<span data-ttu-id="1f24c-199">Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.</span><span class="sxs-lookup"><span data-stu-id="1f24c-199">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="1f24c-200">Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e o converte em uma representação de Pig-latino da palavra.</span><span class="sxs-lookup"><span data-stu-id="1f24c-200">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="1f24c-201">As regras para isso são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1f24c-201">The rules for this are as follows:</span></span>

<span data-ttu-id="1f24c-202">Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" para o fim da palavra.</span><span class="sxs-lookup"><span data-stu-id="1f24c-202">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="1f24c-203">Se ele não começa com uma vogal, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="1f24c-203">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="1f24c-204">Você pode ter observado FSI o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1f24c-204">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="1f24c-205">Isso indica que `toPigLatin` é uma função que aceita um `string` como entrada (chamado `word`) e retorna outro `string`.</span><span class="sxs-lookup"><span data-stu-id="1f24c-205">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="1f24c-206">Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da linguagem F # que é a chave para compreender o código F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-206">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="1f24c-207">Você também observa isso se você passar o mouse sobre a função no código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f24c-207">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="1f24c-208">O corpo da função, você observará duas partes distintas:</span><span class="sxs-lookup"><span data-stu-id="1f24c-208">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="1f24c-209">Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="1f24c-209">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="1f24c-210">Um [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno sem os caracteres de entrada com base em se o primeiro caractere a expressão era uma vogal ou não:</span><span class="sxs-lookup"><span data-stu-id="1f24c-210">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="1f24c-211">O fluxo de `toPigLatin` é assim:</span><span class="sxs-lookup"><span data-stu-id="1f24c-211">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="1f24c-212">Verifique se o primeiro caractere da palavra entrada é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="1f24c-212">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="1f24c-213">Se for, anexe "Sim" para o fim da palavra.</span><span class="sxs-lookup"><span data-stu-id="1f24c-213">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="1f24c-214">Caso contrário, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="1f24c-214">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="1f24c-215">Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas lá.</span><span class="sxs-lookup"><span data-stu-id="1f24c-215">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="1f24c-216">Isso ocorre porque o F # é baseada em expressão, e a última expressão no corpo de uma função é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="1f24c-216">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="1f24c-217">Porque `if..then..else` em si for uma expressão, o corpo do `then` bloco ou o corpo do `else` bloco será retornado, dependendo do valor de entrada.</span><span class="sxs-lookup"><span data-stu-id="1f24c-217">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="1f24c-218">Movendo o código de script para o arquivo de implementação</span><span class="sxs-lookup"><span data-stu-id="1f24c-218">Moving your script code into the implementation file</span></span>

<span data-ttu-id="1f24c-219">As seções anteriores neste artigo demonstrou uma primeira etapa comum gravar código F #: gravar uma função inicial e executá-la interativamente com FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-219">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="1f24c-220">Isso é conhecido como o desenvolvimento controlado por REPL, onde REPL significa "Loop de impressão avaliar leitura".</span><span class="sxs-lookup"><span data-stu-id="1f24c-220">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="1f24c-221">É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="1f24c-221">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="1f24c-222">A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho em um arquivo de implementação do F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-222">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="1f24c-223">Ele então pode ser compilado pelo compilador F # em um assembly que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="1f24c-223">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="1f24c-224">Para começar, abra `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="1f24c-224">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="1f24c-225">Você observará que algum código já está em lá.</span><span class="sxs-lookup"><span data-stu-id="1f24c-225">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="1f24c-226">Vá em frente e excluir a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.</span><span class="sxs-lookup"><span data-stu-id="1f24c-226">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="1f24c-227">Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:</span><span class="sxs-lookup"><span data-stu-id="1f24c-227">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="1f24c-228">Essa é uma das várias maneiras que você pode organizar funções no código F # e uma abordagem comum, se você deseja chamar o código do c# ou projetos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f24c-228">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="1f24c-229">Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionarão, mas certifique-se de manter as duas linhas seguintes no arquivo:</span><span class="sxs-lookup"><span data-stu-id="1f24c-229">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="1f24c-230">A primeira linha é necessária para FSI script para carregar `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="1f24c-230">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="1f24c-231">A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo no escopo.</span><span class="sxs-lookup"><span data-stu-id="1f24c-231">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="1f24c-232">Em seguida, na janela FSI, chame a função com o `PigLatin` módulo definido anteriormente:</span><span class="sxs-lookup"><span data-stu-id="1f24c-232">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="1f24c-233">Sucesso!</span><span class="sxs-lookup"><span data-stu-id="1f24c-233">Success!</span></span>  <span data-ttu-id="1f24c-234">Obter os mesmos resultados como antes, mas agora carregado de um arquivo de implementação do F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-234">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="1f24c-235">A principal diferença é que os arquivos de origem F # são compilados em assemblies que podem ser executados em qualquer lugar, não apenas em FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-235">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="1f24c-236">Resumo</span><span class="sxs-lookup"><span data-stu-id="1f24c-236">Summary</span></span>

<span data-ttu-id="1f24c-237">Neste artigo, você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="1f24c-237">In this article, you've learned:</span></span>

1. <span data-ttu-id="1f24c-238">Como configurar o código do Visual Studio com Ionide.</span><span class="sxs-lookup"><span data-stu-id="1f24c-238">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="1f24c-239">Como criar seu primeiro projeto F # com Ionide.</span><span class="sxs-lookup"><span data-stu-id="1f24c-239">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="1f24c-240">Como usar o F # script para gravar sua primeira função F # em Ionide e, em seguida, execute-o no FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-240">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="1f24c-241">Como migrar o código de script com fonte de F # e, em seguida, chamar esse código de FSI.</span><span class="sxs-lookup"><span data-stu-id="1f24c-241">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="1f24c-242">Você agora está pronto para escrever muito mais código F #, usando o código do Visual Studio e Ionide.</span><span class="sxs-lookup"><span data-stu-id="1f24c-242">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="1f24c-243">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="1f24c-243">Troubleshooting</span></span>

<span data-ttu-id="1f24c-244">Aqui estão algumas maneiras que você pode solucionar determinados problemas que possam ser executadas em:</span><span class="sxs-lookup"><span data-stu-id="1f24c-244">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="1f24c-245">Para obter recursos de Ionide de edição de código, os arquivos de F # precisam ser salvo em disco e dentro de uma pasta que está aberta no espaço de trabalho de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f24c-245">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="1f24c-246">Se tiver sido feitas alterações no sistema ou instalado Ionide pré-requisitos com código do Visual Studio abrir, reinicie o código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f24c-246">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="1f24c-247">Verifique que você pode usar o compilador F # e F # interativo da linha de comando sem um caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="1f24c-247">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="1f24c-248">Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador de F #, e `fsi` ou `fsharpi` para o Visual F # ferramentas no Windows e Mono no Mac/Linux, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1f24c-248">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="1f24c-249">Se você tem caracteres inválidos em seus diretórios de projeto, Ionide podem não funcionar.</span><span class="sxs-lookup"><span data-stu-id="1f24c-249">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="1f24c-250">Se esse for o caso, renomeie os diretórios do projeto.</span><span class="sxs-lookup"><span data-stu-id="1f24c-250">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="1f24c-251">Se nenhum dos comandos Ionide está trabalhando, verifique seu [associações de código do Visual Studio](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por engano.</span><span class="sxs-lookup"><span data-stu-id="1f24c-251">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="1f24c-252">Se Ionide é dividido em seu computador e nenhum deles corrigiu o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o conjunto de plug-in.</span><span class="sxs-lookup"><span data-stu-id="1f24c-252">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="1f24c-253">Ionide é um projeto de código aberto criado e mantido por membros da comunidade do F #.</span><span class="sxs-lookup"><span data-stu-id="1f24c-253">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="1f24c-254">Reportar problemas e fique à vontade para contribuir no [Ionide-o VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="1f24c-254">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="1f24c-255">Se você tiver um problema ao relatório, siga [as instruções para obter logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="1f24c-255">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="1f24c-256">Você também pode pedir para obter ajuda da comunidade do F # em e desenvolvedores Ionide o [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="1f24c-256">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f24c-257">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1f24c-257">Next steps</span></span>

<span data-ttu-id="1f24c-258">Para saber mais sobre F # e os recursos do idioma, check-out [Tour do F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="1f24c-258">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f24c-259">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f24c-259">See also</span></span>

[<span data-ttu-id="1f24c-260">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="1f24c-260">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="1f24c-261">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="1f24c-261">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="1f24c-262">Funções</span><span class="sxs-lookup"><span data-stu-id="1f24c-262">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="1f24c-263">Módulos</span><span class="sxs-lookup"><span data-stu-id="1f24c-263">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="1f24c-264">Namespaces</span><span class="sxs-lookup"><span data-stu-id="1f24c-264">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="1f24c-265">O VSCode do Ionide: FSharp</span><span class="sxs-lookup"><span data-stu-id="1f24c-265">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)