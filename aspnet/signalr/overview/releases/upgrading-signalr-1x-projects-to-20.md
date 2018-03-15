---
uid: signalr/overview/releases/upgrading-signalr-1x-projects-to-20
title: "Actualizar proyectos de 1.x de SignalR a la versión 2 | Documentos de Microsoft"
author: pfletcher
description: "Este tema describe cómo actualizar un proyecto existente de 1.x de SignalR a SignalR 2.x y cómo solucionar problemas que pueden surgir durante el proceso de actualización..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/10/2014
ms.topic: article
ms.assetid: adcfef99-9bc5-489d-a91b-9b7c2bc35e04
ms.technology: dotnet-signalr
ms.prod: .net-framework
msc.legacyurl: /signalr/overview/releases/upgrading-signalr-1x-projects-to-20
msc.type: authoredcontent
ms.openlocfilehash: e372275ae5dd4bbf354db2d02e4407f8c513b7a3
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2017
---
<a name="upgrading-signalr-1x-projects-to-version-2"></a><span data-ttu-id="5e1b6-103">Actualización de proyectos de 1.x SignalR a la versión 2</span><span class="sxs-lookup"><span data-stu-id="5e1b6-103">Upgrading SignalR 1.x Projects to version 2</span></span>
====================
<span data-ttu-id="5e1b6-104">por [Patrick Fletcher](https://github.com/pfletcher)</span><span class="sxs-lookup"><span data-stu-id="5e1b6-104">by [Patrick Fletcher](https://github.com/pfletcher)</span></span>

> <span data-ttu-id="5e1b6-105">Este tema describe cómo actualizar un proyecto existente de 1.x de SignalR a SignalR 2.x y cómo solucionar problemas que pueden surgir durante el proceso de actualización.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-105">This topic describes how to upgrade an existing SignalR 1.x project to SignalR 2.x, and how to troubleshoot issues that may arise during the upgrade process.</span></span>
> 
> ## <a name="software-versions-used-in-the-tutorial"></a><span data-ttu-id="5e1b6-106">Versiones de software que se usa en el tutorial</span><span class="sxs-lookup"><span data-stu-id="5e1b6-106">Software versions used in the tutorial</span></span>
> 
> 
> - [<span data-ttu-id="5e1b6-107">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="5e1b6-107">Visual Studio 2013</span></span>](https://www.microsoft.com/visualstudio/eng/2013-downloads)
> - <span data-ttu-id="5e1b6-108">.NET 4.5</span><span class="sxs-lookup"><span data-stu-id="5e1b6-108">.NET 4.5</span></span>
> - <span data-ttu-id="5e1b6-109">Versiones 1 y 2 de SignalR</span><span class="sxs-lookup"><span data-stu-id="5e1b6-109">SignalR versions 1 and 2</span></span>
>   
> 
> 
> ## <a name="using-visual-studio-2012-with-this-tutorial"></a><span data-ttu-id="5e1b6-110">Uso de Visual Studio 2012 con este tutorial</span><span class="sxs-lookup"><span data-stu-id="5e1b6-110">Using Visual Studio 2012 with this tutorial</span></span>
> 
> 
> <span data-ttu-id="5e1b6-111">Para usar Visual Studio 2012 con este tutorial, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5e1b6-111">To use Visual Studio 2012 with this tutorial, do the following:</span></span>
> 
> - <span data-ttu-id="5e1b6-112">Actualización de su [el Administrador de paquetes](http://docs.nuget.org/docs/start-here/installing-nuget) a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-112">Update your [Package Manager](http://docs.nuget.org/docs/start-here/installing-nuget) to the latest version.</span></span>
> - <span data-ttu-id="5e1b6-113">Instalar el [instalador de plataforma Web](https://www.microsoft.com/web/downloads/platform.aspx).</span><span class="sxs-lookup"><span data-stu-id="5e1b6-113">Install the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span>
> - <span data-ttu-id="5e1b6-114">El instalador de plataforma Web, buscar e instalar **2013.1 de herramientas Web para Visual Studio 2012 y ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-114">In the Web Platform Installer, search for and install **ASP.NET and Web Tools 2013.1 for Visual Studio 2012**.</span></span> <span data-ttu-id="5e1b6-115">Esto instalará como plantillas de Visual Studio para las clases de SignalR **concentrador**.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-115">This will install Visual Studio templates for SignalR classes such as **Hub**.</span></span>
> - <span data-ttu-id="5e1b6-116">Algunas plantillas (como **clase de inicio de OWIN**) no estará disponible; para ello, utilice un archivo de clase en su lugar.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-116">Some templates (such as **OWIN Startup Class**) will not be available; for these, use a Class file instead.</span></span>
> 
> 
> ## <a name="questions-and-comments"></a><span data-ttu-id="5e1b6-117">Preguntas y comentarios</span><span class="sxs-lookup"><span data-stu-id="5e1b6-117">Questions and comments</span></span>
> 
> <span data-ttu-id="5e1b6-118">Vota sobre cómo le gustó este tutorial y lo que podemos mejorar en los comentarios en la parte inferior de la página.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-118">Please leave feedback on how you liked this tutorial and what we could improve in the comments at the bottom of the page.</span></span> <span data-ttu-id="5e1b6-119">Si tiene preguntas que no están directamente relacionados con el tutorial, puede publicar para la [foro de ASP.NET SignalR](https://forums.asp.net/1254.aspx/1?ASP+NET+SignalR) o [StackOverflow.com](http://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="5e1b6-119">If you have questions that are not directly related to the tutorial, you can post them to the [ASP.NET SignalR forum](https://forums.asp.net/1254.aspx/1?ASP+NET+SignalR) or [StackOverflow.com](http://stackoverflow.com/).</span></span>


<span data-ttu-id="5e1b6-120">SignalR 2 ofrece una experiencia de desarrollo coherente entre plataformas de servidor mediante [OWIN](http://owin.org).</span><span class="sxs-lookup"><span data-stu-id="5e1b6-120">SignalR 2 offers a consistent development experience across server platforms using [OWIN](http://owin.org).</span></span> <span data-ttu-id="5e1b6-121">Este artículo describen los pasos necesarios para actualizar una aplicación de 1.x SignalR a la versión 2.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-121">This article describes the few steps that are needed to update a SignalR 1.x application to version 2.</span></span>

<span data-ttu-id="5e1b6-122">Aunque se recomienda actualizar las aplicaciones al 2 de SignalR, SignalR sigue 1.x admitirse.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-122">While it is encouraged to upgrade applications to SignalR 2, SignalR 1.x will still be supported.</span></span>

<span data-ttu-id="5e1b6-123">Este tutorial describe cómo actualizar una aplicación hospedada en web al 2 de SignalR.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-123">This tutorial describes how to upgrade a web-hosted application to SignalR 2.</span></span> <span data-ttu-id="5e1b6-124">Las aplicaciones autohospedadas (aquellas que hospedan un servidor en una aplicación de consola, servicio de Windows u otro proceso) ahora se admiten en SignalR 2.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-124">Self-hosted applications (those that host a server in a console application, Windows service, or other process) are now supported under SignalR 2.</span></span> <span data-ttu-id="5e1b6-125">Para obtener información sobre cómo empezar a crear una aplicación autohospedada con SignalR 2, consulte [Tutorial: SignalR autohospedaje](../deployment/tutorial-signalr-self-host.md).</span><span class="sxs-lookup"><span data-stu-id="5e1b6-125">For information on how to get started creating a self-hosted application with SignalR 2, see [Tutorial: SignalR Self-Host](../deployment/tutorial-signalr-self-host.md).</span></span>

## <a name="contents"></a><span data-ttu-id="5e1b6-126">Contenido</span><span class="sxs-lookup"><span data-stu-id="5e1b6-126">Contents</span></span>

<span data-ttu-id="5e1b6-127">Las secciones siguientes describen las tareas relacionadas con la actualización de proyectos de SignalR y cómo solucionar problemas que pueden surgir.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-127">The following sections describe tasks involved with upgrading SignalR projects, and how to troubleshoot issues that may arise.</span></span>

- [<span data-ttu-id="5e1b6-128">Ejemplo: Actualizar el tutorial de introducción a SignalR 2</span><span class="sxs-lookup"><span data-stu-id="5e1b6-128">Example: Upgrading the Getting Started tutorial to SignalR 2</span></span>](#example)
- [<span data-ttu-id="5e1b6-129">Solución de problemas de errores encontrados durante la actualización</span><span class="sxs-lookup"><span data-stu-id="5e1b6-129">Troubleshooting errors encountered during upgrading</span></span>](#troubleshooting)

<a id="example"></a>

## <a name="example-upgrading-the-getting-started-tutorial-application-to-signalr-2"></a><span data-ttu-id="5e1b6-130">Ejemplo: Actualizar la aplicación de tutorial de introducción para SignalR 2</span><span class="sxs-lookup"><span data-stu-id="5e1b6-130">Example: Upgrading the Getting Started tutorial application to SignalR 2</span></span>

<span data-ttu-id="5e1b6-131">En esta sección, actualizará la aplicación creada en el [SignalR 1.x versión del Tutorial de introducción](../older-versions/index.md) utilizar 2 de SignalR.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-131">In this section, you'll update the application created in the [SignalR 1.x version of the Getting Started Tutorial](../older-versions/index.md) to use SignalR 2.</span></span>

1. <span data-ttu-id="5e1b6-132">Una vez que haya finalizado el tutorial de introducción, haga doble clic en el proyecto y seleccione **propiedades**.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-132">Once you've finished the Getting Started tutorial, right-click on the project, and select **Properties**.</span></span> <span data-ttu-id="5e1b6-133">Compruebe que la **.NET framework de destino** está establecido en **.NET Framework 4.5.**</span><span class="sxs-lookup"><span data-stu-id="5e1b6-133">Verify that the **Target framework** is set to **.NET Framework 4.5.**</span></span>
2. <span data-ttu-id="5e1b6-134">Abra la consola de administrador de paquetes.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-134">Open the Package Manager Console.</span></span> <span data-ttu-id="5e1b6-135">Quitar SignalR 1.x desde el proyecto con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="5e1b6-135">Remove SignalR 1.x from the project using the following command:</span></span>

    [!code-powershell[Main](upgrading-signalr-1x-projects-to-20/samples/sample1.ps1)]
3. <span data-ttu-id="5e1b6-136">Instalar el 2 de SignalR mediante el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5e1b6-136">Install SignalR 2 using the following command:</span></span>

    [!code-powershell[Main](upgrading-signalr-1x-projects-to-20/samples/sample2.ps1)]
4. <span data-ttu-id="5e1b6-137">En la página HTML, actualice la referencia de script para SignalR para que coincida con la versión de la secuencia de comandos que se incluye ahora en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-137">In the HTML page, update the script reference for SignalR to match the version of the script now included in the project.</span></span>

    [!code-html[Main](upgrading-signalr-1x-projects-to-20/samples/sample3.html)]
5. <span data-ttu-id="5e1b6-138">En la clase de aplicación global, quite la llamada a MapHubs.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-138">In the global application class, remove the call to MapHubs.</span></span>

    [!code-csharp[Main](upgrading-signalr-1x-projects-to-20/samples/sample4.cs)]
6. <span data-ttu-id="5e1b6-139">Haga clic en la solución y seleccione **agregar**, **nuevo elemento...** . En el cuadro de diálogo, seleccione **clase de inicio de Owin**.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-139">Right-click the solution, and select **Add**, **New Item...**. In the dialog, select **Owin Startup Class**.</span></span> <span data-ttu-id="5e1b6-140">La nueva clase el nombre **Startup.cs**.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-140">Name the new class **Startup.cs**.</span></span>

    ![](upgrading-signalr-1x-projects-to-20/_static/image1.png)
7. <span data-ttu-id="5e1b6-141">Reemplace el contenido de Startup.cs con el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="5e1b6-141">Replace the contents of Startup.cs with the following code:</span></span>

    [!code-csharp[Main](upgrading-signalr-1x-projects-to-20/samples/sample5.cs)]

    <span data-ttu-id="5e1b6-142">El atributo de ensamblado agrega la clase al proceso de inicio de Owin, que se ejecuta el `Configuration` método cuando se inicia Owin.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-142">The assembly attribute adds the class to Owin's startup process, which executes the `Configuration` method when Owin starts up.</span></span> <span data-ttu-id="5e1b6-143">Esto llama a su vez el `MapSignalR` método, que crea rutas para todos los concentradores de SignalR en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-143">This in turn calls the `MapSignalR` method, which creates routes for all SignalR hubs in the application.</span></span>
8. <span data-ttu-id="5e1b6-144">Ejecute el proyecto y copie la dirección URL de la página principal en otro explorador o el panel del explorador, como antes.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-144">Run the project, and copy the URL of the main page into another browser or browser pane, as before.</span></span> <span data-ttu-id="5e1b6-145">Cada página le pedirá un nombre de usuario y los mensajes enviados desde cada página deben ser visibles en los paneles del explorador.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-145">Each page will ask for a username, and messages sent from each page should be visible in both browser panes.</span></span>

<a id="troubleshooting"></a>

## <a name="troubleshooting-errors-encountered-during-upgrading"></a><span data-ttu-id="5e1b6-146">Solución de problemas de errores encontrados durante la actualización</span><span class="sxs-lookup"><span data-stu-id="5e1b6-146">Troubleshooting errors encountered during upgrading</span></span>

<span data-ttu-id="5e1b6-147">Esta sección describe problemas que pueden surgir durante la actualización.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-147">This section describes issues that may arise during upgrading.</span></span> <span data-ttu-id="5e1b6-148">Para obtener una lista más completa de los errores y problemas que pueden producirse con una aplicación de SignalR, consulte [solución de problemas de SignalR](../testing-and-debugging/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="5e1b6-148">For a more comprehensive list of errors and issues that may occur with a SignalR application, see [SignalR Troubleshooting](../testing-and-debugging/troubleshooting.md).</span></span>

### <a name="the-call-is-ambiguous-between-the-following-methods-or-properties"></a><span data-ttu-id="5e1b6-149">'La llamada es ambigua entre los siguientes métodos o propiedades'</span><span class="sxs-lookup"><span data-stu-id="5e1b6-149">'The call is ambiguous between the following methods or properties'</span></span>

<span data-ttu-id="5e1b6-150">Este error se producirá si una referencia a `Microsoft.AspNet.SignalR.Owin` no se quita.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-150">This error will occur if a reference to `Microsoft.AspNet.SignalR.Owin` is not removed.</span></span> <span data-ttu-id="5e1b6-151">Este paquete está en desuso; la referencia debe quitarse y se debe desinstalar la versión 1.x del paquete SelfHost.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-151">This package is deprecated; the reference must be removed and the 1.x version of the SelfHost package must be uninstalled.</span></span>

### <a name="hub-methods-fail-silently"></a><span data-ttu-id="5e1b6-152">Métodos de concentrador producirá un error en modo silencioso</span><span class="sxs-lookup"><span data-stu-id="5e1b6-152">Hub methods fail silently</span></span>

<span data-ttu-id="5e1b6-153">Compruebe que las referencias de script en el cliente son hasta fecha y que la `OwinStartup` atributo para la clase de inicio tiene la clase correcto y nombres de ensamblado para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-153">Verify that the script references in your client are up to date, and that the `OwinStartup` attribute for your Startup class has the correct class and assembly names for your project.</span></span> <span data-ttu-id="5e1b6-154">Además, pruebe a abrir la dirección de los concentradores (hubs/signalr /) en el explorador; cualquier error que aparece le ofrece más información sobre la causa del error.</span><span class="sxs-lookup"><span data-stu-id="5e1b6-154">Also, try opening up the hubs address (/signalr/hubs) in your browser; any error that appears will offer more information about what's going wrong.</span></span>