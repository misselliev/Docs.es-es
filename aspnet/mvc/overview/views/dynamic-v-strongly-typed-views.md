---
uid: mvc/overview/views/dynamic-v-strongly-typed-views
title: Vistas dinámicas frente a Vistas de establecimiento inflexible de tipos | Microsoft Docs
author: Rick-Anderson
description: ''
ms.author: riande
ms.date: 01/27/2011
ms.assetid: 0cbd88da-0da6-4605-b222-2835c6478304
msc.legacyurl: /mvc/overview/views/dynamic-v-strongly-typed-views
msc.type: authoredcontent
ms.openlocfilehash: bd00fccc44019b2e401247de1532d2abcb5dd396
ms.sourcegitcommit: 7b4e3936feacb1a8fcea7802aab3e2ea9c8af5b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48578508"
---
<a name="dynamic-v-strongly-typed-views"></a>Vistas dinámicas frente a Vistas fuertemente tipadas
====================
por [Rick Anderson]((https://twitter.com/RickAndMSFT))

Hay tres maneras de pasar información de un controlador a una vista en ASP.NET MVC 3:

1. Como un objeto de modelo fuertemente tipado.
2. Como un tipo dinámico (mediante @model dinámico)
3. Utilizando el elemento ViewBag

He escrito una aplicación de MVC 3 principales Blog sencilla para comparar y contrastar las vistas dinámicas y fuertemente tipadas. El controlador comienza con una simple lista de blogs:

[!code-csharp[Main](dynamic-v-strongly-typed-views/samples/sample1.cs)]

Haga clic con el botón derecho en el método IndexNotStonglyTyped() y agregar una vista de Razor.

[![8475.NotStronglyTypedView [1]](dynamic-v-strongly-typed-views/_static/image2.png)](dynamic-v-strongly-typed-views/_static/image1.png)

Asegúrese de que el **crear una vista fuertemente tipada** no esté marcada la casilla. La vista resultante no contiene gran parte:

[!code-cshtml[Main](dynamic-v-strongly-typed-views/samples/sample2.cshtml)]

[!code-cshtml[Main](dynamic-v-strongly-typed-views/samples/sample3.cshtml)]

Dado que usamos un dinámico y no una vista fuertemente tipada, intellisense no ayudarnos. El código completo se muestra a continuación:

[!code-cshtml[Main](dynamic-v-strongly-typed-views/samples/sample4.cshtml)]

[![6646.NotStronglyTypedView_5F00_IE [1]](dynamic-v-strongly-typed-views/_static/image4.png)](dynamic-v-strongly-typed-views/_static/image3.png)

Ahora vamos a agregar una vista fuertemente tipada. Agregue el código siguiente al controlador:

[!code-csharp[Main](dynamic-v-strongly-typed-views/samples/sample5.cs)]


Tenga en cuenta es exactamente el View(topBlogs) devuelto mismo; Llame a que la vista que no son fuertemente tipada. Haga clic con el botón derecho dentro de *StonglyTypedIndex()* y seleccione **agregar vista**. Esta vez seleccione el **Blog** clase de modelo y seleccione **lista** como plantilla Scaffold.

[![5658.StrongView [1]](dynamic-v-strongly-typed-views/_static/image6.png)](dynamic-v-strongly-typed-views/_static/image5.png)

Dentro de la nueva plantilla de vista se obtiene compatibilidad con intellisense.

[![7002.intellesince [1]](dynamic-v-strongly-typed-views/_static/image8.png)](dynamic-v-strongly-typed-views/_static/image7.png)

Se puede descargar el proyecto de c# [aquí](https://blogs.msdn.com/cfs-file.ashx/__key/CommunityServer-Blogs-Components-WeblogFiles/00-00-01-11-73-SSMS/1817.Mvc3ViewDemo.zip).
