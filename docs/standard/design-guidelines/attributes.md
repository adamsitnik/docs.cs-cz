---
title: Atributy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785564"
---
# <a name="attributes"></a>Atributy
<xref:System.Attribute?displayProperty=nameWithType> slouží k definování uživatelských atributů, které základní třídy.  
  
 Atributy jsou poznámky, které mohou být přidány pro programovací prvky, jako je například sestavení, typy, členy a parametry. Tyto jsou uložené v metadatech sestavení a je přístupný za běhu pomocí reflexe rozhraní API. Například rozhraní definuje <xref:System.ObsoleteAttribute>, který je možné použít u typu nebo člena k označení, že tento typ nebo člen je zastaralý.  
  
 Atributy mohou mít jednu nebo více vlastností, které přenášejí další data související s atributem. Například `ObsoleteAttribute` by mohl provést další informace o verzi v které typ nebo člen je teď zastaralé a popis nové rozhraní API nahrazení zastaralé rozhraní API.  
  
 Některé vlastnosti atributu je třeba zadat při použití atributu. Tyto jsou označovány jako požadované vlastnosti nebo povinné argumenty, protože jsou reprezentovány jako konstruktor poziční parametry. Například <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> vlastnost <xref:System.Diagnostics.ConditionalAttribute> je povinná.  
  
 Vlastnosti, které není potřeba zadat, když se atribut používá, se nazývají volitelné vlastnosti (nebo nepovinné argumenty). Jsou zobrazeny v nastavitelné vlastnosti. Kompilátory poskytují speciální syntax k nastavení těchto vlastností, při použití atributu. Například <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> představuje vlastnost nepovinný argument.  
  
 **✓ DO** název třídy vlastních atributů s příponou "Atribut."  
  
 **✓ DO** použít <xref:System.AttributeUsageAttribute> vlastních atributů.  
  
 **✓ DO** zadejte nastavit vlastnosti pro volitelné argumenty.  
  
 **✓ DO** zadejte vlastnosti jen get pro povinnými argumenty.  
  
 **✓ DO** zadat parametry konstruktor k chybě při inicializaci vlastnosti odpovídající povinnými argumenty. Každý parametr by měl mít stejný název (i když s jinou velikostí písmen) jako odpovídající vlastnost.  
  
 **X AVOID** poskytuje konstruktor parametry k chybě při inicializaci vlastnosti odpovídající volitelné argumenty.  
  
 Jinými slovy nemají vlastnosti, které lze nastavit pomocí konstruktoru a setter. Toto pravidlo umožňuje velmi explicitní argumenty, které jsou volitelné a které jsou požadovány a díky tomu není nutné dva způsoby provedení stejného kroku.  
  
 **X AVOID** přetížení konstruktory vlastních atributů.  
  
 Máte jenom jeden konstruktor jasně komunikuje uživateli argumenty, které se vyžadují a které jsou volitelné.  
  
 **✓ DO** zapečetit vlastní atribut třídy, pokud je to možné. Díky tomu vyhledávání pro atribut rychleji.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
