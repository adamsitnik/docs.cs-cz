---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 4943ddcdf1bc4e3e32c8d664cbcc5c50ae3959bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543825"
---
# <a name="virtual-members"></a>Virtuální členové
Virtuální členové lze přepsat, čímž se změní chování podtřídy. Jsou na zpětná volání z hlediska rozšiřitelnosti, které poskytují velmi podobné, ale jsou lepší z hlediska provádění výkonu a využití paměti. Navíc můžete virtuální členy přirozenější ve scénářích, které vyžadují vytvoření zvláštní druh existujícího typu (specializace).  
  
 Virtuální členové poskytují vyšší výkon než zpětná volání a události, ale neprovádět lépe než nevirtuální metody.  
  
 Hlavní nevýhodou virtuální členy je, že chování virtuálního člena lze změnit pouze v době kompilace. Chování zpětné volání, lze upravit za běhu.  
  
 Virtuální členy jako zpětná volání (a možná víc než zpětná volání), je nákladné navrhnout, testovat a spravovat, protože jakékoli volání virtuálního členu mohou být přepsána nastaveními v nepředvídatelnými způsoby a může spustit libovolný kód. Navíc je k jasně definovat kontrakt virtuální členy, tedy vyšší náklady na navrhování a dokumentace je většinou potřeba mnohem větší úsilí.  
  
 **X DO NOT** zkontrolujte virtuální členy, pokud máte dobrý důvod k tomu a jste si vědomi veškeré náklady související s návrh, testování a údržbě virtuální členy.  
  
 Virtuální členy jsou méně striktní z hlediska změn, které můžete k nim nevytváří bez porušení kompatibilitu. Navíc jsou pomalejší než nevirtuální členy, většinou, protože volání virtuální členy nejsou vložené.  
  
 **✓ CONSIDER** omezení rozšiřitelnost pouze co je to nezbytně nutné.  
  
 **✓ DO** raději chráněné usnadnění přes veřejnou dostupnost pro virtuální členy. Veřejné členy by měl zajistí možnosti rozšíření (v případě potřeby) ve volání do chráněná virtuální členská funkce.  
  
 Veřejné členy třídy by měly poskytnout správné sady funkcí pro přímé zákazníky této třídy. Virtuální členy jsou určeny k přepsání v podtřídách a chráněné přístupnost je skvělý způsob, jak oboru, ve kterém můžou použít všechny body rozšiřitelnosti virtuální.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
