---
title: Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: ad2f84fbde512bb99b213bf3b97f2190091d8576
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042993"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IWindowProvider>implementaci, včetně informací <xref:System.Windows.Automation.WindowPattern> o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.WindowPattern> ovládacího prvku slouží k podpoře ovládacích prvků, které poskytují základní funkce založené na oknech v tradičním grafickém uživatelském rozhraní (GUI). Příklady ovládacích prvků, které musí implementovat tento vzor ovládacích prvků, zahrnují okna aplikace nejvyšší úrovně, podřízená okna rozhraní MDI (Multiple Document Interface), okna, modální dialogová okna a okna nápovědy k bublinám s možností změny velikosti.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku okna si všimněte následujících pokynů a konvencí:  
  
- Aby bylo možné podporovat možnost upravit velikost okna a umístění obrazovky pomocí automatizace uživatelského rozhraní, musí ovládací prvek implementovat <xref:System.Windows.Automation.Provider.ITransformProvider> <xref:System.Windows.Automation.Provider.IWindowProvider>kromě.  
  
- Pro implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>jsou obvykle vyžadovány ovládací prvky, které obsahují záhlaví a prvky záhlaví, které umožňují přesunutí ovládacího prvku, jeho velikost, maximalizaci, minimalizaci nebo zavření.  
  
- Ovládací prvky, jako jsou například automaticky otevíraná okna s popisem tlačítka a pole se seznamem nebo nabídky, <xref:System.Windows.Automation.Provider.IWindowProvider>nejsou obvykle implementovány.  
  
- Okna nápovědy k bublinám jsou odlišená od základních popsaných tlačítek pomocí překryvných tlačítek pro tlačítko Zavřít.  
  
- Režim zobrazení na celé obrazovce není podporován IWindowProvider, protože se jedná o konkrétní funkci pro aplikaci a nejedná se o typické chování okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Vyžadovaná členové pro IWindowProvider  
 Pro rozhraní IWindowProvider jsou vyžadovány následující vlastnosti, metody a události.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowInteractionState>|Událost|Není zaručeno být<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> – Když ovládací prvek nepodporuje požadované chování.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> – Pokud parametr není platným číslem.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
