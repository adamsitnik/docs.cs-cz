---
title: 'Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: b4efef869c96ddb4e58445e45ecad12b5658f9f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343342"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu
Tento názorný postup ukazují, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři. Můžete vybrat všechny typy ovládacích prvků WPF, které jsou zahrnuty ve vašem projektu.

 V tomto podrobném návodu můžete provádět následující úlohy:

-   Vytvoření projektu.

-   Vytvořte typy ovládacích prvků WPF.

-   Vyberte ovládací prvky WPF.

> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu Windows Forms.  
  
> [!NOTE]
>  Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Vytváření typů ovládacích prvků WPF  
 Po přidání typy ovládacích prvků WPF k projektu, můžete je hostujte v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků.  
  
#### <a name="to-create-wpf-control-types"></a>Chcete-li vytvořit typy ovládacích prvků WPF  
  
1. Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2. V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto. Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).  
  
3. V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.  
  
4. Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.  
  
5. Přidejte druhý WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl2.xaml`.  
  
6. V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.  
  
7. Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostovaný obsah 2**.  
  
 **Poznámka:** obecně byste neměli hostit složitější obsahu WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek se tady používá pouze pro ilustraci.  
  
1. Sestavte projekt.  
  
## <a name="selecting-wpf-controls"></a>Výběr ovládacích prvků WPF  
 Můžete přiřadit jiný obsah WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek, který je již hostování obsahu.  
  
#### <a name="to-select-wpf-controls"></a>Chcete-li vybrat ovládací prvky WPF  
  
1. Otevřít `Form1` v Návrháři formulářů Windows.  
  
2. V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3. Na panelu inteligentních značek `elementHost1`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.  
  
4. Vyberte **UserControl2** z rozevíracího seznamu.  
  
     `elementHost1` Ovládací prvek nyní hostitelem instance `UserControl2` typu.  
  
5. V **vlastnosti** okno, ujistěte se, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl2**.  
  
6. Z **nástrojů**v **interoperabilita WPF** skupiny tak, že přetáhnete <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek na formuláři.  
  
     Výchozí název pro nový ovládací prvek je `elementHost2`.  
  
7. Na panelu inteligentních značek `elementHost2`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.  
  
8. Vyberte **UserControl1** z rozevíracího seznamu.  
  
9. `elementHost2` Ovládací prvek nyní hostitelem instance `UserControl1` typu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
