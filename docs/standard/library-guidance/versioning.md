---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: 9250e48707c0ea72cdf8bef9663f5a3516309b86
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969008"
---
# <a name="versioning"></a>Správa verzí

Knihovna softwaru je ve verzi 1,0 jenom zřídka. Dobrá knihovna se vyvíjí v průběhu času, přidávání funkcí, opravy chyb a zlepšení výkonu. Je důležité, abyste si vyuvolnili nové verze knihovny .NET, která poskytuje další hodnotu s každou verzí bez přerušení stávajících uživatelů.

## <a name="breaking-changes"></a>Změny způsobující chyby

Informace o zpracování nejnovějších změn mezi verzemi najdete v tématu [přerušující změny](./breaking-changes.md).

## <a name="version-numbers"></a>Čísla verzí

Knihovna .NET má mnoho způsobů, jak určit verzi. Nejdůležitější jsou tyto verze:

### <a name="nuget-package-version"></a>Verze balíčku NuGet

[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazuje v NuGet.org, správce balíčků NuGet sady Visual Studio a při použití balíčku se přidá do zdrojového kódu. Verze balíčku NuGet je číslo verze, které se uživatelům obvykle uvidí a na něj budou odkazovat, když budou komunikovat s verzí knihovny, kterou používají. Verzi balíčku NuGet používá NuGet a nemá žádný vliv na chování za běhu.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet. Například `Newtonsoft.Json` . +  `11.0.2` Balíček s příponou je předběžná verze balíčku a má speciální chování, které je ideální pro testování. Další informace najdete v tématu [předběžné verze balíčků](./nuget.md#pre-release-packages).

Vzhledem k tomu, že verze balíčku NuGet je nejvíce viditelná pro vývojáře, je vhodné ji aktualizovat pomocí [sémantického správy verzí (SemVer)](https://semver.org/). SemVer označuje význam změn mezi vydanými verzemi a pomáhá vývojářům v rozhodování o tom, jaká verze se má použít. Například v `1.0` `2.0` případě, že znamená, že existují potenciálně zásadní změny.

**✔️ zvažte** použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.

**✔️** použít verzi balíčku NuGet ve veřejné dokumentaci, protože se jedná o číslo verze, které se uživatelům běžně zobrazuje.

při uvolňování nestabilního balíčku **✔️** zahrnout příponu předběžné verze.

> Uživatelé musí souhlasit s načtením předběžných balíčků, aby porozuměli tomu, že balíček není kompletní.

### <a name="assembly-version"></a>Verze sestavení

Verze sestavení je to, co modul CLR používá za běhu k výběru verze sestavení, které se má načíst. Výběr sestavení pomocí správy verzí se vztahuje pouze na sestavení se silným názvem.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR požaduje přesnou shodu pro načtení silného pojmenovaného sestavení. Například `Libary1, Version=1.0.0.0` byl zkompilován s odkazem na `Newtonsoft.Json, Version=11.0.0.0`. .NET Framework načte pouze tuto přesnou verzi `11.0.0.0`. Pro načtení jiné verze za běhu musí být přesměrování vazby přidáno do konfiguračního souboru aplikace .NET.

Silné pojmenování v kombinaci s verzí sestavení umožňuje [striktní načítání verzí sestavení](../assembly/versioning.md). I když silné pojmenování knihovny má několik výhod, často to vede k výjimkám za běhu, že se sestavení nedá najít a vyžaduje, `web.config` aby se `app.config` opravily / [přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) . Načítání sestavení .NET Core bylo uvolněno a modul CLR .NET Core bude automaticky načítat sestavení za běhu s vyšší verzí.

**✔️ zvažte** pouze hlavní verzi v AssemblyVersion.

> například knihovna 1,0 a 1.0.1 knihovny mají AssemblyVersion `1.0.0.0`, zatímco knihovna 2,0 obsahuje `2.0.0.0`AssemblyVersion. Pokud se verze sestavení nemění méně často, snižuje se přesměrování vazby.

**✔️ zvažte** zachování hlavního čísla verze AssemblyVersion a verze balíčku NuGet v synchronizaci.

> AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a kvalifikované typy názvů sestavení ve zprávách o výjimkách. Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře, kteří používají verzi.

**❌** Nemají pevně AssemblyVersion.

> I když nezměněný AssemblyVersion vybrání nutnosti přesměrování vazby, znamená to, že v globální mezipaměti sestavení (GAC) může být nainstalována pouze jedna verze sestavení. Aplikace, které odkazují na sestavení v globální mezipaměti sestavení (GAC), budou také přerušit, pokud jiná aplikace aktualizuje sestavení GAC s nezměněnými změnami.

### <a name="assembly-file-version"></a>Verze souboru sestavení

Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Zobrazuje se v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")

**✔️ zvažte** zahrnutí čísla sestavení průběžné integrace jako revize AssemblyFileVersion.

> Například sestavíte 1.0.0 verze projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.

**✔️** použít formát `Major.Minor.Build.Revision` pro verzi souboru.

> I když verze souboru není rozhraním .NET nikdy používána, [systém Windows očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) je `Major.Minor.Build.Revision` ve formátu. Pokud verze nedodržuje tento formát, bude vyvolána výstraha.

### <a name="assembly-informational-version"></a>Informační verze sestavení

Informační verze sestavení se používá k záznamu dalších informací o verzi a nemá žádný vliv na chování za běhu. Nastavení této verze je volitelné. Pokud používáte zdrojový odkaz, bude tato verze nastavena pro sestavení s verzí balíčku NuGet a verzí správy zdrojového kódu. Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestaveno. Další informace najdete v tématu [zdrojový odkaz](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starší verze sady Visual Studio vyvolají upozornění sestavení, pokud tato verze nedodržuje `Major.Minor.Build.Revision`formát. Upozornění lze bezpečně ignorovat.

**❌ Se vyhnout** nastavení informační verze sestavení sami.

> Povolí, aby SourceLink automaticky vygenerovala verzi, která obsahuje metadata nástroje NuGet a správy zdrojového kódu.

>[!div class="step-by-step"]
>[Předchozí](publish-nuget-package.md)Další
>[](breaking-changes.md)
