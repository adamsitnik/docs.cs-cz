---
title: 'Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: baa6f79f2e0d454412992d9c951734a3437a96cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517640"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="1d14c-102">Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1d14c-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1d14c-103">Ve výchozím nastavení, popisy slouží k zobrazení hodnoty <xref:System.Windows.Forms.DataGridView> buňky, které jsou příliš malé a zobrazit jejich celý obsah.</span><span class="sxs-lookup"><span data-stu-id="1d14c-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="1d14c-104">Toto chování můžete přepsat však můžete nastavit text popisku hodnoty jednotlivých buněk.</span><span class="sxs-lookup"><span data-stu-id="1d14c-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="1d14c-105">To je užitečné, chcete-li zobrazit uživatelům další informace o buňku nebo můžete uživatelům poskytnout alternativní popis obsah buňky.</span><span class="sxs-lookup"><span data-stu-id="1d14c-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="1d14c-106">Například pokud máte řádek, který zobrazuje ikony stavu, můžete zadat text vysvětlení použití popisů tlačítek.</span><span class="sxs-lookup"><span data-stu-id="1d14c-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="1d14c-107">Zobrazit popisky na úrovni buněk můžete také zakázat nastavením <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="1d14c-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="1d14c-108">Chcete-li přidat popisek buňky</span><span class="sxs-lookup"><span data-stu-id="1d14c-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="1d14c-109">Nastavte <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d14c-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d14c-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1d14c-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1d14c-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1d14c-111">This example requires:</span></span>  
  
-   <span data-ttu-id="1d14c-112">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `Rating` pro zobrazení hodnoty řetězců jeden až čtyři hvězdičky ("\*") symboly.</span><span class="sxs-lookup"><span data-stu-id="1d14c-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="1d14c-113"><xref:System.Windows.Forms.DataGridView.CellFormatting> Události ovládacího prvku musí být přidružená k metodě obslužné rutiny události v příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d14c-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="1d14c-114">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="1d14c-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d14c-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1d14c-115">Robust Programming</span></span>  
 <span data-ttu-id="1d14c-116">Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení k externímu zdroji dat nebo poskytnutí zdroje dat tak, že implementace virtuálního režimu, může dojít problémům s výkonem.</span><span class="sxs-lookup"><span data-stu-id="1d14c-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="1d14c-117">Aby se zabránilo snížení výkonu při práci s velkými objemy dat, zpracovat <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> události spíše než nastavení <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost více buněk.</span><span class="sxs-lookup"><span data-stu-id="1d14c-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="1d14c-118">Při zpracování této události, získání vyšší hodnoty buňky <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost vyvolá událost a vrátí hodnotu <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> vlastnost jako uvedené v události obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1d14c-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d14c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d14c-119">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1d14c-120">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1d14c-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
