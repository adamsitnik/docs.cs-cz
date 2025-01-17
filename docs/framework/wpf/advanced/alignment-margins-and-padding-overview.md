---
title: Přehled zarovnání, okrajů a odsazení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963640"
---
# <a name="alignment-margins-and-padding-overview"></a>Přehled zarovnání, okrajů a odsazení
<xref:System.Windows.FrameworkElement> Třída zveřejňuje několik vlastností, které se používají k přesnému umístění podřízených elementů. Toto téma popisuje čtyři <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>z nejdůležitějších vlastností:, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>a. Účinky těchto vlastností jsou důležité pochopit, protože poskytují základ pro řízení pozice prvků v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích.  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Úvod do umístění elementu  
 Existuje mnoho způsobů, jak umístit prvky pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nicméně dosažení ideálního rozložení překračuje pouhou volbu správného <xref:System.Windows.Controls.Panel> prvku. Přesné řízení <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>umístění vyžaduje porozumění vlastnostem, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
 Následující ilustrace znázorňuje scénář rozložení, který využívá několik vlastností umístění.  
  
 ![Ukázka vlastnosti umístění WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na první pohled se může zdát <xref:System.Windows.Controls.Button> , že prvky na tomto obrázku jsou náhodně umístěné. Nicméně jejich pozice jsou ve skutečnosti přesně ovládány pomocí kombinace okrajů, zarovnání a odsazení.  
  
 Následující příklad popisuje, jak vytvořit rozložení na předchozí ilustraci. Element zapouzdřuje nadřazenou <xref:System.Windows.Controls.StackPanel>položku s hodnotou <xref:System.Windows.Controls.Border.Padding%2A> 15 pixelů nezávislých na zařízení. <xref:System.Windows.Controls.Border> Tyto účty pro úzký <xref:System.Windows.Media.Brushes.LightBlue%2A> pruh, které obklopují podřízenou položku. <xref:System.Windows.Controls.StackPanel> Podřízené prvky <xref:System.Windows.Controls.StackPanel> jsou použity k ilustraci každé z různých vlastností umístění, které jsou popsány v tomto tématu. Tři <xref:System.Windows.Controls.Button> prvky jsou použity k demonstraci <xref:System.Windows.FrameworkElement.Margin%2A> vlastností <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Následující diagram poskytuje podrobné zobrazení různých vlastností umístění, které jsou použity v předchozí ukázce. Následující části tohoto tématu popisují podrobněji, jak použít jednotlivé vlastnosti umístění.  
  
 ![Umístění vlastností s voláními&#45;obrazovky](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Porozumění vlastnostem zarovnání  
 Vlastnosti <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> popisují, jak by měl být podřízený element umístěn v rámci přiděleného prostoru rozložení nadřazeného elementu. Použitím těchto vlastností společně můžete umístit podřízené prvky přesně. Například podřízené <xref:System.Windows.Controls.DockPanel> prvky prvku mohou určovat čtyři různá vodorovná zarovnání: <xref:System.Windows.HorizontalAlignment.Right> <xref:System.Windows.HorizontalAlignment.Left>, nebo <xref:System.Windows.HorizontalAlignment.Center>, nebo k <xref:System.Windows.HorizontalAlignment.Stretch> vyplnění dostupného místa. Podobné hodnoty jsou k dispozici pro vertikální umístění.  
  
> [!NOTE]
> Explicitně nastavené <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti <xref:System.Windows.HorizontalAlignment.Stretch> prvku mají přednost před hodnotou vlastnosti. Při pokusu o <xref:System.Windows.FrameworkElement.Height%2A>nastavení <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota `Stretch` výsledků v `Stretch` požadavku se ignoruje.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Vlastnost HorizontalAlignment  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Vlastnost deklaruje vlastnosti vodorovného zarovnání pro použití u podřízených elementů. V následující tabulce jsou uvedeny všechny možné hodnoty <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Podřízené elementy jsou zarovnány nalevo od přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Podřízené elementy jsou zarovnány do středu přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Podřízené elementy jsou zarovnány napravo od přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>Výchozí|Podřízené prvky jsou roztaženy tak, aby vyplnily přidělené místo rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a<xref:System.Windows.FrameworkElement.Height%2A> hodnoty mají přednost.|  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost na <xref:System.Windows.Controls.Button> prvky. Pro lepší ilustraci různých chování vykreslování se zobrazí každá hodnota atributu.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Předchozí kód poskytuje rozložení podobné následujícímu obrázku. Na ilustraci jsou viditelné <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> efekty umístění jednotlivých hodnot.  
  
 ![Ukázka HorizontalAlignment](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Vlastnost VerticalAlignment  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Vlastnost popisuje vlastnosti svislého zarovnání pro použití u podřízených elementů. V následující tabulce jsou uvedeny všechny možné hodnoty pro <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Podřízené elementy jsou zarovnány k hornímu okraji přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Center>|Podřízené elementy jsou zarovnány do středu přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Podřízené elementy jsou zarovnány k dolnímu okraji přiděleného prostoru rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Stretch>Výchozí|Podřízené prvky jsou roztaženy tak, aby vyplnily přidělené místo rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a<xref:System.Windows.FrameworkElement.Height%2A> hodnoty mají přednost.|  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost na <xref:System.Windows.Controls.Button> prvky. Pro lepší ilustraci různých chování vykreslování se zobrazí každá hodnota atributu. Pro účely této ukázky <xref:System.Windows.Controls.Grid> se jako nadřazený objekt používá element s viditelnými mřížkami, aby lépe ilustroval chování rozložení každé hodnoty vlastnosti.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Předchozí kód poskytuje rozložení podobné následujícímu obrázku. Na ilustraci jsou viditelné <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> efekty umístění jednotlivých hodnot.  
  
 ![Ukázka vlastnosti VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Porozumění vlastnostem okraje  
 <xref:System.Windows.FrameworkElement.Margin%2A> Vlastnost popisuje vzdálenost mezi prvkem a jeho podřízenými objekty nebo partnery. <xref:System.Windows.FrameworkElement.Margin%2A>hodnoty mohou být uniformně použity syntaxí, `Margin="20"`jako je. V této syntaxi by se pro <xref:System.Windows.FrameworkElement.Margin%2A> element použilo jednotné pixely nezávislé na zařízení. <xref:System.Windows.FrameworkElement.Margin%2A>hodnoty mohou také mít formu čtyř jedinečných hodnot. Každá hodnota, která popisuje samostatný okraj, má být použita vlevo, nahoře, vpravo a dole (v tomto pořadí), například `Margin="0,10,5,25"`. Správné použití <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti umožňuje velmi přesné řízení pozice vykreslování elementu a umístění vykreslování jeho sousedních prvků a podřízených objektů.  
  
> [!NOTE]
> Nenulový okraj aplikuje mezeru mimo element <xref:System.Windows.FrameworkElement.ActualWidth%2A> a. <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
  
 Následující příklad ukazuje, jak použít jednotné okraje kolem skupiny <xref:System.Windows.Controls.Button> prvků. <xref:System.Windows.Controls.Button> Prvky jsou rovnoměrně rozmístěny s mezipamětí okraje 10 pixelů v každém směru.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 V mnoha případech není jednotné okraje vhodné. V těchto případech lze použít nestejnoměrné mezery. Následující příklad ukazuje, jak použít nerovnoměrné mezery mezi podřízenými prvky. Okraje jsou popsány v tomto pořadí: levý, horní, pravý, dolní.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Princip vlastnosti odsazení  
 Odsazení je podobné <xref:System.Windows.FrameworkElement.Margin%2A> jako v nejvíc ohledech. Vlastnost odsazení <xref:System.Windows.Documents.Block>je vystavena pouze na několika třídách, primárně jako pohodlí: <xref:System.Windows.Controls.Control>, <xref:System.Windows.Controls.Border>, a <xref:System.Windows.Controls.TextBlock> jsou vzorky tříd, které zpřístupňují vlastnost odsazení. Vlastnost zvětší efektivní velikost podřízeného prvku zadanou <xref:System.Windows.Thickness> hodnotou. <xref:System.Windows.Controls.Border.Padding%2A>  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.Border.Padding%2A> na nadřazený <xref:System.Windows.Controls.Border> element.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Použití zarovnání, okrajů a odsazení v aplikaci  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]a Poskytněteovládacíprvekumístěnípotřebnýkvytvořenísložitého<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> . Můžete použít důsledky jednotlivých vlastností a změnit umístění podřízených elementů a umožnit tak flexibilitu při vytváření dynamických aplikací a uživatelského prostředí.  
  
 Následující příklad znázorňuje každou z konceptů, které jsou podrobně popsané v tomto tématu. V tomto tématu se sestavuje infrastruktura, která se nachází v první ukázce v tomto <xref:System.Windows.Controls.Grid> tématu. Tento příklad přidá prvek <xref:System.Windows.Controls.Border> jako podřízenou položku v první ukázce. <xref:System.Windows.Controls.Border.Padding%2A>je použito pro nadřazený <xref:System.Windows.Controls.Border> element. Slouží k rozdělení prostoru mezi tři podřízené <xref:System.Windows.Controls.StackPanel> prvky. <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Button>prvky jsou znovu použity k zobrazení různých efektů <xref:System.Windows.FrameworkElement.Margin%2A> a. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.TextBlock>prvky jsou přidány do každého <xref:System.Windows.Controls.ColumnDefinition> pro lepší definování různých vlastností použitých <xref:System.Windows.Controls.Button> na prvky v jednotlivých sloupcích.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Při kompilaci předchozí aplikace navede objekt [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který bude vypadat jako na následujícím obrázku. Účinky různých hodnot vlastností jsou zjevné v odstupech mezi prvky a významné hodnoty vlastností prvků v jednotlivých sloupcích jsou zobrazeny v rámci <xref:System.Windows.Controls.TextBlock> prvků.  
  
 ![Několik vlastností umístění v jedné aplikaci](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Co dál  
 Umístění vlastností definovaných <xref:System.Windows.FrameworkElement> třídou umožňuje přesné řízení umístění elementu v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací. Nyní máte několik postupů, které můžete použít k lepšímu umístění prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pomocí.  
  
 K dispozici jsou další prostředky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které vysvětlují rozložení podrobněji. Téma [Přehled panelů](../controls/panels-overview.md) obsahuje další podrobnosti o různých <xref:System.Windows.Controls.Panel> prvcích. Téma [Návod: Moje první desktopová aplikace](../getting-started/walkthrough-my-first-wpf-desktop-application.md) WPF zavádí pokročilé techniky, které používají prvky rozložení k umístění komponent a vázání jejich akcí na zdroje dat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Přehled panelu](../controls/panels-overview.md)
- [Rozložení](layout.md)
- [Ukázka Galerie rozložení WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
