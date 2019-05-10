---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 81be2c07f9fd3cc449527c389b0e6bf46182c382
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659845"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="ba4e2-102">Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="ba4e2-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ba4e2-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ba4e2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ba4e2-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>, včetně informací o vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="ba4e2-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="ba4e2-107"><xref:System.Windows.Automation.GridItemPattern> – Vzor ovládacích prvků slouží k podpoře jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="ba4e2-108">Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ba4e2-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ba4e2-109">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="ba4e2-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ba4e2-110">Při implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="ba4e2-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="ba4e2-111">Souřadnice mřížky jsou počítány od nuly s levá horní buňka s souřadnice (0, 0).</span><span class="sxs-lookup"><span data-stu-id="ba4e2-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="ba4e2-112">Sloučené buňky budou hlásit jejich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> a <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti na základě jejich základní ukotvení buňky definované ve zprostředkovateli automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="ba4e2-113">Obvykle bude nejvyšší a levém řádku nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="ba4e2-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> neposkytuje aktivní manipulaci s například slučování nebo rozdělení buňky v mřížce.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="ba4e2-115">Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IGridItemProvider> lze obvykle Procházet (automatizace uživatelského rozhraní klienta můžete přesunout na sousední ovládací prvky) pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="ba4e2-116">Požadované členy pro IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="ba4e2-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="ba4e2-117">Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="ba4e2-118">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="ba4e2-118">Required members</span></span>|<span data-ttu-id="ba4e2-119">Typ člena</span><span class="sxs-lookup"><span data-stu-id="ba4e2-119">Member type</span></span>|<span data-ttu-id="ba4e2-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba4e2-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="ba4e2-121">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba4e2-121">Property</span></span>|<span data-ttu-id="ba4e2-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="ba4e2-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="ba4e2-123">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba4e2-123">Property</span></span>|<span data-ttu-id="ba4e2-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="ba4e2-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="ba4e2-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba4e2-125">Property</span></span>|<span data-ttu-id="ba4e2-126">Žádný</span><span class="sxs-lookup"><span data-stu-id="ba4e2-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="ba4e2-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba4e2-127">Property</span></span>|<span data-ttu-id="ba4e2-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="ba4e2-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="ba4e2-129">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba4e2-129">Property</span></span>|<span data-ttu-id="ba4e2-130">Žádný</span><span class="sxs-lookup"><span data-stu-id="ba4e2-130">None</span></span>|  
  
 <span data-ttu-id="ba4e2-131">Tento model ovládací prvek nemá žádné přidružené metody a události.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ba4e2-132">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ba4e2-132">Exceptions</span></span>  
 <span data-ttu-id="ba4e2-133">Tento model ovládací prvek nemá žádné související výjimky.</span><span class="sxs-lookup"><span data-stu-id="ba4e2-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4e2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba4e2-134">See also</span></span>

- [<span data-ttu-id="ba4e2-135">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ba4e2-136">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="ba4e2-137">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="ba4e2-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ba4e2-138">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="ba4e2-139">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="ba4e2-140">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba4e2-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
