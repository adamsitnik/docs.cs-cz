---
title: Analyzátor rozhraní .NET API
description: Přečtěte si, jak může analyzátor rozhraní .NET API pomáhat detekovat zastaralá rozhraní API a problémy s kompatibilitou platforem.
author: oliag
ms.author: mairaw
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 584f9f952148ebf72c5d5aaed64a2a078be00ce5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929350"
---
# <a name="net-api-analyzer"></a>Analyzátor rozhraní .NET API

Analyzátor rozhraní .NET API je nástroj Roslyn Analyzer, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání zastaralých rozhraní API. Může být užitečné pro všechny C# vývojáře v jakékoli fázi vývoje.

Analyzátor API se dodává jako balíček NuGet [Microsoft. dotnet. analyzers. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Poté, co na něj odkazujete v projektu, automaticky monitoruje kód a indikuje problematické využití rozhraní API. Kliknutím na žárovku můžete také získat návrhy na možné opravy. Rozevírací nabídka obsahuje možnost pro potlačení upozornění.

> [!NOTE]
> Analyzátor rozhraní .NET API je stále předběžnou verzí.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 a novější verze nebo Visual Studio pro Mac (všechny verze).

## <a name="discovering-deprecated-apis"></a>Zjišťují se zastaralá rozhraní API.

### <a name="what-are-deprecated-apis"></a>Co jsou zastaralá rozhraní API?

Rodina .NET je sada velkých produktů, které se neustále upgradují tak, aby lépe vyhovovaly potřebám zákazníků. Je přirozené zastaralá některá rozhraní API a nahrazovat je novými. Rozhraní API se považuje za zastaralé, pokud existuje lepší alternativa. Jedním ze <xref:System.ObsoleteAttribute> způsobů, jak informovat o tom, že rozhraní API je zastaralé a nemělo by se používat, je označit s atributem. Nevýhodou tohoto přístupu je, že existuje jenom jedno ID diagnostiky pro všechna zastaralá C#rozhraní API (pro, [CS0612](../../csharp/misc/cs0612.md)). To znamená, že:

- U každého případu není možné mít vyhrazené dokumenty.
- Není možné potlačit určitou kategorii upozornění. Můžete potlačit buď všechny, nebo žádné z nich.
- Chcete-li informovat uživatele o nové zastaralosti, je nutné aktualizovat odkazované sestavení nebo balíček cílení.

Analyzátor API používá kódy chyb specifické pro rozhraní API, které začínají na DE (což představuje chybu při vyřazení), která umožňuje kontrolu nad zobrazením jednotlivých upozornění. Zastaralá rozhraní API identifikovaná analyzátorem jsou definována v úložišti [dotnet/Platform-kompatibility](https://github.com/dotnet/platform-compat) .

### <a name="using-the-api-analyzer"></a>Použití analyzátoru rozhraní API

Pokud se v kódu používá zastaralé rozhraní API <xref:System.Net.WebClient>, jako je například, analyzátor rozhraní API ho zvýrazní zelenou vlnovkou. Když najedete myší na volání rozhraní API, zobrazí se žárovka s informacemi o zastaralém rozhraní API, jako v následujícím příkladu:

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/green-squiggle.jpg)

Okno **Seznam chyb** obsahuje upozornění s jedinečným ID na zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`): 

![Snímek obrazovky okna Seznam chyb zobrazující ID a popis upozornění](media/api-analyzer/warnings-id-and-descriptions.jpg "Seznam chyb okno, které obsahuje upozornění.")

Kliknutím na ID přejdete na webovou stránku s podrobnými informacemi o tom, proč se rozhraní API zastaralo, a návrhy týkající se alternativních rozhraní API, která se dají použít.

Všechna upozornění lze potlačit kliknutím pravým tlačítkem na zvýrazněný člen a výběrem možnosti **potlačit \<ID diagnostiky >** . Existují dva způsoby, jak potlačit upozornění: 

- [místně (ve zdroji)](#suppressing-warnings-locally)
- [globálně (v souboru potlačení)](#suppressing-warnings-globally) – doporučeno

### <a name="suppressing-warnings-locally"></a>Místní potlačení upozornění

Chcete-li potlačit upozornění místně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoringy** > **potlačit ID diagnostiky\< *ID diagnostiky*>**  >   **ve zdroji**. Do vašeho zdrojového kódu je v definovaném oboru přidána direktiva preprocesoru upozornění [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) : !["Snímek obrazovky s kódem s rámcem #pragma vypnutí upozornění"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Globální potlačení upozornění

Chcete-li potlačit upozornění globálně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoringy** > **potlačit ID diagnostiky\< *ID diagnostiky*>**  >  **v souboru potlačení**.

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppress-in-sup-file.jpg)

Po prvním potlačení se do projektu přidá soubor *GlobalSuppressions.cs* . K tomuto souboru se připojí nová globální potlačení.

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppression-file.jpg)

Globální potlačení je doporučený způsob, jak zajistit konzistenci využití rozhraní API napříč projekty.

## <a name="discovering-cross-platform-issues"></a>Zjišťování problémů s více platformami

Podobně jako zastaralá rozhraní API nástroj Analyzer identifikuje všechna rozhraní API, která nejsou pro různé platformy. Například funguje ve <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows, ale ne v systémech Linux a MacOS. ID diagnostiky se zobrazí v okně **Seznam chyb** . Toto upozornění můžete potlačit tak, že kliknete pravým tlačítkem a vyberete **rychlé akce a refaktoringy**. Na rozdíl od zastaralých případů, kde máte dvě možnosti (můžete buď dál používat zastaralé členy a potlačit upozornění, nebo je nepoužívat vůbec), pokud vyvíjíte kód jenom pro určité platformy, můžete potlačit všechna upozornění pro všechny ostatní platformy, které nepoužíváte. Naplánujte spuštění kódu v. K tomu stačí upravit soubor projektu a přidat `PlatformCompatIgnore` vlastnost, která obsahuje seznam všech platforem, které mají být ignorovány. Přípustné hodnoty jsou: `Linux`, `macOS`a `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Pokud váš kód cílí na více platforem a chcete využít výhod rozhraní API, které není na některých z nich podporováno, můžete tuto část kódu `if` chránit příkazem:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Můžete také podmíněně kompilovat na cílové rozhraní nebo operační systém, ale v tuto chvíli je nutné provést [ručně](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Podporovaná Diagnostika

Analyzátor v současné době zpracovává následující případy:

- Použití rozhraní API pro .NET Standard, které <xref:System.PlatformNotSupportedException> vyvolá (PC001).
- Použití rozhraní .NET Standard API, které není k dispozici v .NET Framework 4.6.1 (PC002).
- Použití nativního rozhraní API, které neexistuje v UWP (PC003).
- Použití rozhraní API Delegate. BeginInvoke a EndInvoke u delegujících (PC004).
- Použití rozhraní API, které je označeno jako zastaralé (pro odstranění XXXX).

## <a name="ci-machine"></a>Počítač CI

Všechna tato diagnostika jsou k dispozici nejen v integrovaném vývojovém prostředí (IDE), ale také na příkazovém řádku jako součást sestavení projektu, který zahrnuje server CI.

## <a name="configuration"></a>Konfiguraci

Uživatel rozhodne, jak by měla být Diagnostika zpracována: jako upozornění, chyby, návrhy nebo je vypnuto. Například jako architekt se můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některých zastaralých rozhraní API generují upozornění, zatímco ostatní generují pouze návrhy. Můžete ji nakonfigurovat samostatně podle ID diagnostiky a podle projektu. Provedete to tak, že v **Průzkumník řešení**přejdete do uzlu **závislosti** v projektu. Rozbalte uzel **závislosti** > uzlů**analyzátory** > **Microsoft. dotnet. Analyzer. Compatibility**. Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost sady pravidel** a vyberte požadovanou možnost.

![Snímek obrazovky Průzkumník řešení znázorňující diagnostiku a automaticky otevírané okno se závažností sady pravidel "](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Viz také:

- Představujeme Blogový příspěvek k [analyzátoru API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .
- Ukázkové video [analyzátoru API](https://youtu.be/eeBEahYXGd0) na YouTube
