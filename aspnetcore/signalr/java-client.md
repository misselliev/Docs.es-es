---
title: Cliente ASP.NET Core SignalR Java
author: mikaelm12
description: Obtenga información sobre cómo usar al cliente de Java de ASP.NET Core SignalR.
monikerRange: '>= aspnetcore-2.2'
ms.author: mimengis
ms.custom: mvc
ms.date: 09/06/2018
uid: signalr/java-client
ms.openlocfilehash: f110f5391ac34f5cb4a72f64c16d86c8a37369a2
ms.sourcegitcommit: 4cd8dce371d63a66d780e4af1baab2bcf9d61b24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43995423"
---
# <a name="aspnet-core-signalr-java-client"></a><span data-ttu-id="e4bd7-103">Cliente de SignalR Java de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e4bd7-103">ASP.NET Core SignalR Java Client</span></span>

<span data-ttu-id="e4bd7-104">Por [Mikael Mengistu](https://twitter.com/MikaelM_12)</span><span class="sxs-lookup"><span data-stu-id="e4bd7-104">By [Mikael Mengistu](https://twitter.com/MikaelM_12)</span></span>

<span data-ttu-id="e4bd7-105">El cliente de Java que permite conectarse a un servidor de ASP.NET Core SignalR desde el código de Java, incluidas las aplicaciones Android.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-105">The Java client enables connecting to an ASP.NET Core SignalR server from Java code, including Android apps.</span></span> <span data-ttu-id="e4bd7-106">Al igual que el [cliente JavaScript](xref:signalr/javascript-client) y el [cliente .NET](xref:signalr/dotnet-client), el cliente de Java que le permite recibir y enviar mensajes a un concentrador en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-106">Like the [JavaScript client](xref:signalr/javascript-client) and the [.NET client](xref:signalr/dotnet-client), the Java client enables you to receive and send messages to a hub in real time.</span></span> <span data-ttu-id="e4bd7-107">El cliente de Java está disponible en ASP.NET Core 2.2 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-107">The Java client is available in ASP.NET Core 2.2 and later.</span></span>

<span data-ttu-id="e4bd7-108">En este artículo hace referencia a la aplicación de consola de Java de ejemplo usa al cliente de SignalR Java.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-108">The sample Java console app referenced in this article uses the SignalR Java client.</span></span>

<span data-ttu-id="e4bd7-109">[Vea o descargue el código de ejemplo](https://github.com/aspnet/Docs/tree/master/aspnetcore/signalr/java-client/sample) ([cómo descargarlo](xref:tutorials/index#how-to-download-a-sample))</span><span class="sxs-lookup"><span data-stu-id="e4bd7-109">[View or download sample code](https://github.com/aspnet/Docs/tree/master/aspnetcore/signalr/java-client/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))</span></span>

## <a name="install-the-signalr-java-client-package"></a><span data-ttu-id="e4bd7-110">Instale el paquete de cliente de SignalR Java</span><span class="sxs-lookup"><span data-stu-id="e4bd7-110">Install the SignalR Java client package</span></span>

<span data-ttu-id="e4bd7-111">El *signalr-0.1.0-preview1-35029* archivo JAR permite a los clientes para conectarse a los concentradores de SignalR.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-111">The *signalr-0.1.0-preview1-35029* JAR file allows clients to connect to SignalR hubs.</span></span> <span data-ttu-id="e4bd7-112">Para buscar el número de versión de archivo JAR más reciente, consulte el [los resultados de búsqueda de Maven](https://search.maven.org/search?q=g:com.microsoft.aspnet%20AND%20a:signalr&core=gav).</span><span class="sxs-lookup"><span data-stu-id="e4bd7-112">To find the latest JAR file version number, see the [Maven search results](https://search.maven.org/search?q=g:com.microsoft.aspnet%20AND%20a:signalr&core=gav).</span></span>

<span data-ttu-id="e4bd7-113">Si usa Gradle, agregue la siguiente línea a la `dependencies` sección de su *build.gradle* archivo:</span><span class="sxs-lookup"><span data-stu-id="e4bd7-113">If using Gradle, add the following line to the `dependencies` section of your *build.gradle* file:</span></span>

```gradle
implementation 'com.microsoft.aspnet:signalr:0.1.0-preview1-35029'
```

<span data-ttu-id="e4bd7-114">Si con Maven, agregue las siguientes líneas dentro de la `<dependencies>` elemento de su *pom.xml* archivo:</span><span class="sxs-lookup"><span data-stu-id="e4bd7-114">If using Maven, add the following lines inside the `<dependencies>` element of your *pom.xml* file:</span></span>

[!code-xml[pom.xml dependency element](java-client/sample/pom.xml?name=snippet_dependencyElement)]

## <a name="connect-to-a-hub"></a><span data-ttu-id="e4bd7-115">Conectarse a un concentrador</span><span class="sxs-lookup"><span data-stu-id="e4bd7-115">Connect to a hub</span></span>

<span data-ttu-id="e4bd7-116">Para establecer un `HubConnection`, el `HubConnectionBuilder` se debe usar.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-116">To establish a `HubConnection`, the `HubConnectionBuilder` should be used.</span></span> <span data-ttu-id="e4bd7-117">El nivel de registro y la dirección URL del centro se puede configurar durante la compilación de una conexión.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-117">The hub URL and log level can be configured while building a connection.</span></span> <span data-ttu-id="e4bd7-118">Configurar las opciones necesarias mediante una llamada a cualquiera de los `HubConnectionBuilder` métodos antes de `build`.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-118">Configure any required options by calling any of the `HubConnectionBuilder` methods before `build`.</span></span> <span data-ttu-id="e4bd7-119">Iniciar la conexión con `start`.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-119">Start the connection with `start`.</span></span>

[!code-java[Build hub connection](java-client/sample/src/main/java/Chat.java?range=17-20)]

## <a name="call-hub-methods-from-client"></a><span data-ttu-id="e4bd7-120">Llamar a métodos de concentrador de cliente</span><span class="sxs-lookup"><span data-stu-id="e4bd7-120">Call hub methods from client</span></span>

<span data-ttu-id="e4bd7-121">Una llamada a `send` invoca un método de concentrador.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-121">A call to `send` invokes a hub method.</span></span> <span data-ttu-id="e4bd7-122">Pase el nombre del método de concentrador y los argumentos definidos en el método de concentrador a `send`.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-122">Pass the hub method name and any arguments defined in the hub method to `send`.</span></span>

[!code-java[send method](java-client/sample/src/main/java/Chat.java?range=31)]

## <a name="call-client-methods-from-hub"></a><span data-ttu-id="e4bd7-123">Llamar a métodos cliente desde el concentrador</span><span class="sxs-lookup"><span data-stu-id="e4bd7-123">Call client methods from hub</span></span>

<span data-ttu-id="e4bd7-124">Use `hubConnection.on` para definir métodos en el cliente que se puede llamar la central.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-124">Use `hubConnection.on` to define methods on the client that the hub can call.</span></span> <span data-ttu-id="e4bd7-125">Definir los métodos después de compilar, pero antes de iniciar la conexión.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-125">Define the methods after building but before starting the connection.</span></span>

[!code-java[Define client methods](java-client/sample/src/main/java/Chat.java?range=22-24)]

## <a name="known-limitations"></a><span data-ttu-id="e4bd7-126">Limitaciones conocidas</span><span class="sxs-lookup"><span data-stu-id="e4bd7-126">Known limitations</span></span>

<span data-ttu-id="e4bd7-127">Se trata de una versión preliminar del cliente de Java.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-127">This is an early preview release of the Java client.</span></span> <span data-ttu-id="e4bd7-128">Hay muchas características que aún no se admiten.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-128">There are many features that aren't supported yet.</span></span> <span data-ttu-id="e4bd7-129">Para las versiones futuras, están trabajando los huecos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e4bd7-129">The following gaps are being worked on for future releases:</span></span>

* <span data-ttu-id="e4bd7-130">Solo los tipos primitivos se pueden aceptar como parámetros y tipos de valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-130">Only primitive types can be accepted as parameters and return types.</span></span>
* <span data-ttu-id="e4bd7-131">Las API son sincrónicas.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-131">The APIs are synchronous.</span></span>
* <span data-ttu-id="e4bd7-132">Solo el tipo de llamada de "Envío" se admite en este momento.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-132">Only the "Send" call type is supported at this time.</span></span> <span data-ttu-id="e4bd7-133">No se admiten "Invocar" y la transmisión por secuencias de valores devueltos.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-133">"Invoke" and streaming of return values aren't supported.</span></span>
* <span data-ttu-id="e4bd7-134">El cliente no admite actualmente la [Azure SignalR Service](/azure/azure-signalr/).</span><span class="sxs-lookup"><span data-stu-id="e4bd7-134">The client doesn't currently support the [Azure SignalR Service](/azure/azure-signalr/).</span></span>
* <span data-ttu-id="e4bd7-135">Se admite solo el protocolo JSON.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-135">Only the JSON protocol is supported.</span></span>
* <span data-ttu-id="e4bd7-136">Se admite sólo el transporte de WebSockets.</span><span class="sxs-lookup"><span data-stu-id="e4bd7-136">Only the WebSockets transport is supported.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e4bd7-137">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="e4bd7-137">Additional resources</span></span>

* <xref:signalr/hubs>
* <xref:signalr/javascript-client>
* <xref:signalr/publish-to-azure-web-app>