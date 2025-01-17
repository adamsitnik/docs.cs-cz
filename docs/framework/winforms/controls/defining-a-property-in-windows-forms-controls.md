---
title: Definování vlastnosti v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: a641b1e7565842a1edf6aeec88bdc37ee0786ab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969120"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definování vlastnosti v ovládacích prvcích Windows Forms
Přehled vlastností najdete v tématu [Přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Při definování vlastnosti je potřeba několik důležitých otázek:  
  
- Je nutné použít atributy pro vlastnosti, které definujete. Atributy určují, jak má Návrhář zobrazit vlastnost. Podrobnosti najdete v tématu [atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Pokud změna vlastnosti ovlivňuje vizuální zobrazení ovládacího prvku, zavolejte <xref:System.Windows.Forms.Control.Invalidate%2A> metodu (kterou ovládací prvek dědí z <xref:System.Windows.Forms.Control>) z `set` přístupového objektu. <xref:System.Windows.Forms.Control.Invalidate%2A>zase volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která překreslí ovládací prvek. Vícenásobné volání <xref:System.Windows.Forms.Control.Invalidate%2A> , které má za následek jedno <xref:System.Windows.Forms.Control.OnPaint%2A> volání kvůli efektivitě.  
  
- Knihovna tříd .NET Framework poskytuje převaděče typů pro běžné datové typy, jako jsou celá čísla, desetinná čísla, logické hodnoty a další. Účelem převaděče typu je obecně poskytnout převod řetězce na hodnotu (z řetězcových dat na jiné datové typy). Společné datové typy jsou přidruženy k výchozím převaděčům typů, které převádějí hodnoty na řetězce a řetězce na příslušné datové typy. Definujete-li vlastnost, která je vlastní (tj. nestandardní) datový typ, bude nutné použít atribut, který určuje konvertor typu k přidružení k této vlastnosti. Můžete také použít atribut k přidružení vlastního editoru typů uživatelského rozhraní k vlastnosti. Editor typu uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu vlastnosti nebo datového typu. Výběr barvy je příkladem editoru typů uživatelského rozhraní. Příklady atributů jsou uvedené na konci tohoto tématu.  
  
    > [!NOTE]
    > Pokud není pro vlastní vlastnost převaděč typu nebo Editor typů uživatelského rozhraní k dispozici, můžete implementovat jeden, jak je popsáno v tématu [rozšíření podpory při návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Následující fragment kódu definuje vlastní vlastnost pojmenovanou `EndColor` pro vlastní ovládací prvek. `FlashTrackBar`  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Následující fragment kódu přidruží konvertor typu a Editor typů uživatelského rozhraní s vlastností `Value`. V tomto případě `Value` je celé číslo a má výchozí konvertor typu, <xref:System.ComponentModel.TypeConverterAttribute> ale atribut používá vlastní konvertor typu (`FlashTrackBarValueConverter`), který umožňuje návrháři zobrazit ho jako procento. Editor `FlashTrackBarValueEditor`typu uživatelského rozhraní umožňuje zobrazit zobrazené procento vizuálně. Tento příklad také ukazuje, že převaděč typu nebo editor určený <xref:System.ComponentModel.TypeConverterAttribute> atributem nebo <xref:System.ComponentModel.EditorAttribute> přepisuje výchozí převaděč.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Události změny vlastnosti](property-changed-events.md)
- [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)
