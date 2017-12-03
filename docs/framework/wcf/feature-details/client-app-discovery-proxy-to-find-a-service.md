---
title: "Como implementar um aplicativo cliente que utiliza o proxy de descoberta para encontrar um serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62b41a75-cf40-4c52-a842-a5f1c70e247f
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09c75ff3c19110a4ed97d8b95a4f63174cba0406
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-application-that-uses-the-discovery-proxy-to-find-a-service"></a><span data-ttu-id="a5fcc-102">Como implementar um aplicativo cliente que utiliza o proxy de descoberta para encontrar um serviço</span><span class="sxs-lookup"><span data-stu-id="a5fcc-102">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>
<span data-ttu-id="a5fcc-103">Este tópico é o terceiro de três tópicos que descreve como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-103">This topic is the third of three topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="a5fcc-104">No tópico anterior, [como: implementar um serviço de descoberta que registra com o Proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md), você já implementou um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que é registrado com o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-104">In the previous topic, [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers itself with the discovery proxy.</span></span> <span data-ttu-id="a5fcc-105">Neste tópico, você cria um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que usa o proxy de descoberta para localizar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-105">In this topic you create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that uses the discovery proxy to find the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="implement-the-client"></a><span data-ttu-id="a5fcc-106">Implementar o cliente</span><span class="sxs-lookup"><span data-stu-id="a5fcc-106">Implement the client</span></span>  
  
1.  <span data-ttu-id="a5fcc-107">Adicionar um novo projeto de aplicativo de console para o `DiscoveryProxyExample` solução chamada `Client`.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Client`.</span></span>  
  
2.  <span data-ttu-id="a5fcc-108">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5fcc-108">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="a5fcc-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a5fcc-109">System.ServiceModel</span></span>  
  
    2.  <span data-ttu-id="a5fcc-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="a5fcc-110">System.ServiceModel.Discovery</span></span>  
  
3.  <span data-ttu-id="a5fcc-111">Adicione o GeneratedClient.cs localizado na parte inferior deste tópico para o projeto.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-111">Add the GeneratedClient.cs found at the bottom of this topic to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5fcc-112">Esse arquivo normalmente é gerado usando uma ferramenta como Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-112">This file is usually generated using a tool such as Svcutil.exe.</span></span> <span data-ttu-id="a5fcc-113">Ele é fornecido neste tópico para simplificar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-113">It is provided in this topic to simplify the task.</span></span>  
  
4.  <span data-ttu-id="a5fcc-114">Abra o arquivo Program.cs e adicione o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-114">Open the Program.cs file and add the following method.</span></span> <span data-ttu-id="a5fcc-115">Esse método usa um endereço de ponto de extremidade e usa para inicializar o cliente do serviço (proxy).</span><span class="sxs-lookup"><span data-stu-id="a5fcc-115">This method takes an endpoint address and uses it to initialize the service client (proxy).</span></span>  
  
    ```  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
            {  
                // Create a client  
                CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
                Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
                Console.WriteLine();  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                // Call the Add service operation.  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
                Console.WriteLine();  
  
                // Closing the client gracefully closes the connection and cleans up resources  
                client.Close();  
            }  
    ```  
  
5.  <span data-ttu-id="a5fcc-116">Adicione o seguinte código ao método de `Main` .</span><span class="sxs-lookup"><span data-stu-id="a5fcc-116">Add the following code to the `Main` method.</span></span>  
  
    ```  
    public static void Main()  
            {  
                // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
                Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
  
                // Create a DiscoveryClient passing in the discovery endpoint  
                DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  
  
                Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
                Console.WriteLine();  
  
                try  
                {  
                    // Search for services that implement ICalculatorService              
                    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  
  
                    Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
                    Console.WriteLine();  
  
                    // Check to see if endpoints were found, if so then invoke the service.  
                    if (findResponse.Endpoints.Count > 0)  
                    {  
                        InvokeCalculatorService(findResponse.Endpoints[0].Address);  
                    }  
                }  
                catch (TargetInvocationException)  
                {  
                    Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
                }  
  
                Console.WriteLine("Press <ENTER> to exit.");  
                Console.ReadLine();  
            }  
    ```  
  
 <span data-ttu-id="a5fcc-117">Você concluiu a implementação do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-117">You have completed implementing the client application.</span></span> <span data-ttu-id="a5fcc-118">Continue no [como: testar o Proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="a5fcc-118">Continue on to [How to: Test the Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5fcc-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5fcc-119">Example</span></span>  
 <span data-ttu-id="a5fcc-120">É o código completo listando deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a5fcc-120">This is the full code listing for this topic.</span></span>  
  
```  
// GeneratedClient.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1434  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace Microsoft.Samples.Discovery  
{  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.Samples.Discovery", ConfigurationName = "ICalculatorService")]  
    public interface ICalculatorService  
    {  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Add", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/AddResponse")]  
        double Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Subtract", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/SubtractResponse")]  
        double Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Multiply", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/MultiplyResponse")]  
        double Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Divide", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/DivideResponse")]  
        double Divide(double n1, double n2);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public interface ICalculatorServiceChannel : ICalculatorService, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public partial class CalculatorServiceClient : System.ServiceModel.ClientBase<ICalculatorService>, ICalculatorService  
    {  
  
        public CalculatorServiceClient()  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName) :  
            base(endpointConfigurationName)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, string remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(binding, remoteAddress)  
        {  
        }  
  
        public double Add(double n1, double n2)  
        {  
            return base.Channel.Add(n1, n2);  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            return base.Channel.Subtract(n1, n2);  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            return base.Channel.Multiply(n1, n2);  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            return base.Channel.Divide(n1, n2);  
        }  
    }  
}  
```  
  
```  
// Program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Reflection;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Client  
    {  
        public static void Main()  
        {  
            // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
  
            DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  
  
            Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
            Console.WriteLine();  
  
            try  
            {  
                // Find ICalculatorService endpoints              
                FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  
  
                Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
                Console.WriteLine();  
  
                // Check to see if endpoints were found, if so then invoke the service.  
                if (findResponse.Endpoints.Count > 0)  
                {  
                    InvokeCalculatorService(findResponse.Endpoints[0].Address);  
                }  
            }  
            catch (TargetInvocationException)  
            {  
                Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
            Console.WriteLine();  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            // Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5fcc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5fcc-121">See Also</span></span>  
 [<span data-ttu-id="a5fcc-122">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="a5fcc-122">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="a5fcc-123">Como: implementar um Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="a5fcc-123">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="a5fcc-124">Como: implementar um serviço de descoberta que registra com o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="a5fcc-124">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)