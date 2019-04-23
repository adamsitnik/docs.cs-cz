---
title: Hledání prvku automatizace uživatelského rozhraní pro položku seznamu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 7fe1f564e8c9fb967c0b7b4e8b12712962bdedc7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179657"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="556e6-102">Hledání prvku automatizace uživatelského rozhraní pro položku seznamu</span><span class="sxs-lookup"><span data-stu-id="556e6-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="556e6-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="556e6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="556e6-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="556e6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="556e6-105">Toto téma ukazuje, jak načíst <xref:System.Windows.Automation.AutomationElement> pro některou položku v seznamu, pokud je známý index položky.</span><span class="sxs-lookup"><span data-stu-id="556e6-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="556e6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="556e6-106">Example</span></span>  
 <span data-ttu-id="556e6-107">Následující příklad ukazuje dva způsoby načítání zadané položky seznamu, pomocí <xref:System.Windows.Automation.TreeWalker> a dalších použití <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="556e6-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="556e6-108">První způsob je spíše pro rychlejší [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků, ale druhá je rychlejší ovládacích prvků Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="556e6-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="556e6-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="556e6-109">See also</span></span>

- [<span data-ttu-id="556e6-110">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="556e6-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
