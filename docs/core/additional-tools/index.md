---
title: Ferramentas adicionais do .NET Core
description: Uma visão geral das ferramentas adicionais que oferecem suporte e estendem a funcionalidade do .NET Core.
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 21fcc1190ee4586a8d7eb6fb8d63a7c312e63825
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="net-core-additional-tools"></a>Ferramentas adicionais do .NET Core

Esta seção compila uma lista de ferramentas de suporte e estender a funcionalidade do .NET Core, além das ferramentas da [CLI (interface de linha de comando) do .NET Core](..\tools\index.md).

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Ferramenta de Referência do Serviço Web do WCF](wcf-web-service-reference-guide.md)

A Referência do Serviço Web do WCF é um provedor de serviços conectados do Visual Studio que fez sua estreia no [Visual Studio 2017 versão 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL e gera um arquivo de fonte compatível com o .NET Core que contém o código de proxy de cliente do Windows Communication Foundation (WCF) que você pode usar para acessar esse serviço Web.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é a solução para bibliotecas .NET Core e .NET Standard. Ele cria um assembly de serialização de XML para tipos contidos em um assembly para melhorar o desempenho de inicialização de serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.