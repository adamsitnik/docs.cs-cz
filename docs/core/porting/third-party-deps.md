---
title: Analyzovat závislosti na kód portu pro .NET Core
description: Naučte se analyzovat externí závislosti, abyste mohli přenést projekt z .NET Framework do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 5fa5a20e9a2b5427401835a0c1c6e1845d86c3ef
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798791"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analyzovat závislosti na kód portu pro .NET Core

Chcete-li svůj kód přenést do rozhraní .NET Core nebo .NET Standard, je nutné pochopit závislosti. Externí závislosti jsou balíčky NuGet nebo `.dll`s, na které odkazujete v projektu, ale nevytváříte sami sebe.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migrace balíčků NuGet do `PackageReference`

.NET Core používá [PackageReference](/nuget/consume-packages/package-references-in-project-files) k určení závislostí balíčku. Pokud používáte [balíčky. config](/nuget/reference/packages-config) k určení balíčků v projektu, je nutné ji převést na formát `PackageReference`, protože `packages.config` není v rozhraní .NET Core podporován.

Informace o tom, jak migrovat, najdete v článku [migrace ze souboru Packages. config na PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) .

## <a name="upgrade-your-nuget-packages"></a>Upgrade balíčků NuGet

Po migraci projektu do formátu `PackageReference` musíte ověřit, jestli jsou balíčky kompatibilní s .NET Core.

Nejprve upgradujte balíčky na nejnovější verzi, kterou můžete. To se dá udělat s uživatelským rozhraním správce balíčků NuGet v aplikaci Visual Studio. Je pravděpodobný, že novější verze závislostí balíčku jsou již kompatibilní s .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analýza závislostí balíčku

Pokud jste ještě neověřili, že vaše převedené a upgradované balíčky fungují v .NET Core, existuje několik způsobů, jak to dosáhnout:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analýza balíčků NuGet pomocí nuget.org

V části **závislosti** stránky balíčku můžete zobrazit monikery cílového rozhraní (TFM), které každý balíček podporuje v [NuGet.org](https://www.nuget.org/) .

I když použití webu je jednodušší způsob, jak ověřit kompatibilitu, informace o **závislostech** nejsou v lokalitě k dispozici pro všechny balíčky.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analýza balíčků NuGet pomocí Průzkumníka balíčků NuGet

Balíček NuGet je sada složek, které obsahují sestavení specifická pro konkrétní platformu. Proto je nutné ověřit, zda existuje složka, která obsahuje kompatibilní sestavení v rámci balíčku.

Nejjednodušší způsob, jak zkontrolovat složky balíčku NuGet, je použít nástroj [Průzkumník balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) . Po instalaci použijte následující postup k zobrazení názvů složek:

1. Otevřete Průzkumníka balíčků NuGet.
2. Klikněte na **Otevřít balíček z online informačního kanálu**.
3. Vyhledejte název balíčku.
4. Ve výsledcích hledání vyberte název balíčku a klikněte na **otevřít**.
5. Rozbalte složku *lib* na pravé straně a podívejte se na názvy složek.

Vyhledejte složku s názvy pomocí jednoho z následujících vzorů: `netstandardX.Y` nebo `netcoreappX.Y`.

Tyto hodnoty jsou [cílové monikery rozhraní .NET Framework (TFM)](../../standard/frameworks.md) , které jsou namapovány na verze [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily PŘENOSITELNÉ knihovny tříd (PCL), které jsou kompatibilní s .NET Core.

> [!IMPORTANT]
> Při prohlížení TFM, který balíček podporuje, pamatujte, že `netcoreapp*`, i když je kompatibilní, je jenom pro projekty .NET Core, a ne pro .NET Standard projekty.
> Knihovna, která cílí jenom na `netcoreapp*` a ne `netstandard*`, může být spotřebovaná jenom jinými aplikacemi .NET Core.

## <a name="net-framework-compatibility-mode"></a>Režim kompatibility .NET Framework

Po analýze balíčků NuGet se může stát, že budou cílit jenom na .NET Framework.

Počínaje .NET Standard 2,0 byl zaveden režim kompatibility .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard a .NET Core odkazovat na .NET Framework knihovny. Odkazování na knihovny .NET Framework nefunguje pro všechny projekty, například pokud knihovna používá rozhraní API Windows Presentation Foundation (WPF), ale odblokuje mnoho scénářů přenosu.

Při odkazování na balíčky NuGet, které cílí na .NET Framework ve vašem projektu, jako je například [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), získáte upozornění záložního balíčku ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobně jako v následujícím příkladu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Toto upozornění se zobrazí, když přidáte balíček a pokaždé, když ho sestavíte, abyste se ujistili, že balíček otestujete s vaším projektem. Pokud projekt pracuje podle očekávání, můžete toto upozornění potlačit úpravou vlastností balíčku v aplikaci Visual Studio nebo ruční úpravou souboru projektu ve svém oblíbeném editoru kódu.

Chcete-li potlačit upozornění úpravou souboru projektu, vyhledejte položku `PackageReference` balíčku, pro který chcete upozornění potlačit, a přidejte atribut `NoWarn`. Atribut `NoWarn` přijímá čárkami oddělený seznam všech ID upozornění. Následující příklad ukazuje, jak potlačit upozornění `NU1701` pro balíček `Huitian.PowerCollections` úpravou souboru projektu ručně:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Další informace o potlačení upozornění kompilátoru v aplikaci Visual Studio naleznete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co dělat, když se závislost balíčku NuGet nespustí v .NET Core

Existuje několik věcí, které můžete udělat, pokud balíček NuGet, na kterém závisíte, neběží na .NET Core:

1. Pokud je projekt Open Source a hostovaný někde jako GitHub, můžete vývojáře přímo zapojit.
2. Autora můžete kontaktovat přímo na [NuGet.org](https://www.nuget.org/). Vyhledejte balíček a na levé straně stránky balíčku klikněte na **vlastníci kontaktní** osoby.
3. Můžete vyhledat jiný balíček, který běží v .NET Core, který provede stejnou úlohu jako balíček, který jste používali.
4. Můžete se pokusit napsat kód, který balíček prováděl sami.
5. Závislost na balíčku můžete eliminovat tak, že změníte funkčnost vaší aplikace alespoň do chvíle, kdy bude k dispozici kompatibilní verze balíčku.

Pamatujte na to, že open source projekty údržba a vydavatelé balíčků NuGet jsou často dobrovolníkem. Přispívají vzhledem k tomu, že se na danou doménu zajímá, je to zdarma a často mají jinou denní úlohu. Nezapomeňte to mít na vědomí, že při kontaktování s žádostí o podporu .NET Core.

Pokud nemůžete problém vyřešit pomocí některé z výše uvedených verzí, možná budete muset přenést na rozhraní .NET Core později.

Tým .NET by chtěl zjistit, které knihovny jsou pro podporu rozhraní .NET Core nejdůležitější. Můžete odeslat e-mail dotnet@microsoft.com o knihovnách, které chcete použít.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analyzovat závislosti, které nejsou balíčky NuGet

Může se jednat o závislost, která není balíčkem NuGet, jako je například knihovna DLL v systému souborů. Jediným způsobem, jak určit přenositelnost této závislosti, je spustit nástroj [analyzátor přenositelnosti .NET](https://github.com/Microsoft/dotnet-apiport) . Nástroj může analyzovat sestavení, která cílí na .NET Framework, a identifikovat rozhraní API, která nejsou přenosné na jiné platformy .NET, jako je .NET Core. Nástroj můžete spustit jako konzolovou aplikaci nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).

>[!div class="step-by-step"]
>[Next](libraries.md)
