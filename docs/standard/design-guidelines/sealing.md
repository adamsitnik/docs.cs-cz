---
title: Zapečetění
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: c8aeb5ce3d93755f30bf68732592a08d7af54957
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646656"
---
# <a name="sealing"></a>Zapečetění
Jednou z funkcí objektově orientované rozhraní je, že vývojáři můžete rozšířit a přizpůsobit způsoby neočekávané návrháři rozhraní framework. Toto je výkon a nebezpečí extensible návrhu. Při navrhování rozhraní framework je, proto velmi důležité, pečlivě navrhování pro rozšiřitelnost ho potřebujete a omezit rozšiřitelnosti, když je nebezpečné.  
  
 Zapečetění je výkonný mechanismus, který brání rozšiřitelnosti. Můžete zapečeťte třídu nebo jednotlivé členy. Zapečetění třídu zabraňuje uživatelům dědění ze třídy. Zapečetění člen zabraňuje uživatelům v přepsání určitého člena.  
  
 **X DO NOT** zapečetit třídy bez nutnosti důvodem k tomu.  
  
 Zapečetění třídu, protože nelze myslíte, že rozšíření scénáře není dobrý důvod. Dědit ze tříd z různých důvodů nonobvious, jako je přidání členů pohodlí, jako jsou uživatelé rozhraní Framework. Zobrazit [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md) příklady nonobvious důvodů uživatelé chtějí dědit z typu.  
  
 Oprávněné důvody pro zapečetění třídy zahrnují následující:  
  
-   Třída je statická třída. Zobrazit [návrh statické třídy](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Třídy ukládá citlivé na zabezpečení tajné kódy ve zděděných chráněných členů.  
  
-   Třída dědí mnoho virtuální členy a náklady na jejich jednotlivě zapečetění by převážit nad výhodami opuštění nezapečetěné třídy.  
  
-   Třída je atribut, který vyžaduje velmi rychlé zpracování runtime vyhledat. Zapečetěné atributy mají mírně vyšší úrovně výkonu než nezapečetěné. Zobrazit [atributy](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X DO NOT** deklarovat chráněný nebo virtuální členy v zapečetěných typech.  
  
 Dle definice nelze dědit zapečetěné typy z. To znamená, že nelze volat chráněné členy v zapečetěných typech a nedají se přepsat virtuální metody zapečetěných typů.  
  
 **✓ CONSIDER** zapečetění členů, které můžete přepsat.  
  
 Problémy, které můžou být výsledkem Představujeme virtuální členy (popsáno v [virtuální členy](../../../docs/standard/design-guidelines/virtual-members.md)) použít k přepsání, i když se do menší míry. Zapečetění přepsání chrání před tyto problémy od tohoto bodu v hierarchii dědičnosti.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)
