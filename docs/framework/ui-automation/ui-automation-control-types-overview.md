---
title: Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 3c53d07cc6ebbd5259a4bfb5224c486481167c10
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042235"
---
# <a name="ui-automation-control-types-overview"></a>Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy ovládacích prvků jsou známé identifikátory, které lze použít k určení toho, jaký typ ovládacího prvku konkrétní element představuje, například pole se seznamem nebo tlačítko.  
  
 Má-li dobře známý identifikátor, je snazší pro zařízení s podporou technologie, aby určila, jaké typy ovládacích prvků jsou [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] k dispozici v nástroji a jak pracovat s ovládacími prvky.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Požadavky typu ovládacího prvku automatizace uživatelského rozhraní  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy ovládacích prvků poskytují sadu podmínek, které musí poskytovatelé splňovat. Pokud jsou splněny tyto podmínky, může ovládací prvek použít název konkrétního typu ovládacího prvku. Každý typ ovládacího prvku má podmínky pro následující:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vzory ovládacích prvků – které řídicí vzory musí být podporovány, které vzory ovládacích prvků jsou volitelné a které řídicí vzory nesmí být podporovány ovládacím prvkem.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hodnoty vlastností – které hodnoty vlastností jsou podporovány.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Stromová struktura – požadovaná [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura pro ovládací prvek.  
  
 Když ovládací prvek splňuje podmínky pro určitý typ ovládacího prvku, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> hodnota vlastnosti bude označovat, že typ ovládacího prvku.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Aktuální typy ovládacích prvků automatizace uživatelského rozhraní  
 Následující seznam obsahuje aktuální sadu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typů ovládacích prvků:  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko](ui-automation-support-for-the-button-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku dokument](ui-automation-support-for-the-document-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav](ui-automation-support-for-the-edit-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku skupina](ui-automation-support-for-the-group-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku záhlaví](ui-automation-support-for-the-header-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku hypertextový odkaz](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek](ui-automation-support-for-the-image-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam](ui-automation-support-for-the-list-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku nabídka](ui-automation-support-for-the-menu-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno](ui-automation-support-for-the-pane-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku oddělovač](ui-automation-support-for-the-separator-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník](ui-automation-support-for-the-slider-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta](ui-automation-support-for-the-tab-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tabulka](ui-automation-support-for-the-table-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku text](ui-automation-support-for-the-text-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku jezdec](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku strom](ui-automation-support-for-the-tree-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku okno](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType>
