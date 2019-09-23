---
title: Samoobslužné aplikace gRPC – gRPC pro vývojáře WCF
description: Nasazení ASP.NET Corech aplikací gRPC jako samoobslužných služeb.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184104"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="0582c-103">Samoobslužné aplikace gRPC</span><span class="sxs-lookup"><span data-stu-id="0582c-103">Self-hosted gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0582c-104">I když aplikace ASP.NET Core 3,0 je možné hostovat ve službě IIS na Windows serveru, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 se ještě nepodporují.</span><span class="sxs-lookup"><span data-stu-id="0582c-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't yet supported.</span></span> <span data-ttu-id="0582c-105">Tato funkce se očekává v budoucí aktualizaci Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="0582c-105">This functionality is expected in a future update to Windows Server.</span></span>

<span data-ttu-id="0582c-106">Aplikaci můžete spustit jako službu systému Windows nebo jako službu pro Linux řízenou [systémem](https://en.wikipedia.org/wiki/Systemd), a to díky některým novým funkcím v rozšířeních hostování .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0582c-106">You can run your application as a Windows Service, or as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), thanks to some new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="0582c-107">Spuštění aplikace jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="0582c-107">Run your app as a Windows service</span></span>

<span data-ttu-id="0582c-108">Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z nástroje NuGet.</span><span class="sxs-lookup"><span data-stu-id="0582c-108">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="0582c-109">Pak přidejte volání `UseWindowsService` `CreateHostBuilder` do metody v `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0582c-109">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="0582c-110">Pokud aplikace není spuštěna jako služba systému Windows, `UseWindowsService` metoda neprovede žádné akce.</span><span class="sxs-lookup"><span data-stu-id="0582c-110">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="0582c-111">Nyní můžete aplikaci publikovat buď ze sady Visual Studio, a to tak, že kliknete pravým tlačítkem na projekt a zvolíte možnost *publikovat* z kontextové nabídky nebo z .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0582c-111">Now publish your application, either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI.</span></span>

<span data-ttu-id="0582c-112">Při publikování aplikace .NET Core se můžete rozhodnout pro vytvoření nasazení *závislého na rozhraní* nebo *samostatného* nasazení.</span><span class="sxs-lookup"><span data-stu-id="0582c-112">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="0582c-113">Nasazení závislá na rozhraní vyžadují, aby byl na hostiteli, na kterém je spuštěný, nainstalovaný sdílený modul .NET Core Shared.</span><span class="sxs-lookup"><span data-stu-id="0582c-113">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="0582c-114">Samostatně obsažená nasazení jsou publikována s úplnou kopií modulu runtime .NET Core a architekturou a lze ji spustit na jakémkoli hostiteli.</span><span class="sxs-lookup"><span data-stu-id="0582c-114">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="0582c-115">Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci k [nasazení aplikace .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .</span><span class="sxs-lookup"><span data-stu-id="0582c-115">For more information, including the advantages and disadvantages of each approach, refer to the [.NET Core application deployment](https://docs.microsoft.com/dotnet/core/deploying/) documentation.</span></span>

<span data-ttu-id="0582c-116">Chcete-li publikovat samostatné sestavení aplikace, které nevyžaduje instalaci modulu runtime .NET Core 3,0 na hostitele, zadejte modul runtime, který bude součástí aplikace pomocí `-r` příznaku (nebo `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="0582c-116">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application using the `-r` (or `--runtime`) flag.</span></span>

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="0582c-117">Chcete-li publikovat sestavení závislé na rozhraní, vynechejte `-r` příznak.</span><span class="sxs-lookup"><span data-stu-id="0582c-117">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```console
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="0582c-118">Zkopírujte celý obsah `publish` adresáře do instalační složky a pomocí [Nástroje SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) vytvořte pro spustitelný soubor službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0582c-118">Copy the complete contents of the `publish` directory to an installation folder, and use the [sc utility](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a><span data-ttu-id="0582c-119">Přihlášení do protokolu událostí systému Windows</span><span class="sxs-lookup"><span data-stu-id="0582c-119">Log to Windows Event Log</span></span>

<span data-ttu-id="0582c-120">Metoda automaticky přidá poskytovatele protokolování, který zapíše zprávy protokolu do protokolu událostí systému Windows. [](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) `UseWindowsService`</span><span class="sxs-lookup"><span data-stu-id="0582c-120">The `UseWindowsService` method automatically adds a [Logging](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) provider that writes log messages to the Windows Event Log.</span></span> <span data-ttu-id="0582c-121">Protokolování pro tohoto zprostředkovatele můžete nakonfigurovat přidáním `EventLog` položky `Logging` do oddílu `appsettings.json` nebo jiného zdroje konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0582c-121">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or other configuration source.</span></span> <span data-ttu-id="0582c-122">Název zdroje, který se používá v protokolu událostí, lze přepsat nastavením `SourceName` vlastnosti v těchto nastaveních. Pokud nezadáte název, použije se výchozí název aplikace (obvykle název sestavení spustitelného souboru).</span><span class="sxs-lookup"><span data-stu-id="0582c-122">The source name used in Event Log can be overridden by setting a `SourceName` property in these settings; if you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="0582c-123">Další informace o protokolování najdete na konci této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="0582c-123">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="0582c-124">Spuštění aplikace jako služby pro Linux se systémem</span><span class="sxs-lookup"><span data-stu-id="0582c-124">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="0582c-125">Pokud chcete svou aplikaci ASP.NET Core nakonfigurovat tak, aby běžela jako služba pro Linux (nebo *démon* v systému Linux agilním), nainstalujte balíček [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="0582c-125">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="0582c-126">Pak přidejte volání `UseSystemd` `CreateHostBuilder` do metody v `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0582c-126">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="0582c-127">Pokud aplikace není spuštěna jako služba pro Linux, `UseSystemd` metoda neprovede žádné akce.</span><span class="sxs-lookup"><span data-stu-id="0582c-127">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="0582c-128">Nyní publikujte aplikaci (Buď závislou na rozhraní, nebo samostatnou pro příslušné prostředí Linux runtime `linux-x64`), a to buď ze sady Visual Studio, kliknutím pravým tlačítkem myši na projekt a volbou možnosti *publikovat* z kontextové nabídky nebo z rozhraní .NET. Core CLI pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="0582c-128">Now publish your application (either framework-dependent, or self-contained for the relevant Linux runtime, e.g. `linux-x64`), either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI using the following command.</span></span>

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

<span data-ttu-id="0582c-129">Zkopírujte celý obsah `publish` adresáře do instalační složky v hostiteli systému Linux.</span><span class="sxs-lookup"><span data-stu-id="0582c-129">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="0582c-130">Registrace služby vyžaduje speciální soubor, který se označuje jako "soubor jednotky", který se má přidat do `/etc/systemd/system` adresáře.</span><span class="sxs-lookup"><span data-stu-id="0582c-130">Registering the service requires a special file, called a "unit file", to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="0582c-131">K vytvoření souboru v této složce budete potřebovat oprávnění root.</span><span class="sxs-lookup"><span data-stu-id="0582c-131">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="0582c-132">Pojmenujte soubor s identifikátorem, `systemd` který chcete použít `.service` , a rozšířením.</span><span class="sxs-lookup"><span data-stu-id="0582c-132">Name the file with the identifier you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="0582c-133">Například, `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="0582c-133">For example, `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="0582c-134">Soubor služby používá formát INI, jak je znázorněno v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="0582c-134">The service file uses INI format, as shown in this example.</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="0582c-135">`Type=notify` Vlastnost oznamuje`systemd` , že aplikace bude upozorněna na spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="0582c-135">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="0582c-136">Toto `WantedBy=multi-user.target` nastavení způsobí, že se služba spustí, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.</span><span class="sxs-lookup"><span data-stu-id="0582c-136">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2", meaning a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="0582c-137">Předtím `systemd` , než nástroj rozpozná službu, musí znovu načíst konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0582c-137">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="0582c-138">Můžete ovládat `systemd` `systemctl` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0582c-138">You control `systemd` using the `systemctl` command.</span></span> <span data-ttu-id="0582c-139">Po opětovném načtení pomocí `status` dílčího příkazu potvrďte, že se aplikace úspěšně zaregistrovala.</span><span class="sxs-lookup"><span data-stu-id="0582c-139">After reloading, use the `status` subcommand to confirm the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="0582c-140">Pokud jste službu nakonfigurovali správně, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0582c-140">If you've configured the service correctly, the following output will be shown:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="0582c-141">Službu spusťte pomocí příkazu. `start`</span><span class="sxs-lookup"><span data-stu-id="0582c-141">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="0582c-142">Přípona je při použití `systemctl start`volitelná. `.service`</span><span class="sxs-lookup"><span data-stu-id="0582c-142">The `.service` extension is optional when using `systemctl start`.</span></span>

<span data-ttu-id="0582c-143">Chcete- `systemd` li říct, že se služba spustí automaticky při spuštění systému `enable` , použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="0582c-143">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="0582c-144">Přihlášení do deníku</span><span class="sxs-lookup"><span data-stu-id="0582c-144">Log to journald</span></span>

<span data-ttu-id="0582c-145">Ekvivalent systému Linux v protokolu událostí systému Windows je `journald`služba strukturovaného protokolování systému, která je `systemd`součástí nástroje.</span><span class="sxs-lookup"><span data-stu-id="0582c-145">The Linux equivalent of the Windows Event Log is `journald`, a structured logging system service that is part of `systemd`.</span></span> <span data-ttu-id="0582c-146">Protokolovat zprávy zapsané do standardního výstupu pomocí démona Linux se automaticky zapisují do `journald`, takže pokud chcete nakonfigurovat úrovně protokolování, `Console` použijte část konfigurace protokolování.</span><span class="sxs-lookup"><span data-stu-id="0582c-146">Log messages written to the standard output by a Linux daemon are automatically written to `journald`, so to configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="0582c-147">Metoda `UseSystemd` sestavení hostitele automaticky nakonfiguruje výstupní formát konzoly tak, aby odpovídaly deníku.</span><span class="sxs-lookup"><span data-stu-id="0582c-147">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="0582c-148">Vzhledem `journald` k tomu, že je standard pro protokoly Linux, existuje celá řada nástrojů, které se s ním integrují, a můžete snadno směrovat `journald` protokoly z do externího systému protokolování.</span><span class="sxs-lookup"><span data-stu-id="0582c-148">Because `journald` is the standard for Linux logs, there are a variety of tools that integrate with it, and you can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="0582c-149">Místně pracujete na hostiteli, pomocí `journalctl` příkazu můžete zobrazit protokoly z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0582c-149">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="0582c-150">Pokud máte k dispozici prostředí GUI na vašem hostiteli, je pro Linux k dispozici několik grafických prohlížečů, jako jsou například *QJournalctl* a *GNOME-* log.</span><span class="sxs-lookup"><span data-stu-id="0582c-150">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="0582c-151">Další informace o dotazování systémového deníku z příkazového řádku pomocí `journalctl`najdete [na stránkách Man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="0582c-151">To learn more about querying the systemd journal from the command line with `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="0582c-152">Certifikáty HTTPS pro samoobslužné aplikace</span><span class="sxs-lookup"><span data-stu-id="0582c-152">HTTPS Certificates for self-hosted applications</span></span>

<span data-ttu-id="0582c-153">Při spuštění aplikace gRPC v produkčním prostředí byste měli použít certifikát TLS od důvěryhodné certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="0582c-153">When running a gRPC application in production, you should use a TLS certificate from a trusted Certificate Authority (CA).</span></span> <span data-ttu-id="0582c-154">Tato certifikační autorita může být veřejná certifikační autoritou nebo interní pro vaši organizaci.</span><span class="sxs-lookup"><span data-stu-id="0582c-154">This CA could be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="0582c-155">Na hostitelích s Windows může být certifikát načtený z zabezpečeného [úložiště certifikátů](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí [třídy X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="0582c-155">On Windows hosts, the certificate may be loaded from a secure [Certificate Store](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) using the [X509Store class](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span></span> <span data-ttu-id="0582c-156">`X509Store` Třídu lze také použít s úložištěm OpenSSL Key na některých hostitelích se systémem Linux.</span><span class="sxs-lookup"><span data-stu-id="0582c-156">The `X509Store` class can also be used with the OpenSSL key-store on some Linux hosts.</span></span>

<span data-ttu-id="0582c-157">Certifikáty je také možné vytvořit pomocí jednoho z [konstruktorů X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), buď ze souboru (například `.pfx` soubor chráněný silným heslem), nebo z binárních dat načtených ze zabezpečené služby úložiště, jako je [Azure Key Vault ](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="0582c-157">Certificates may also be created using one of the [X509Certificate2 constructors](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), either from a file (for example a `.pfx` file protected by a strong password), or from binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="0582c-158">Kestrel se dá nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0582c-158">Kestrel can be configured to use a certificate in two ways: from configuration, or in code.</span></span>

### <a name="set-https-certificates-using-configuration"></a><span data-ttu-id="0582c-159">Nastavení certifikátů HTTPS pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="0582c-159">Set HTTPS certificates using configuration</span></span>

<span data-ttu-id="0582c-160">Konfigurační přístup vyžaduje nastavení cesty k souboru certifikátu `.pfx` a heslo v oddílu konfigurace Kestrel.</span><span class="sxs-lookup"><span data-stu-id="0582c-160">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="0582c-161">V `appsettings.json` takovém případě by vypadala takto.</span><span class="sxs-lookup"><span data-stu-id="0582c-161">In `appsettings.json` that would look like this.</span></span>

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

<span data-ttu-id="0582c-162">Heslo by mělo být k dispozici pomocí zabezpečeného zdroje konfigurace, jako je Azure webtrezor nebo trezor Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="0582c-162">The password should be provided using a secure configuration source such as Azure KeyVault or Hashicorp Vault.</span></span>

<span data-ttu-id="0582c-163">Nešifrovaná hesla byste neměli ukládat v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="0582c-163">You SHOULD NOT store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="0582c-164">Nastavení certifikátů HTTPS v kódu</span><span class="sxs-lookup"><span data-stu-id="0582c-164">Set HTTPS certificates in code</span></span>

<span data-ttu-id="0582c-165">Chcete-li nakonfigurovat https na Kestrel v kódu, `ConfigureKestrel` použijte metodu `IWebHostBuilder` pro ve `Program` třídě.</span><span class="sxs-lookup"><span data-stu-id="0582c-165">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

<span data-ttu-id="0582c-166">Heslo pro tento `.pfx` soubor byste znovu měli uložit v a načíst ze zdroje zabezpečené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0582c-166">Again, the password for the `.pfx` file should be stored in and retrieved from a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0582c-167">[Předchozí](grpc-in-production.md)
>[Další](docker.md)</span><span class="sxs-lookup"><span data-stu-id="0582c-167">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>