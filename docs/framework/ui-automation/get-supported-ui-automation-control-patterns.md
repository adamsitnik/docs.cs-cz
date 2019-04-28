---
title: Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 64c5bae738cee5249e6c2406a2f94667ecb2931f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609903"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="4c022-102">Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c022-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="4c022-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4c022-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4c022-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4c022-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4c022-105">Toto téma ukazuje, jak načíst objekty vzor ovládacího prvku z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="4c022-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="4c022-106">Získat všechny vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4c022-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="4c022-107">Získejte <xref:System.Windows.Automation.AutomationElement> vzorů jehož ovládacích prvků, které mají zájem.</span><span class="sxs-lookup"><span data-stu-id="4c022-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="4c022-108">Volání <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> zobrazíte všechny vzorů ovládacích prvků z elementu.</span><span class="sxs-lookup"><span data-stu-id="4c022-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4c022-109">Důrazně doporučujeme, že klient nepoužívat <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c022-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="4c022-110">Výkon může vážně to jako tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="4c022-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="4c022-111">Pokud je to možné, by měl klient volat <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> klíče vzorců, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="4c022-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="4c022-112">Získat vzoru pro konkrétní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4c022-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="4c022-113">Získejte <xref:System.Windows.Automation.AutomationElement> vzorů jehož ovládacích prvků, které mají zájem.</span><span class="sxs-lookup"><span data-stu-id="4c022-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="4c022-114">Volání <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> dotazu určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="4c022-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="4c022-115">Tyto metody jsou podobné, ale pokud není nalezen vzor, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku, a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="4c022-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c022-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c022-116">Example</span></span>  
 <span data-ttu-id="4c022-117">Následující příklad načte <xref:System.Windows.Automation.AutomationElement> pro položky seznamu a získá <xref:System.Windows.Automation.SelectionItemPattern> z tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="4c022-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="4c022-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c022-118">See also</span></span>

- [<span data-ttu-id="4c022-119">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="4c022-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
