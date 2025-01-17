---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl type
- UI Automation, Tab control type
- control types, Tab
ms.assetid: f8be2732-836d-4e4d-85e2-73aa39479bf4
ms.openlocfilehash: defe2ef5fc4deedfdf78b0f2b8a5ddd6632cbac9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040955"
---
# <a name="ui-automation-support-for-the-tab-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku karta. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost použít. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků.  
  
 Ovládací prvek karta je podobný oddělovači v poznámkovém bloku nebo jmenovkách v souboru CAB. Pomocí ovládacího prvku karta může aplikace definovat více stránek pro stejnou oblast okna nebo dialogového okna.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku karta. Požadavky platí pro všechny ovládací prvky karty, bez [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]ohledu na to [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům karty, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Karta<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>Posuvník (0 nebo 1)<br /><br /> <ul><li>Tlačítko (0 nebo 2)</li></ul></li></ul>|Karta<br /><br /> -TabItem (1 nebo více)|  
  
 Ovládací prvky karty mají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podřízené prvky založené na typu ovládacího prvku položka karty. Když jsou položky karty seskupeny (například jako v aplikacích systém Microsoft Office 2007), typ ovládacího prvku karta může také hostovat typy ovládacích prvků skupin pro položky seskupené karty, jak ukazuje následující stromová struktura.  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Karta<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>Skupina (0 nebo více)<br /><br /> <ul><li>TabItem (0 nebo více)</li></ul></li><li>Posuvník (0 nebo více)<br /><br /> <ul><li>Tlačítko (0 nebo 2)</li></ul></li></ul>|Karta<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>Skupina (0 nebo více)<br /><br /> <ul><li>TabItem (0 nebo více)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro typ ovládacího prvku karta. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Value|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek karta zřídka vyžaduje vlastnost Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Ne|Ovládací prvek karta nemá žádný bod kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Ovládací prvky karty mají obvykle statický textový popisek, který je vystaven prostřednictvím této vlastnosti.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Karta|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|rážky|Lokalizovaný řetězec odpovídající typu ovládacího prvku karta|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Pravda|Typ ovládacího prvku karta musí být schopný přijmout fokus klávesnice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Klient obvykle volá SetFocus na ovládacím prvku karta a jedna z jeho položek předává fokus klávesnice ovládacímu prvku karta. Může se stát, že některé kontejnery karet mají fokus bez nastavení fokusu na jednu z jejích položek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Ovládací prvek karta je vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek karta je vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromové struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Viz poznámky.|Ovládací prvek karta musí vždy označovat, zda je umístěn vodorovně nebo svisle.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky karty. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Řídicí vzorek/vlastnost vzoru|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Všechny ovládací prvky karty musí podporovat vzorek výběru.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Pravda|Ovládací prvky karty vždy vyžadují, aby byl proveden výběr.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Ovládací prvky karty jsou vždy kontejnery s jedním výběrem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závislosti|Vzor posouvání musí být podporován v ovládacím prvku karta má widgety, které umožňují procházení sady položek karet.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky karty. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.Tab>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
