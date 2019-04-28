---
title: Návrh struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: cc5b8d7effda31b0236477b217bccf5cf2137f8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650138"
---
# <a name="struct-design"></a>Návrh struktury
Typ hodnoty pro obecné účely se nejčastěji označuje jako struktury, jeho klíčové slovo C#. Tato část obsahuje pokyny pro návrh obecné struktury.  
  
 **X DO NOT** zadejte výchozí konstruktor pro struktury.  
  
 Za toto pravidlo umožňuje pole struktur, který se má vytvořit bez nutnosti spuštění konstruktoru pro každou položku pole. Všimněte si, že C# nepovoluje struktury mají výchozí konstruktory.  
  
 **X DO NOT** definování typů měnitelný hodnotu.  
  
 Proměnlivé hodnoty typy mají několik problémů. Například typ hodnoty návratu metoda getter vlastnosti volající obdrží kopii. Vzhledem k tomu, že kopie je vytvořena implicitně, vývojáři se nemusíte být vědomi, mutace kopii a na původní hodnotu. Některé jazyky (dynamické jazyky, zejména) také mít problémy pomocí proměnlivé hodnoty typů, protože i lokální proměnné, při dereferenci, způsobit, že kopie má být provedeno.  
  
 **✓ DO** jistotu, že stav, kde všechny instance dat je nastavený na nulu, false, nebo hodnotu null (podle potřeby) je platný.  
  
 To zabraňuje nechtěnému vytváření instancí neplatný při vytváření pole struktury.  
  
 **✓ DO** implementovat <xref:System.IEquatable%601> u typů hodnot.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Metoda u typů hodnot způsobí, že zabalení a jeho výchozí implementace není velmi efektivní, protože používá reflexi. <xref:System.IEquatable%601.Equals%2A> může mít mnohem lepší výkon a může být implementováno tak, aby nezpůsobí zabalení.  
  
 **X DO NOT** explicitně rozšířit <xref:System.ValueType>. Ve skutečnosti většina jazyků to neumožňuje.  
  
 Obecně platí struktury může být velmi užitečné, ale by měla sloužit pouze pro malé, jednu, neměnné hodnoty, které se nesmí použít boxing. často.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Volba mezi třídou a strukturou](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
