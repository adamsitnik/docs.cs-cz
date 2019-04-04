---
title: Nasazení aplikace .NET core
description: Další informace o způsobech, jak nasadit aplikaci .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 12/03/2018
ms.custom: seodec18
ms.openlocfilehash: 6f88659fcef49eba9344d3c4b2f0245b4072d7ab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745444"
---
# <a name="net-core-application-deployment"></a>Nasazení aplikace .NET core

Můžete vytvořit tři typy nasazení pro aplikace .NET Core:

- Nasazení závisí na architektuře. Jak již název napovídá, závisí na architektuře nasazení (chyba) spoléhá na přítomnost sdílené systémová verzi .NET Core v cílovém systému. Protože .NET Core je již k dispozici, vaše aplikace je také přenosné mezi instalacemi sady .NET Core. Vaše aplikace obsahuje pouze vlastní kód a případných závislostí třetích stran, které nejsou na knihovny .NET Core. Obsahují FDDs *.dll* soubory, které se dají spouštět pomocí [nástrojů dotnet](../tools/dotnet.md) z příkazového řádku. Například `dotnet app.dll` spustí aplikaci s názvem `app`.

- Samostatná nasazení. Na rozdíl od disketové jednotky samostatná nasazení (SCD) nemusí spoléhat na přítomnost sdílené komponenty v cílovém systému. Všechny komponenty, včetně knihoven .NET Core a .NET Core runtime jsou součástí aplikace a jsou izolované od jiných aplikací .NET Core. SCDs zahrnují spustitelný soubor (například *app.exe* na platformách Windows pro aplikaci s názvem `app`), což je přejmenované verze hostitele specifické pro platformu .NET Core a *.dll* souboru (například *app.dll*), což je aplikace skutečný.

- Závisí na architektuře spustitelných souborů. Vytvoří spustitelný soubor, který běží na cílovou platformu. Podobně jako FDDs, závisí na architektuře spustitelných souborů (FDE) jsou specifické pro platformu a nejsou samostatné. Tato nasazení spoléhat na přítomnost sdílené systémová verzi .NET Core pro spuštění. Na rozdíl od SCD obsahuje vaši aplikaci pouze váš kód a případných závislostí třetích stran, které nejsou na knihovny .NET Core. FDEs vytvoří spustitelný soubor, který běží na cílovou platformu.

## <a name="framework-dependent-deployments-fdd"></a>Nasazení závisí na architektuře (chyba)

Pro disketové jednotky nasaďte jenom aplikace a závislostí třetích stran. Vaše aplikace bude používat verzi .NET Core, který je k dispozici v cílovém systému. Toto je výchozí model nasazení pro aplikace .NET Core a ASP.NET Core, které cílí na .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Proč vytvořit nasazení závisí na architektuře?

Nasazení disketové jednotky má několik výhod:

- Není nutné definovat cílový operační systémy, které se spustí aplikace .NET Core na předem. Vzhledem k tomu .NET Core používá běžný formát souborů PE pro spustitelné soubory a knihovny bez ohledu na operační systém, .NET Core může spustit vaši aplikaci bez ohledu na příslušný operační systém. Další informace o souborovém formátu PE najdete v tématu [formát souborů sestavení .NET](../../standard/assembly/file-format.md).

- Velikost nasazovaného balíčku je malá. Pouze nasazení aplikace a jeho závislosti, ne .NET Core samotný.

- Pokud nejsou přepsány, FDDs použije nejnovější obsluhované runtime nainstalovaného v cílovém systému. To umožňuje vaší aplikaci použít nejnovější opravenou verzi modulu runtime .NET Core. 

- Více aplikací použít stejné instalace .NET Core, což snižuje jak disku místa a využití paměti v hostitelských systémech.

Existuje také několik nevýhody:

- Vaše aplikace může běžet jenom v případě, že verze sady .NET Core vaší aplikaci zaměřuje [nebo novější verze](../versions/selection.md#framework-dependent-apps-roll-forward), je již nainstalována v hostitelském systému.

- Je možné pro modul runtime .NET Core a knihovny, které chcete změnit bez vašeho vědomí v budoucích vezích se. Ve výjimečných případech může změnit chování vaší aplikace.

## <a name="self-contained-deployments-scd"></a>Samostatná nasazení (SCD)

Pro samostatné nasazení nasadíte aplikaci a všechny požadované závislosti spolu s verzi .NET Core, který jste použili k vytvoření aplikace třetích stran. Vytvoření SCD neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na různých platformách, takže tyto musí být k dispozici před spuštěním aplikace. Další informace o verzi vazbu za běhu, najdete v článku na [vázání verze v .NET Core](../versions/selection.md).

Počínaje NET Core 2.1 SDK (verze 2.1.300), .NET Core podporuje *opravy verze dopředné posunutí*. Při vytváření samostatná nasazení nástroje pro .NET Core automaticky zahrnují obsluhované runtime verze .NET Core, která vaše aplikace cílí. (Nejnovější obsluhované runtime obsahuje opravy zabezpečení a ostatní opravy chyb). Obsluhované runtime nemusí být k dispozici ve vašem systému sestavení; stáhnout je automaticky z NuGet.org. Další informace, včetně informací o tom, jak vyjádřit výslovný nesouhlas opravy verze Posunutí vpřed, naleznete v tématu [samostatná nasazení modulu runtime dopředné posunutí](runtime-patch-selection.md).

Disketové jednotky a SCD nasazení používat spustitelné soubory samostatného hostitele, tak pro SCD můžou zaregistrovat hostitele spustitelný soubor s podpisem vydavatele.

### <a name="why-deploy-a-self-contained-deployment"></a>Proč nasazovat samostatná nasazení?

Samostatná nasazení má dvě hlavní výhody:

- Máte výhradní kontrolu nad verzi .NET Core, který je nasazen s vaší aplikací. .NET core lze udržovat jenom vámi.

- Můžete si být jistí, že cílový systém můžete spustit aplikace .NET Core, vzhledem k tomu, že zadáváte verzi .NET Core, který se spustí na.

Obsahuje také některé nevýhody:

- Protože .NET Core je zahrnutý v balíčku pro nasazení, je nutné vybrat cílové platformy, pro které je předem vytvářet balíčky pro nasazení.

- Velikost nasazovaného balíčku je relativně velké, protože je nutné zahrnout .NET Core i vaše aplikace a jeho závislostí třetích stran.

  Od verze rozhraní .NET Core 2.0, můžete snížit velikost vašeho nasazení v systémech Linux přibližně 28 MB pomocí .NET Core [ *invariantní režimu globalizace*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Obvykle, .NET Core v Linuxu se může spolehnout [ICU knihovny](http://icu-project.org) globalizace podporu. Ve výchozím režimu, nejsou součástí vašeho nasazení knihoven a všechny jazykové verze se chovat jako [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Nasazení do systému mnoho samostatné aplikace .NET Core může spotřebovat významné množství místa na disku, od každé aplikace duplicitní soubory .NET Core.

## <a name="framework-dependent-executables-fde"></a>Závisí na architektuře spustitelných souborů (FDE)

Spouští se s nástroji .NET Core 2.2, můžete nasadit aplikaci jako FDE, včetně případných požadovaných závislostí třetích stran. Vaše aplikace bude používat verzi .NET Core, který je nainstalován v cílovém systému.

### <a name="why-deploy-a-framework-dependent-executable"></a>Proč nasazení závisí na architektuře spustitelného souboru?

Nasazení FDE má několik výhod:

- Velikost nasazovaného balíčku je malá. Pouze nasazení aplikace a jeho závislosti, ne .NET Core samotný.

- Více aplikací použít stejné instalace .NET Core, což snižuje jak disku místa a využití paměti v hostitelských systémech.

- Vaše aplikace může být spuštěna voláním publikované spustitelný soubor bez vyvolání `dotnet` nástroj přímo.

Existuje také několik nevýhody:

- Vaše aplikace může běžet jenom v případě, že verze sady .NET Core vaší aplikaci zaměřuje [nebo novější verze](../versions/selection.md#framework-dependent-apps-roll-forward), je již nainstalována v hostitelském systému.

- Je možné pro modul runtime .NET Core a knihovny, které chcete změnit bez vašeho vědomí v budoucích vezích se. Ve výjimečných případech může změnit chování vaší aplikace.

- Je nutné publikovat aplikace pro každou cílovou platformu.

## <a name="step-by-step-examples"></a>Podrobné příklady

Podrobné příklady nasazení aplikace .NET Core pomocí nástrojů příkazového řádku, naleznete v tématu [nasazení aplikace .NET Core pomocí nástrojů CLI](deploy-with-cli.md). Podrobné příklady nasazení aplikace .NET Core pomocí sady Visual Studio, najdete v článku [nasazení aplikace .NET Core pomocí sady Visual Studio](deploy-with-vs.md). 

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací .NET Core pomocí nástrojů CLI](deploy-with-cli.md)
- [Nasazení aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)
- [Balíčky, metabalíčky a architektury](../packages.md)
- [.NET core Runtime identifikátor (RID) katalogu](../rid-catalog.md)
