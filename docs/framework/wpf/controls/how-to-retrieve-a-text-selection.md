---
title: 'Postupy: Načtení výběru textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 3e2a4d9938f73cb306e8fd8b0e6b25b5abfa3b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517770"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="14783-102">Postupy: Načtení výběru textu</span><span class="sxs-lookup"><span data-stu-id="14783-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="14783-103">Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.TextBox.SelectedText%2A> vlastnost pro načtení textu, který uživatel vybral v <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14783-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14783-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="14783-104">Example</span></span>  
 <span data-ttu-id="14783-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje definici <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje text, který chcete vybrat, a <xref:System.Windows.Controls.Button> ovládací prvek se zadaným <xref:System.Windows.Controls.Button.OnClick%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="14783-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="14783-106">V tomto příkladu tlačítko s přidruženou <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události se používá k načtení výběru textu.</span><span class="sxs-lookup"><span data-stu-id="14783-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="14783-107">Když uživatel klikne na tlačítko <xref:System.Windows.Controls.Button.OnClick%2A> metoda zkopíruje vybraný text do textového pole na řetězec.</span><span class="sxs-lookup"><span data-stu-id="14783-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="14783-108">Zvláštní okolnosti, které výběr textu je načten (kliknutí na tlačítko), stejně jako akci prováděnou s výběr (text výběr se kopíruje do řetězce), lze snadno upravit tak, aby vyhovovaly širokou škálu scénářů.</span><span class="sxs-lookup"><span data-stu-id="14783-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="14783-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="14783-109">Example</span></span>  
 <span data-ttu-id="14783-110">Následující C# ukazuje příklad <xref:System.Windows.Controls.Button.OnClick%2A> obslužné rutiny události pro tlačítko definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="14783-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="14783-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14783-111">See also</span></span>
- [<span data-ttu-id="14783-112">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="14783-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="14783-113">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="14783-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
