---
ms.openlocfilehash: 4b87fb0161059eb9df919a64a9966c00177caf89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858533"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Přístup k WPF DataGrid vybrané položky z obslužné rutiny události UnloadingRow DataGrid může způsobit NullReferenceException

|   |   |
|---|---|
|Podrobnosti|Kvůli chybě v rozhraní .NET Framework 4.5, obslužné rutiny událostí pro <xref:System.Windows.Controls.DataGrid> události týkající se odebrání řádek může způsobit, že <xref:System.NullReferenceException?displayProperty=name> která je vyvolána, pokud budou přistupovat k <xref:System.Windows.Controls.DataGrid>společnosti <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

