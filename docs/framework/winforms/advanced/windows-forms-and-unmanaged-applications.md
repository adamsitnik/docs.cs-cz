---
title: Windows Forms a nespravované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: f54f039fd3477c380a2236a93ad8d80b4f7153b2
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441811"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms a nespravované aplikace
Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravované aplikace, se některé upozornění. Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu Windows Forms a nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Poskytuje obecné informace o tom, jak používat a implementaci ovládacích prvků Windows Forms, které pracují s nespravovanými aplikacemi.  
  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Obsahuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> způsob spuštění formulář Windows v nespravované aplikace.  
  
 [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Obsahuje příklad kódu, který ukazuje, jak spustit formulářů Windows ve vlastním vlákně.  
  
 Viz také [názorný postup: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Použít k vytvoření samostatného vlákna pro formulář Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Spustí se smyčkou zpráv pro vlákno.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Zařadí volání z nespravovaného aplikace do formuláře.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.
