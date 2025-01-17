---
title: 'Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: 748ab027fa8206c163578c89b94460665563cbce
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197864"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms

Tento návod ukazuje, jak lze vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek a hostovat ho v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvcích a formulářích pomocí ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.

V tomto návodu implementujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>, které obsahují dva podřízené ovládací prvky. <xref:System.Windows.Controls.UserControl> zobrazí trojrozměrné (3D) kužel. Vykreslování 3D objektů je mnohem snazší s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto má smysl hostovat třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> a vytvořit v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]3D grafiku.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváření <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- Vytváří se projekt hostitele model Windows Forms.

- Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Vytvoření prvku UserControl

1. Vytvořte projekt **knihovny uživatelských ovládacích prvků WPF** s názvem `HostingWpfUserControlInWf`.

2. Otevřete UserControl1. XAML v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Vygenerovaný kód nahraďte následujícím kódem:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, která obsahuje dva podřízené ovládací prvky. Prvním podřízeným ovládacím prvkem je ovládací prvek <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; druhým je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazuje prostorový kuželový.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Vytvořit hostitelský projekt

1. Přidejte do řešení projekt **aplikace model Windows Forms (.NET Framework)** s názvem `WpfUserControlHost`.

2. V **Průzkumník řešení**přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.

3. Přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. Přidejte odkaz na `HostingWpfUserControlInWf` projekt.

5. V Průzkumník řešení nastavte projekt `WpfUserControlHost` na spouštěný projekt.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Hostování prvku UserControl

1. V Návrhář formulářů otevřete Form1.

2. V okno Vlastnosti klikněte na položku **události**a potom poklikejte na událost <xref:System.Windows.Forms.Form.Load> a vytvořte obslužnou rutinu události.

     Editor kódu se otevře v nově vygenerované obslužné rutině `Form1_Load` události.

3. Nahraďte kód v Form1.cs následujícím kódem.

     Obslužná rutina události `Form1_Load` vytvoří instanci `UserControl1` a přidá tovární kolekci podřízených ovládacích prvků <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hostování složeného ovládacího prvku WPF v model Windows Forms Sample](https://go.microsoft.com/fwlink/?LinkID=160001)
