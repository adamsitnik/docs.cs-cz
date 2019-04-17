---
title: Aplikace konzoly spuštěné v Dockeru
description: Zjistěte, jak využít stávající aplikace konzoly rozhraní .NET Framework a spuštění v kontejneru Windows Docker.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: da3c814e2ae3ae646072deaf7aa932272160ce49
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611494"
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="40cdb-103">Spuštění konzolové aplikace v kontejnerech Windows</span><span class="sxs-lookup"><span data-stu-id="40cdb-103">Running console applications in Windows containers</span></span>

<span data-ttu-id="40cdb-104">Konzolové aplikace se používají pro celou řadu účelů; od jednoduché dotazování stavu dlouhotrvající bitovou kopii dokumentu zpracování úlohy.</span><span class="sxs-lookup"><span data-stu-id="40cdb-104">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="40cdb-105">Možnost spuštění a tyto aplikace škálovat v každém případě splnění s omezeními hardwaru akvizice, časy spuštění nebo spuštění více instancí.</span><span class="sxs-lookup"><span data-stu-id="40cdb-105">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="40cdb-106">Přesunutí vaší konzolové aplikace pomocí Docker a Windows Server kontejnery umožňuje spouštění těchto aplikací z čistého stavu, což jim umožňuje provádět operace a vypnutí čistě.</span><span class="sxs-lookup"><span data-stu-id="40cdb-106">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="40cdb-107">Toto téma se zobrazí kroky potřebné k přesunutí konzolovou aplikaci pro Windows základě kontejneru, spusťte ji pomocí skriptu prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40cdb-107">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="40cdb-108">Ukázková Konzolová aplikace je jednoduchý příklad, který v tomto případě přebírá argument, dotaz a vrátí náhodné odpovědí.</span><span class="sxs-lookup"><span data-stu-id="40cdb-108">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="40cdb-109">To může trvat `customer_id` a zpracovat jejich daně, nebo vytvořit miniaturu pro `image_url` argument.</span><span class="sxs-lookup"><span data-stu-id="40cdb-109">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="40cdb-110">Kromě odpověď `Environment.MachineName` se přidal do odpovědi zobrazíte rozdíl mezi spuštěním aplikace místně a v kontejneru Windows.</span><span class="sxs-lookup"><span data-stu-id="40cdb-110">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="40cdb-111">Při místním spuštění aplikace by měla být vrácena název místního počítače a při spuštění v kontejneru Windows; id relace kontejneru se vrátí.</span><span class="sxs-lookup"><span data-stu-id="40cdb-111">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="40cdb-112">[Kompletní příklad](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) je k dispozici v úložišti dotnet/samples na Githubu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-112">The [complete example](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="40cdb-113">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="40cdb-113">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="40cdb-114">Musíte znát některé Docker podmínky před zahájením práce ohledně přesunu aplikace do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="40cdb-114">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> [!NOTE]
> <span data-ttu-id="40cdb-115">A *image Dockeru* je jen pro čtení šablona definující prostředí pro spuštěný kontejner, včetně operačního systému (OS), součásti systému a aplikací.</span><span class="sxs-lookup"><span data-stu-id="40cdb-115">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="40cdb-116">Důležitou součástí Image Dockeru je, že Image se skládají ze základní image.</span><span class="sxs-lookup"><span data-stu-id="40cdb-116">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="40cdb-117">Každý nový obrázek přidá malé sadě funkcí do existující image.</span><span class="sxs-lookup"><span data-stu-id="40cdb-117">Each new image adds a small set of features to an existing image.</span></span>

> [!NOTE]
> <span data-ttu-id="40cdb-118">A *kontejneru Dockeru* je spuštěna instance bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="40cdb-118">A *Docker container* is a running instance of an image.</span></span>

<span data-ttu-id="40cdb-119">Škálování aplikace spuštěním stejnou bitovou kopii v spousta kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="40cdb-119">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="40cdb-120">Koncepčně je podobná spuštění stejné aplikace v několika hostitelích.</span><span class="sxs-lookup"><span data-stu-id="40cdb-120">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="40cdb-121">Další informace o architektuře Dockeru najdete [přehled Dockeru](https://docs.docker.com/engine/understanding-docker/) na web Dockeru.</span><span class="sxs-lookup"><span data-stu-id="40cdb-121">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span>

<span data-ttu-id="40cdb-122">Přesun vaší konzolové aplikace je otázkou pár kroků.</span><span class="sxs-lookup"><span data-stu-id="40cdb-122">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="40cdb-123">Sestavení aplikace</span><span class="sxs-lookup"><span data-stu-id="40cdb-123">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="40cdb-124">Vytváří se soubor Dockerfile pro bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="40cdb-124">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="40cdb-125">Proces sestavení a spuštění kontejneru Dockeru</span><span class="sxs-lookup"><span data-stu-id="40cdb-125">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="40cdb-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40cdb-126">Prerequisites</span></span>

<span data-ttu-id="40cdb-127">Kontejnery Windows se podporují na [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) nebo [Windows serveru 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="40cdb-127">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="40cdb-128">Pokud používáte Windows Server 2016, je nutné kontejnery ručně povolit, protože instalační služba Docker pro Windows nebudou povolení této funkce.</span><span class="sxs-lookup"><span data-stu-id="40cdb-128">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="40cdb-129">Ujistěte se, že všechny aktualizace spustili pro operační systém a pak postupujte podle pokynů v [nasazení hostitele kontejneru](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) článku a nainstalujte kontejnery a Docker funkce.</span><span class="sxs-lookup"><span data-stu-id="40cdb-129">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) article to install the containers and Docker features.</span></span>

<span data-ttu-id="40cdb-130">Musíte mít Docker pro Windows, kontejnery Windows verze 1.12 Beta 26 nebo vyšší pro podporu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-130">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="40cdb-131">Ve výchozím nastavení Docker umožňuje kontejnery založené na Linuxu; Přepnout na kontejnery Windows klikněte pravým tlačítkem myši klikněte na ikonu Dockeru na hlavním panelu systému a vyberte **přepnout na kontejnery Windows**.</span><span class="sxs-lookup"><span data-stu-id="40cdb-131">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="40cdb-132">Docker se spustí proces změny a může vyžadovat restartování.</span><span class="sxs-lookup"><span data-stu-id="40cdb-132">Docker will run the process to change and a restart may be required.</span></span>

![Snímek obrazovky možností nabídky kontejneru Windows.](./media/console/windows-container-option.png)

## <a name="building-the-application"></a><span data-ttu-id="40cdb-134">Sestavení aplikace</span><span class="sxs-lookup"><span data-stu-id="40cdb-134">Building the application</span></span>

<span data-ttu-id="40cdb-135">Obvykle se distribuují konzolové aplikace pomocí instalačního programu, FTP nebo sdílené složky nasazení.</span><span class="sxs-lookup"><span data-stu-id="40cdb-135">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="40cdb-136">Při nasazování do kontejneru, třeba prostředky zkompilovat a připravené k umístění, ke kterému se dá použít při vytvoření image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="40cdb-136">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="40cdb-137">Tady je ukázková aplikace: [ConsoleRandomAnswerGenerator](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator)</span><span class="sxs-lookup"><span data-stu-id="40cdb-137">Here is the sample application: [ConsoleRandomAnswerGenerator](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator)</span></span>

<span data-ttu-id="40cdb-138">V *build.ps1*<sup>[[zdroj]](https://github.com/dotnet/samples/blob/master/framework/docker/ConsoleRandomAnswerGenerator/ConsoleRandomAnswerGenerator/build.ps1)</sup>, tento skript využívá [MSBuild](/visualstudio/msbuild/msbuild) pro kompilaci aplikace k dokončení úlohy vytváření prostředků.</span><span class="sxs-lookup"><span data-stu-id="40cdb-138">In *build.ps1*<sup>[[source]](https://github.com/dotnet/samples/blob/master/framework/docker/ConsoleRandomAnswerGenerator/ConsoleRandomAnswerGenerator/build.ps1)</sup>, the script uses [MSBuild](/visualstudio/msbuild/msbuild) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="40cdb-139">Existuje několik parametrů předávaným do MSBuild pro dokončení potřebné prostředky.</span><span class="sxs-lookup"><span data-stu-id="40cdb-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="40cdb-140">Název souboru projektu nebo řešení ke kompilaci, umístění výstupu a nakonec požadované konfigurace (vydání nebo ladícího).</span><span class="sxs-lookup"><span data-stu-id="40cdb-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="40cdb-141">Při volání funkce `Invoke-MSBuild` `OutputPath` je nastavena na **publikovat** a `Configuration` nastavena na **vydání**.</span><span class="sxs-lookup"><span data-stu-id="40cdb-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span>

```powershell
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="40cdb-142">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="40cdb-142">Creating the Dockerfile</span></span>
<span data-ttu-id="40cdb-143">Základní image používá pro konzolu aplikace rozhraní .NET Framework je `microsoft/windowsservercore`, která je veřejně dostupná na [Docker Hubu](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="40cdb-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="40cdb-144">Základní image obsahuje minimální instalaci Windows serveru 2016, rozhraní .NET Framework 4.6.2 a slouží jako základní image operačního systému pro kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="40cdb-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```Dockerfile
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```

<span data-ttu-id="40cdb-145">Určuje první řádek v souboru Dockerfile pomocí základní image [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukce.</span><span class="sxs-lookup"><span data-stu-id="40cdb-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="40cdb-146">Dále [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) v souboru zkopíruje prostředky aplikace z **publikovat** složka ke kořenové složce kontejneru a poslední; nastavení [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) stavů bitové kopie, že je příkaz nebo aplikaci, která se spustí při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="40cdb-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span>

## <a name="creating-the-image"></a><span data-ttu-id="40cdb-147">Vytváření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="40cdb-147">Creating the image</span></span>

<span data-ttu-id="40cdb-148">Pokud chcete vytvořit image Dockeru, následující kód je přidán do *build.ps1* skriptu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="40cdb-149">Při spuštění skriptu `console-random-answer-generator` image se vytvoří pomocí prostředky z MSBuild definované v [vytváření aplikace](#building-the-application) oddílu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="40cdb-150">Spuštění skriptu pomocí `.\build.ps1` z příkazového řádku Powershellu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="40cdb-151">Po dokončení sestavení pomocí `docker images` příkazu z příkazového řádku nebo příkazového řádku Powershellu, uvidíte, že na obrázku je vytvořená a připravená ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="40cdb-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="40cdb-152">Spuštění kontejneru</span><span class="sxs-lookup"><span data-stu-id="40cdb-152">Running the container</span></span>

<span data-ttu-id="40cdb-153">Kontejner můžete spustit z příkazového řádku pomocí příkazu Docker.</span><span class="sxs-lookup"><span data-stu-id="40cdb-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="40cdb-154">Výstup je</span><span class="sxs-lookup"><span data-stu-id="40cdb-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="40cdb-155">Pokud spustíte `docker ps -a` příkazu v Powershellu, uvidíte, že kontejner stále existuje.</span><span class="sxs-lookup"><span data-stu-id="40cdb-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago
```

<span data-ttu-id="40cdb-156">Sloupec stavu zobrazí v "přibližně před minutou", aplikace byl dokončen a může být vypnut.</span><span class="sxs-lookup"><span data-stu-id="40cdb-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="40cdb-157">Pokud jste příkaz spustili stovek časy, by existovat sto levé statické kontejnery s žádnou činnost.</span><span class="sxs-lookup"><span data-stu-id="40cdb-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="40cdb-158">Ve scénáři začátek ideální operace byla pro práci a vypnutí nebo vyčistit.</span><span class="sxs-lookup"><span data-stu-id="40cdb-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="40cdb-159">K provedení tohoto postupu přidání `--rm` umožňuje `docker run` příkaz odstraní kontejner poté, co `Exited` obdrží se signál.</span><span class="sxs-lookup"><span data-stu-id="40cdb-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="40cdb-160">Spuštění příkazu s touto možností a podívat se na výstup `docker ps -a` příkazu, Všimněte si, že id kontejneru ( `Environment.MachineName`) není v seznamu.</span><span class="sxs-lookup"><span data-stu-id="40cdb-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="40cdb-161">Spuštění kontejneru pomocí Powershellu</span><span class="sxs-lookup"><span data-stu-id="40cdb-161">Running the container using PowerShell</span></span>

<span data-ttu-id="40cdb-162">V ukázkových souborů projektu k dispozici je také *run.ps1* což je příklad toho, jak pomocí prostředí PowerShell a spusťte aplikaci přijímá argumenty.</span><span class="sxs-lookup"><span data-stu-id="40cdb-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="40cdb-163">Pokud chcete spustit, otevřete PowerShell a pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="40cdb-163">To run, open PowerShell and use the following command:</span></span>

```powershell
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="40cdb-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="40cdb-164">Summary</span></span>

<span data-ttu-id="40cdb-165">Pouhým přidáním souboru Dockerfile a publikování aplikace, můžete kontejnerizace aplikace konzoly rozhraní .NET Framework a nyní využít přitom žádné spuštěných víc instancí, spuštění a zastavení a další funkce Windows serveru 2016 změny kódu aplikace vůbec.</span><span class="sxs-lookup"><span data-stu-id="40cdb-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>
