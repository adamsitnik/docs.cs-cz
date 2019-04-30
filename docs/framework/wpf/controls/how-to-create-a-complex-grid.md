---
title: Vytvoření komplexní mřížky
description: Příklad, jak používat ovládací prvek mřížky vytvořit rozložení, který vypadá jako měsíční kalendář.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: dd17dfeea85e2b404f7a284f93faceec63145b1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910989"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="32261-103">Vytvoření komplexní mřížky</span><span class="sxs-lookup"><span data-stu-id="32261-103">How to create a complex Grid</span></span>

<span data-ttu-id="32261-104">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.Grid> ovládacího prvku k vytvoření rozložení, který vypadá jako měsíční kalendář.</span><span class="sxs-lookup"><span data-stu-id="32261-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="32261-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="32261-105">Example</span></span>

<span data-ttu-id="32261-106">Následující příklad definuje osm řádků a sloupců osm pomocí <xref:System.Windows.Controls.RowDefinition> a <xref:System.Windows.Controls.ColumnDefinition> třídy.</span><span class="sxs-lookup"><span data-stu-id="32261-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="32261-107">Používá <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> připojených vlastností, spolu s <xref:System.Windows.Shapes.Rectangle> elementy, které vyplnit pozadí různých sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="32261-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="32261-108">Tento návrh je možné, protože v každá buňka může existovat více než jeden prvek <xref:System.Windows.Controls.Grid>, hlavní rozdíl mezi <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="32261-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="32261-109">V příkladu je použit svislá přechody do <xref:System.Windows.Shapes.Shape.Fill%2A> sloupců a řádků ke zlepšení čitelnosti kalendáře a vizuální prezentace.</span><span class="sxs-lookup"><span data-stu-id="32261-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="32261-110">Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentují data a dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="32261-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="32261-111"><xref:System.Windows.Controls.TextBlock> prvky jsou absolutně umístěné v rámci jejich buňky pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti a vlastnosti zarovnání, které jsou definované ve stylu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="32261-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="32261-112">Následující obrázek ukazuje výsledný ovládací prvek, přizpůsobitelné kalendáře:</span><span class="sxs-lookup"><span data-stu-id="32261-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Snímek obrazovky výsledný ovládací prvek](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="32261-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32261-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="32261-115">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="32261-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="32261-116">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="32261-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="32261-117">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="32261-117">Table Overview</span></span>](../advanced/table-overview.md)