---
title: 'Příklad regulárního výrazu: Vyhledávání atributů HREF'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e743f32637a7e15b4b017bbe30aa02ad8388fbe
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975963"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Příklad regulárního výrazu: Vyhledávání atributů HREF
Následující příklad hledá vstupní řetězec a zobrazí všechny href = "..." a jejich umístění v řetězci.  
  
## <a name="the-regex-object"></a>Objekt regulárního výrazu  
 Protože `DumpHRefs` metodu lze volat více než jednou z uživatelského kódu, použije `static` (`Shared` v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody. To umožňuje modulu regulárních výrazů pro ukládání do mezipaměti regulárního výrazu a zabraňuje nároky na vytvoření nové instance <xref:System.Text.RegularExpressions.Regex> objekt pokaždé, když je volána metoda. A <xref:System.Text.RegularExpressions.Match> objekt se pak použije k iteraci v rámci všechny shody v řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Následující příklad ukazuje volání `DumpHRefs` metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Vzor regulárního výrazu `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`href`|Porovná řetězec "href". Shoda nerozlišuje malá a velká písmena.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`=`|Porovná znaménko rovná se.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Bez přiřazení výsledku zachycené skupině odpovídat jedné z následujících akcí:<br /> <ul><li><p>Uvozovka nebo apostrof, za nímž následuje nula nebo více výskytů libovolného znaku jiného než uvozovka nebo apostrof, za nímž následuje uvozovka nebo apostrof. Skupina s názvem `1` je součástí tohoto modelu.</p></li><li><p>Jeden nebo více znaků prázdné znaky. Skupina s názvem `1` je součástí tohoto modelu.</p></li></ul>|  
|`(?<1>[^"']*)`|Přiřadit žádnému nebo více výskytům libovolného znaku jiného než uvozovka nebo apostrof zachytávající skupina s názvem `1`.|  
|`(?<1>\S+)`|Jeden nebo více znaků prázdné znaky přiřadit zachytávající skupina s názvem `1`.|  
  
## <a name="match-result-class"></a>Třída výsledek porovnání  
 Výsledky hledání jsou uloženy v <xref:System.Text.RegularExpressions.Match> třídu, která poskytuje přístup k všechny podřetězců extrahovaná modulem hledání. Také pamatuje prohledávaný řetězec a regulárních výrazů používá, takže můžete volat <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu za účelem, kde skončilo poslední další spuštění vyhledávání.  
  
## <a name="explicitly-named-captures"></a>Explicitně pojmenované zachycení  
 V tradičních regulární výrazy zachycené závorky jsou automaticky číslované. To vede k dva problémy. Nejprve Pokud regulární výraz je upravena pomocí vložení nebo odstranění závorka, veškerý kód, který odkazuje na číslované zachycování musejí být přepsány, tak, aby odrážela nové číslování. Za druhé protože různých sad závorek často se používají k zajištění dva alternativní výrazy pro přijatelné shody, může být obtížné určit, které ze dvou výrazů ve skutečnosti vrátilo výsledek.  
  
 K řešení těchto problémů <xref:System.Text.RegularExpressions.Regex> třídy podporuje syntaxi `(?<name>…)` pro zachycení shoda do zadané pozice (může mít název slotu pomocí řetězce nebo celé číslo; celých čísel může třeba připomenout, rychleji). Alternativní shody proto pro stejný řetězec, který všechny mohou přesměrováni na jednom místě. V případě konfliktu poslední shody přetáhnout do slotu je úspěšná shoda. (Úplný seznam více shod pro jeden slot je však k dispozici. Zobrazit <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce podrobnosti.)  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
