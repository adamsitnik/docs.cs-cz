---
title: Publikování aplikací .NET Core pomocí rozhraní příkazového řádku
description: Naučte se publikovat aplikaci .NET Core pomocí nástrojů rozhraní příkazového řádku .NET Core SDK (CLI).
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: c8b4c60eb4ea09c8b10bd0b2fffc803d0a5fb6e0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834284"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Publikování aplikací .NET Core pomocí rozhraní příkazového řádku

Tento článek ukazuje, jak můžete publikovat aplikaci .NET Core z příkazového řádku. .NET Core nabízí tři způsoby, jak publikovat aplikace. Nasazení závislé na rozhraní vytvoří soubor. dll pro více platforem, který používá místně instalovaný modul runtime .NET Core. Spustitelný soubor závislý na rozhraní vytvoří spustitelný soubor specifický pro platformu, který používá místně instalovaný modul runtime .NET Core. Samostatně obsažený spustitelný soubor vytvoří spustitelný soubor specifický pro platformu a obsahuje místní kopii modulu runtime .NET Core.

Přehled těchto režimů publikování najdete v tématu [nasazení aplikace .NET Core](index.md).

Hledáte nějakou rychlou nápovědu k používání rozhraní příkazového řádku? V následující tabulce jsou uvedeny některé příklady publikování aplikace. Můžete zadat cílovou architekturu s parametrem `-f <TFM>` nebo úpravou souboru projektu. Další informace najdete v tématu [základy publikování](#publishing-basics).

| Režim publikování | Verze sady SDK | Příkaz |
| ------------ | ----------- | ------- |
| Nasazení závislé na rozhraní | 2.x | `dotnet publish -c Release` |
| Spustitelný soubor závislý na rozhraní | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Samostatně zahrnuté nasazení      | 2,1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* při použití sady SDK verze 3,0 je spustitelný soubor závislý na architektuře výchozím režimem publikování při spuštění příkazu Basic `dotnet publish`. To platí pouze v případě, že projekt cílí na **rozhraní .NET core 2,1** nebo **.NET Core 3,0**.

## <a name="publishing-basics"></a>Základy publikování

Nastavení `<TargetFramework>` souboru projektu určuje výchozí cílovou architekturu při publikování aplikace. Můžete změnit cílovou architekturu na libovolný platný [cílový moniker rozhraní (TFM)](../../standard/frameworks.md). Například pokud váš projekt používá `<TargetFramework>netcoreapp2.2</TargetFramework>`, je vytvořen binární soubor, který cílí na .NET Core 2,2. TFM zadané v tomto nastavení je výchozí cíl, který používá příkaz [`dotnet publish`](../tools/dotnet-publish.md) .

Chcete-li cílit na více než jednu architekturu, můžete nastavit nastavení `<TargetFrameworks>` na více než jednu hodnotu TFM oddělené středníkem. Můžete publikovat jednu z architektur pomocí příkazu `dotnet publish -f <TFM>`. Pokud máte například `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` a spustíte `dotnet publish -f netcoreapp2.1`, bude vytvořen binární soubor, který cílí na .NET Core 2,1.

Pokud není nastavena jinak, je výstupní adresář příkazu [`dotnet publish`](../tools/dotnet-publish.md) `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Výchozí režim **konfigurace sestavení** je **ladění** , pokud se nezmění s parametrem `-c`. Například `dotnet publish -c Release -f netcoreapp2.1` publikování `myfolder/bin/Release/netcoreapp2.1/publish/`.

Pokud používáte .NET Core SDK 3,0, výchozím režimem publikování pro aplikace, které cílí na .NET Core verze 2,1, 2,2 nebo 3,0, je spustitelný soubor závislý na rozhraní.

Pokud používáte .NET Core SDK 2,1, výchozím režimem publikování pro aplikace, které cílí na .NET Core verze 2,1, 2,2 je nasazení závislé na rozhraní.

### <a name="native-dependencies"></a>Nativní závislosti

Pokud má vaše aplikace nativní závislosti, nemusí běžet v jiném operačním systému. Pokud vaše aplikace například používá nativní rozhraní API systému Windows, nebude spuštěna na macOS nebo Linux. Je nutné zadat kód specifický pro platformu a zkompilovat spustitelný soubor pro každou platformu.

V případě, že knihovna, na kterou jste odkazovali, má nativní závislost, vaše aplikace nemusí běžet na všech platformách. Je však možné, že balíček NuGet, na který odkazujete, obsahuje verze specifické pro platformu, které pro vás pořídí požadované nativní závislosti.

Při distribuci aplikace s nativními závislostmi možná budete muset použít přepínač `dotnet publish -r <RID>` a zadat cílovou platformu, pro kterou chcete publikovat. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

Další informace o binárních souborech specifických pro konkrétní platformu jsou pokryté [spustitelnými soubory závislými na rozhraní](#framework-dependent-executable) a oddíly [pro nasazení samostatného nasazení](#self-contained-deployment) .

## <a name="sample-app"></a>Ukázková aplikace

Pomocí následující aplikace můžete prozkoumat příkazy pro publikování. Aplikaci vytvoříte spuštěním následujících příkazů v terminálu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Soubor `Program.cs` nebo `Program.vb` generovaný šablonou konzoly musí být změněn na následující:

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Při spuštění aplikace ([`dotnet run`](../tools/dotnet-run.md)) se zobrazí následující výstup:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Nasazení závislé na rozhraní

Pro .NET Core SDK 2. x CLI, nasazení závislé na rozhraní (FDD) je výchozí režim pro příkaz Basic `dotnet publish`.

Když publikujete aplikaci jako FDD, vytvoří se soubor `<PROJECT-NAME>.dll` ve složce `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Chcete-li spustit aplikaci, přejděte do výstupní složky a použijte příkaz `dotnet <PROJECT-NAME>.dll`.

Vaše aplikace je nakonfigurovaná tak, aby byla cílena na konkrétní verzi .NET Core. Cílový modul runtime .NET Core musí být v počítači, na kterém chcete aplikaci spustit. Například pokud vaše aplikace cílí na .NET Core 2,2, musí mít každý počítač, na kterém je aplikace spuštěná, nainstalovaný modul .NET Core 2,2 Runtime. Jak je uvedeno v části [základy publikování](#publishing-basics) , můžete upravit soubor projektu pro změnu výchozí cílové architektury nebo pro cílení na více než jedno rozhraní.

Publikováním FDD se vytvoří aplikace, která se automaticky přenese do nejnovější opravy zabezpečení .NET Core, která je dostupná v systému, ve kterém je spuštěná aplikace. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Spustitelný soubor závislý na rozhraní

Pro .NET Core SDK 3. x CLI, spustitelný soubor závislý na rozhraní (FDE) je výchozím režimem pro příkaz Basic `dotnet publish`. Není nutné zadávat žádné další parametry, pokud chcete cílit na aktuální operační systém.

V tomto režimu se pro hostování aplikace pro různé platformy vytvoří spustitelný hostitel specifický pro platformu. Tento režim je podobný jako FDD, protože FDD vyžaduje hostitele ve formě příkazu `dotnet`. Název spustitelného souboru hostitele se u jednotlivých platforem liší a má název podobný jako `<PROJECT-FILE>.exe`. Tento spustitelný soubor můžete spustit přímo místo volání `dotnet <PROJECT-FILE>.dll`, což je stále přijatelný způsob, jak aplikaci spustit.

Vaše aplikace je nakonfigurovaná tak, aby byla cílena na konkrétní verzi .NET Core. Cílový modul runtime .NET Core musí být v počítači, na kterém chcete aplikaci spustit. Například pokud vaše aplikace cílí na .NET Core 2,2, musí mít každý počítač, na kterém je aplikace spuštěná, nainstalovaný modul .NET Core 2,2 Runtime. Jak je uvedeno v části [základy publikování](#publishing-basics) , můžete upravit soubor projektu pro změnu výchozí cílové architektury nebo pro cílení na více než jedno rozhraní.

Publikováním FDE se vytvoří aplikace, která se automaticky přenese na nejnovější aktualizaci zabezpečení .NET Core dostupnou v systému, ve kterém je aplikace spuštěná. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

Je nutné (kromě .NET Core 3. x při cílení na aktuální platformu) použít následující přepínače s příkazem `dotnet publish` k publikování FDE:

- `-r <RID>` Tento přepínač pomocí identifikátoru (RID) určí cílovou platformu. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

- `--self-contained false` Tento přepínač oznamuje .NET Core SDK vytvoření spustitelného souboru jako FDE.

Pokaždé, když použijete přepínač `-r`, změní se cesta výstupní složky na: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`.

Pokud používáte [ukázkovou aplikaci](#sample-app), spusťte `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Tento příkaz vytvoří následující spustitelný soubor: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Celkovou velikost nasazení můžete snížit povolením **režimu invariantování globalizace**. Tento režim je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [neutrální jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a o tom, jak ho povolit, najdete v tématu [Nevariantní režim globalizace .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Samostatně zahrnuté nasazení

Při publikování samostatného nasazení (SCD) vytvoří .NET Core SDK spustitelný soubor specifický pro platformu. Publikování SCD zahrnuje všechny požadované soubory .NET Core ke spuštění vaší aplikace, ale nezahrnuje [nativní závislosti rozhraní .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Tyto závislosti musí být v systému před spuštěním aplikace přítomny.

Publikování SCD vytvoří aplikaci, která nepřevádí zpět na nejnovější dostupnou opravu zabezpečení .NET Core. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

K publikování SCD je nutné použít následující přepínače s příkazem `dotnet publish`:

- `-r <RID>` Tento přepínač pomocí identifikátoru (RID) určí cílovou platformu. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

- `--self-contained true` Tento přepínač instruuje .NET Core SDK, aby vytvořil spustitelný soubor jako SCD.

> [!NOTE]
> Celkovou velikost nasazení můžete snížit povolením **režimu invariantování globalizace**. Tento režim je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [neutrální jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a o tom, jak ho povolit, najdete v tématu [Nevariantní režim globalizace .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="see-also"></a>Viz také:

- [Přehled nasazení aplikace .NET Core](index.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
