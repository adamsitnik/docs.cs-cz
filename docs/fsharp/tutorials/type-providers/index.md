---
title: Zprostředkovatelé typů
description: Zjistěte, jak F# poskytovatel typu je komponenta, která poskytuje typy, vlastnosti a metody pro použití ve svých programech.
ms.date: 04/02/2018
ms.openlocfilehash: 39000fd1ca2af78afd1c333816fe9d5c0e2517cb
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611630"
---
# <a name="type-providers"></a>Zprostředkovatelé typů

Poskytovatel typů jazyka F# je komponenta, která poskytuje typy, vlastnosti a metody pro váš program. Zprostředkovatelé typů generovat, co jsou označovány jako **poskytuje typy**, které jsou generovány F# kompilátoru a jsou založené na externí zdroj dat.

Například F# poskytovatel typů pro SQL můžete vygenerovat typy, které představují tabulky a sloupce v relační databázi. Ve skutečnosti se jedná, co [SQLProvider](https://fsprojects.github.io/SQLProvider/) zprostředkovatel typu nemá.

Za předpokladu, že typy, závisí na vstupních parametrů zprostředkovateli typu. Takové zadání může být vzorový zdroj dat (např. soubor schématu JSON), odkazuje přímo na externí službu nebo připojovací řetězec pro zdroj dat adresy URL. Poskytovatel typů dokáže také zajistit, že skupiny typů byly rozbaleny dle potřeby; To znamená jsou rozbaleny Pokud typy ve skutečnosti odkazuje váš program. To umožňuje přímou integraci rozsáhlých informačních prostorů přístupných na vyžádání, jako jsou například online datové trhy, způsobem využívajícím silné typy.

## <a name="generative-and-erased-type-providers"></a>Zprostředkovatelé typů tvoří a mazání

Poskytovatelé typů jsou ve dvou formách: Tvoří a mazání.

Tvoří poskytovatelů typů vytvořit typy, které lze zapsat jako typy .NET do sestavení, ve kterém se vytváří. To umožňuje jejich využít z kódu v jiných sestaveních. To znamená, že zadaný reprezentaci zdroje dat obecně musí být ten, který je možné použít k reprezentaci s typy .NET.

Mazání poskytovatelů typů vytvořit typy, které můžete používat jen v sestavení nebo projekt, který se generují z. Typy jsou dočasné; To znamená nejsou zapsány do sestavení a nemůže být zaplněny kódem v jiných sestaveních. Může obsahovat *zpožděné* členy, abyste mohli používat k dispozici typy z potenciálně nekonečné informační prostor. Jsou vhodné pro použití malou část velké a propojených zdroj.

## <a name="commonly-used-type-providers"></a>Nejčastěji používané zprostředkovatelů typů

Následující knihovny nejběžněji používanými obsahovat poskytovatelů typů pro různé účely:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) obsahuje typ zprostředkovatelů pro JSON, XML, CSV a HTML dokumentů formátů a prostředky.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje přístup k relaci databáze pomocí mapování objektu s silného typu a F# dotazů LINQ na tyto datové zdroje.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sadu poskytovatelů typů pro kompilaci změnami vkládání T-SQL v F#.
- [Zprostředkovatel Azure typu úložiště](https://fsprojects.github.io/AzureStorageTypeProvider/) poskytuje typy pro Azure Blobs, Tables a Queues, umožňuje přístup k těmto prostředkům, aniž byste museli zadat názvy prostředků jako řetězce v celém programu.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) obsahuje **GraphQLProvider**, která poskytuje typy založené na serveru GraphQL zadaný pomocí adresy URL.

V případě potřeby můžete [vytvořte vlastní vlastní poskytovatele typů](creating-a-type-provider.md), nebo odkaz na poskytovatele typů vytvořené jinými uživateli. Předpokládejme například organizaci, která má datovou službu poskytující velké a zvyšující se množství pojmenovaných datových sad, přičemž každá z nich má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typů, který schémata přečte a nabídne programátorům nejnovější dostupné datové sady se silnými typy.

## <a name="see-also"></a>Viz také:

- [Kurz: Vytvoření zprostředkovatele typů](creating-a-type-provider.md)
- [Referenční dokumentace jazyka F#](../../language-reference/index.md)
- [Visual F#](../../index.md)