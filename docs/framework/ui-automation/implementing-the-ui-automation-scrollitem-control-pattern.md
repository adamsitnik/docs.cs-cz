---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: c0bb852fa6c117ae8eb2644a0be75f20367b2054
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095019"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="ef548-102">Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef548-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="ef548-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ef548-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ef548-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ef548-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ef548-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IScrollItemProvider>, včetně informací o vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="ef548-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="ef548-106">Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ef548-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="ef548-107"><xref:System.Windows.Automation.ScrollItemPattern> – Vzor ovládacích prvků slouží k podpoře jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="ef548-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="ef548-108">Tento ovládací prvek model funguje jako komunikační kanál mezi podřízeného ovládacího prvku a jeho kontejneru k zajištění, že kontejner můžete změnit aktuálně viditelný obsah (nebo oblastí) v rámci jeho zobrazení zobrazíte podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ef548-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="ef548-109">Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ef548-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ef548-110">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="ef548-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ef548-111">Pokud implementace vzoru ovládacích prvků posuvníku položky, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="ef548-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="ef548-112">Položky obsažené v okně nebo plátno ovládací prvek není nutné implementovat rozhraní IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="ef548-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="ef548-113">Jako alternativu, ale musí zveřejňovaly platné umístění <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="ef548-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="ef548-114">To vám umožní použití automatizace uživatelského rozhraní klientské aplikace <xref:System.Windows.Automation.ScrollPattern> řídit vzor metody na kontejner pro podřízené položky zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ef548-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="ef548-115">Požadované členy pro IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="ef548-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="ef548-116">Je vyžadována pro implementaci rozhraní IScrollProvider následující metoda.</span><span class="sxs-lookup"><span data-stu-id="ef548-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="ef548-117">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="ef548-117">Required members</span></span>|<span data-ttu-id="ef548-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="ef548-118">Member type</span></span>|<span data-ttu-id="ef548-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef548-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="ef548-120">– Metoda</span><span class="sxs-lookup"><span data-stu-id="ef548-120">-   Method</span></span>|<span data-ttu-id="ef548-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ef548-121">None</span></span>|  
  
 <span data-ttu-id="ef548-122">Tento model ovládací prvek nemá žádné přidružené vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="ef548-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ef548-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ef548-123">Exceptions</span></span>  
 <span data-ttu-id="ef548-124">Poskytovatelé musí vyvolání následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef548-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ef548-125">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="ef548-125">Exception Type</span></span>|<span data-ttu-id="ef548-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="ef548-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="ef548-127">Pokud položka nemůže být přesunut do oblasti zobrazení:</span><span class="sxs-lookup"><span data-stu-id="ef548-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="ef548-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef548-128">See also</span></span>

- [<span data-ttu-id="ef548-129">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef548-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ef548-130">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef548-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="ef548-131">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="ef548-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ef548-132">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef548-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="ef548-133">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef548-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
