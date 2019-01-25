---
title: 'Průvodce: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 7e5984edfc081427214220eadf190282846b1c44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640716"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Průvodce: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí mnoho ovládacích prvků s bohatou sadou funkcí. Však můžete někdy chtít použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky ve vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. Například můžete mít značné investice v existujícím [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo můžete mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.  
  
 Tento návod ukazuje, jak hostovat prvku Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládání na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML vzorek](https://go.microsoft.com/fwlink/?LinkID=160000).  
  
## <a name="prerequisites"></a>Požadavky  

Visual Studio k dokončení tohoto návodu potřebujete.  
  
## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>K hostování ovládacím prvkem MaskedTextBox  
  
1.  Vytvoření projektu aplikace WPF s názvem `HostingWfInWpfWithXaml`.  
  
2.  Přidáte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  V <xref:System.Windows.Window> prvku, přidejte následující mapování oboru názvů. `wf` Mapování oboru názvů vytvoří odkaz na sestavení, která obsahuje ovládací prvek Windows Forms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  V <xref:System.Windows.Controls.Grid> prvek přidejte následující XAML.  
  
     <xref:System.Windows.Forms.MaskedTextBox> Ovládací prvek je vytvořen jako podřízený objekt <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí ukázky XAML](https://go.microsoft.com/fwlink/?LinkID=160000)
