---
title: Pokyny k návrhu typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650099"
---
# <a name="type-design-guidelines"></a>Pokyny k návrhu typu
Z pohledu CLR existují jenom dvě kategorie typů – typy odkazu a typy hodnot, ale pro účely diskuse o návrhu rozhraní framework, jsme typy rozdělit do více logických skupin, každou s vlastní pravidla konkrétního návrhu.  
  
 Třídy jsou obecné případ odkazových typů. Tvoří hromadné typy ve většině platforem. Třídy je splatná jejich oblíbenosti bohaté sady objektově orientovaných vlastností, které podporují a jejich obecné použitelnosti. Základní třídy a abstraktní třídy jsou speciální logických skupin souvisejících do rozšíření.  
  
 Rozhraní jsou typy, které je možné implementovat pomocí odkazové typy a typy hodnot. Proto mohou sloužit jako kořeny hierarchie polymorfní typy odkazů a typy hodnot. Kromě toho rozhraní umožňuje simulovat vícenásobná dědičnost, což není podporováno nativně modulem CLR.  
  
 Struktury jsou obecném případě typy hodnot a by se mělo vyhradit pro malé, jednoduché typy, podobně jako primitiva jazyka.  
  
 Výčty představují zvláštní případ typů hodnot, které slouží k definování krátký sady hodnot, například dny v týdnu, barvy konzoly a tak dále.  
  
 Statické třídy jsou typy, které má být kontejnery pro statické členy. Běžně se používají k poskytování klávesové zkratky pro jiné operace.  
  
 Delegáty, výjimky, atributy, pole a kolekce jsou všechny speciální případy typy odkazů, které jsou určené pro konkrétní použití, a pokyny pro jejich návrhu a využití jsou jinde popsaných v této příručce.  
  
 **✓ DO** zajistěte, aby byl každý typ dobře definované sadě souvisejících členů, nejen náhodné kolekce funkcí, které nejsou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba mezi třídou a strukturou](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Návrh abstraktní třídy](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Návrh statické třídy](../../../docs/standard/design-guidelines/static-class.md)  
 [Návrh rozhraní](../../../docs/standard/design-guidelines/interface.md)  
 [Návrh struktury](../../../docs/standard/design-guidelines/struct.md)  
 [Návrh výčtu](../../../docs/standard/design-guidelines/enum.md)  
 [Vnořené typy](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
