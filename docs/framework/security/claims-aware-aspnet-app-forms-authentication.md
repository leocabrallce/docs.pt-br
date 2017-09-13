---
title: "Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação Baseada em Formulários"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: 6
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 987157bc3663330d9c610c1016787890e9dc6137
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="13461-102">Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação Baseada em Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="13461-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="13461-103">Applies To</span></span>  
  
-   <span data-ttu-id="13461-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="13461-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="13461-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="13461-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="13461-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="13461-106">Summary</span></span>  
 <span data-ttu-id="13461-107">Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET Web Forms simples baseado em declarações que usa a autenticação de Formulários.</span><span class="sxs-lookup"><span data-stu-id="13461-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="13461-108">Também fornece instruções sobre como testar o aplicativo para verificar se as declarações são apresentadas quando um usuário se conecta usando a autenticação de Formulários.</span><span class="sxs-lookup"><span data-stu-id="13461-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="13461-109">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="13461-109">Contents</span></span>  
  
-   <span data-ttu-id="13461-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="13461-110">Objectives</span></span>  
  
-   <span data-ttu-id="13461-111">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="13461-111">Overview</span></span>  
  
-   <span data-ttu-id="13461-112">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="13461-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="13461-113">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="13461-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="13461-114">Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="13461-115">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="13461-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="13461-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="13461-116">Objectives</span></span>  
  
-   <span data-ttu-id="13461-117">Configurar um aplicativo ASP.NET Web Forms para declarações usando a autenticação de Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="13461-118">Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente</span><span class="sxs-lookup"><span data-stu-id="13461-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="13461-119">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="13461-119">Overview</span></span>  
 <span data-ttu-id="13461-120">No .NET 4.5, o WIF e sua autorização baseada em declarações foram incluídos como parte integrante do Framework.</span><span class="sxs-lookup"><span data-stu-id="13461-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="13461-121">Anteriormente, se você quisesse obter declarações de um usuário do ASP.NET, precisava instalar o WIF e, em seguida, converter as interfaces para objetos de Entidade de Segurança, como `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="13461-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="13461-122">Agora, as declarações são atendidas automaticamente por esses objetos de Entidade de Segurança.</span><span class="sxs-lookup"><span data-stu-id="13461-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="13461-123">A autenticação de Formulários se beneficiou com a inclusão do WIF no .NET 4.5, porque todos os usuários autenticados pelas credenciais de Formulários têm declarações associadas a eles automaticamente.</span><span class="sxs-lookup"><span data-stu-id="13461-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="13461-124">Comece a usar essas declarações imediatamente em um aplicativo ASP.NET que usa a autenticação de Formulários, conforme demonstrado por estas Instruções.</span><span class="sxs-lookup"><span data-stu-id="13461-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="13461-125">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="13461-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="13461-126">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="13461-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="13461-127">Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="13461-128">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="13461-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="13461-129">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="13461-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="13461-130">Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="13461-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="13461-131">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="13461-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="13461-132">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="13461-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="13461-133">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="13461-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="13461-134">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="13461-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="13461-135">Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="13461-136">Nesta etapa, você adicionará uma entrada de configuração ao arquivo de configuração *Web.config* e edite o arquivo *Default.aspx* para exibir as informações de declarações de uma conta.</span><span class="sxs-lookup"><span data-stu-id="13461-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="13461-137">Para configurar um aplicativo ASP.NET para declarações usando a autenticação de Formulários</span><span class="sxs-lookup"><span data-stu-id="13461-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="13461-138">No arquivo *Default.aspx*, substitua a marcação existente pela seguinte:</span><span class="sxs-lookup"><span data-stu-id="13461-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="13461-139">Essa etapa adiciona um controle GridView à página *Default.aspx* que será populada com as declarações recuperadas da autenticação de Formulários.</span><span class="sxs-lookup"><span data-stu-id="13461-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="13461-140">Salve o arquivo *Default.aspx* e, depois, abra seu arquivo code-behind chamado *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="13461-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="13461-141">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="13461-141">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="13461-142">O código acima exibirá declarações sobre um usuário autenticado, incluindo os usuários identificados pela autenticação de Formulários.</span><span class="sxs-lookup"><span data-stu-id="13461-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="13461-143">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="13461-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="13461-144">Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação de formulários.</span><span class="sxs-lookup"><span data-stu-id="13461-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="13461-145">Testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação de formulários</span><span class="sxs-lookup"><span data-stu-id="13461-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="13461-146">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13461-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="13461-147">Você deverá ver o *Default.aspx*, que tem os links **Registrar** e **Fazer logon** na parte superior direita da página.</span><span class="sxs-lookup"><span data-stu-id="13461-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="13461-148">Clique em **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="13461-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="13461-149">Na página **Registrar**, crie uma conta de usuário e, em seguida, clique em **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="13461-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="13461-150">Sua conta será criada usando a autenticação de Formulários e você será conectado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="13461-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="13461-151">Depois de ser redirecionado para a home page, você deverá ver uma tabela abaixo do cabeçalho **Suas Declarações**, que inclui as informações das declarações **Issuer**, **OriginalIssuer**, **Type**, **Value** e **ValueType** sobre sua conta.</span><span class="sxs-lookup"><span data-stu-id="13461-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
