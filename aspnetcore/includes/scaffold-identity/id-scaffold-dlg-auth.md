<span data-ttu-id="6c706-101">Ejecute al scaffolder de identidad:</span><span class="sxs-lookup"><span data-stu-id="6c706-101">Run the Identity scaffolder:</span></span>

# <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="6c706-102">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c706-102">Visual Studio</span></span>](#tab/visual-studio)

* <span data-ttu-id="6c706-103">De **el Explorador de soluciones**, haga doble clic en el proyecto > **agregar** > **nuevo elemento de scaffolding**.</span><span class="sxs-lookup"><span data-stu-id="6c706-103">From **Solution Explorer**, right-click on the project > **Add** > **New Scaffolded Item**.</span></span>
* <span data-ttu-id="6c706-104">En el panel izquierdo de la **agregar scaffolding** cuadro de diálogo, seleccione **identidad** > **agregar**.</span><span class="sxs-lookup"><span data-stu-id="6c706-104">From the left pane of the **Add Scaffold** dialog, select **Identity** > **ADD**.</span></span>
* <span data-ttu-id="6c706-105">En el **Agregar identidad** cuadro de diálogo, seleccione las opciones que desee.</span><span class="sxs-lookup"><span data-stu-id="6c706-105">In the **ADD Identity** dialog, select the options you want.</span></span>
  * <span data-ttu-id="6c706-106">Seleccione la página de diseño existente, o se sobrescribirá el archivo de diseño con formato incorrecto.</span><span class="sxs-lookup"><span data-stu-id="6c706-106">Select your existing layout page, or your layout file will be overwritten with incorrect markup.</span></span> <span data-ttu-id="6c706-107">Cuando se selecciona un archivo _Layout.cshtml existente, es **no** sobrescribe.</span><span class="sxs-lookup"><span data-stu-id="6c706-107">When an existing _Layout.cshtml file is selected, it is **not** overwritten.</span></span>

 <span data-ttu-id="6c706-108">Por ejemplo `~/Pages/Shared/_Layout.cshtml` para las páginas de Razor `~/Views/Shared/_Layout.cshtml` para los proyectos MVC</span><span class="sxs-lookup"><span data-stu-id="6c706-108">For example `~/Pages/Shared/_Layout.cshtml` for Razor Pages `~/Views/Shared/_Layout.cshtml` for MVC projects</span></span>
* <span data-ttu-id="6c706-109">Para usar el contexto de datos existente, seleccione al menos un archivo para invalidar.</span><span class="sxs-lookup"><span data-stu-id="6c706-109">To use your existing data context, select at least one file to override.</span></span> <span data-ttu-id="6c706-110">Debe seleccionar al menos un archivo para agregar el contexto de datos.</span><span class="sxs-lookup"><span data-stu-id="6c706-110">You must select at least one file to add your data context.</span></span>
  * <span data-ttu-id="6c706-111">Seleccione la clase de contexto de datos.</span><span class="sxs-lookup"><span data-stu-id="6c706-111">Select your data context class.</span></span>
  * <span data-ttu-id="6c706-112">Seleccione **agregar**.</span><span class="sxs-lookup"><span data-stu-id="6c706-112">Select **ADD**.</span></span>
* <span data-ttu-id="6c706-113">Para crear un nuevo contexto de usuario y posiblemente crear una clase de usuario personalizado de identidad:</span><span class="sxs-lookup"><span data-stu-id="6c706-113">To create a new user context and possibly create a custom user class for Identity:</span></span>
  * <span data-ttu-id="6c706-114">Seleccione el **+** botón para crear un nuevo **clase de contexto de datos**.</span><span class="sxs-lookup"><span data-stu-id="6c706-114">Select the **+** button to create a new **Data context class**.</span></span>
  * <span data-ttu-id="6c706-115">Seleccione **agregar**.</span><span class="sxs-lookup"><span data-stu-id="6c706-115">Select **ADD**.</span></span>

<span data-ttu-id="6c706-116">Nota: Si va a crear un nuevo contexto de usuario, no tienes que seleccionar un archivo para invalidar.</span><span class="sxs-lookup"><span data-stu-id="6c706-116">Note: If you're creating a new user context, you don't have to select a file to override.</span></span>

# <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="6c706-117">CLI de .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c706-117">.NET Core CLI</span></span>](#tab/netcore-cli)

<span data-ttu-id="6c706-118">Si no ha instalado previamente el scaffolder ASP.NET, instalarla ahora:</span><span class="sxs-lookup"><span data-stu-id="6c706-118">If you have not previously installed the ASP.NET scaffolder, install it now:</span></span>

```cli
dotnet tool install -g dotnet-aspnet-codegenerator
```

<span data-ttu-id="6c706-119">Agregue una referencia de paquete a [Microsoft.VisualStudio.Web.CodeGeneration.Design](https://www.nuget.org/packages/Microsoft.VisualStudio.Web.CodeGeneration.Design/) al proyecto (\*.csproj) archivo.</span><span class="sxs-lookup"><span data-stu-id="6c706-119">Add a package reference to [Microsoft.VisualStudio.Web.CodeGeneration.Design](https://www.nuget.org/packages/Microsoft.VisualStudio.Web.CodeGeneration.Design/) to the project (\*.csproj) file.</span></span> <span data-ttu-id="6c706-120">Ejecute el siguiente comando en el directorio del proyecto:</span><span class="sxs-lookup"><span data-stu-id="6c706-120">Run the following command in the project directory:</span></span>

```cli
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet restore
```

<span data-ttu-id="6c706-121">Ejecute el siguiente comando para mostrar las opciones de scaffolder de identidad:</span><span class="sxs-lookup"><span data-stu-id="6c706-121">Run the following command to list the Identity scaffolder options:</span></span>

```cli
dotnet aspnet-codegenerator identity -h
```

<span data-ttu-id="6c706-122">En la carpeta del proyecto, ejecute al scaffolder de identidad con las opciones que desee.</span><span class="sxs-lookup"><span data-stu-id="6c706-122">In the project folder, run the Identity scaffolder with the options you want.</span></span> <span data-ttu-id="6c706-123">Por ejemplo, para configurar la identidad con la interfaz de usuario predeterminada y el número mínimo de archivos, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="6c706-123">For example, to setup identity with the default UI and the minimum number of files, run the following command.</span></span> <span data-ttu-id="6c706-124">Use el nombre completo correcto para el contexto de base de datos:</span><span class="sxs-lookup"><span data-stu-id="6c706-124">Use the correct fully qualified name for your DB context:</span></span>

```cli
dotnet aspnet-codegenerator identity -dc MyWeb.Data.ApplicationDbContext --files Account.Register
```

-------------