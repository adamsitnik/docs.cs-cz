---
title: Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 13ebc6aefe925ecefe48a9b0fa8cf7a6ecd3c454
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042955"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k získání podrobností o atributu textu z rozsahu textu, který zahrnuje více hodnot atributu. Rozsah textu může odpovídat aktuálnímu umístění stříšky (nebo degenerovat výběr) v rámci dokumentu, souvislého výběru textu, kolekce nesouvislých výběrů textu nebo celého textového obsahu dokumentu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak získat <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z oblasti textu, kde <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> vrací <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> objekt.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 Vzor ovládacího prvku, v rámci společné <xref:System.Windows.Automation.Text.TextPatternRange> třídy, podporuje základní atributy textu, vlastnosti a metody. <xref:System.Windows.Automation.TextPattern> Pro funkce specifické pro ovládací prvky, které nejsou podporovány <xref:System.Windows.Automation.TextPattern> nástrojem <xref:System.Windows.Automation.Text.TextPatternRange>nebo, <xref:System.Windows.Automation.AutomationElement> Třída poskytuje metody pro klienta automatizace uživatelského rozhraní pro přístup k odpovídajícímu nativnímu objektovému modelu.  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](ui-automation-textpattern-overview.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](find-and-highlight-text-using-ui-automation.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Získání textových atributů s použitím automatizace uživatelského rozhraní](obtain-text-attributes-using-ui-automation.md)
