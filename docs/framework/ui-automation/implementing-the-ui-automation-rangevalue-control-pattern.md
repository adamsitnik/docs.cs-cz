---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 00fb179cb95e764089b6427f41aefd0367fec836
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672250"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="d3e8b-102">Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e8b-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d3e8b-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d3e8b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d3e8b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d3e8b-105">Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>, včetně informací o události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="d3e8b-106">Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d3e8b-107"><xref:System.Windows.Automation.RangeValuePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které lze nastavit na hodnotu v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="d3e8b-108">Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d3e8b-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d3e8b-109">Pokyny pro implementaci a konvence</span><span class="sxs-lookup"><span data-stu-id="d3e8b-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d3e8b-110">Pokud implementace vzoru ovládacích prvků hodnota rozsahu, mějte na paměti následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="d3e8b-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d3e8b-111">Ovládací prvky umožňují překalibrování jejich podporovaných vlastností na základě národního prostředí nebo uživatelských předvoleb.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="d3e8b-112">Příkladem je teploměru – ovládací prvek, který lze nastavit pro zobrazení teploty ve stupních Fahrenheita nebo ve stupních Celsia.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="d3e8b-113">Ovládací prvky, které mají nejednoznačný rozsah hodnot, například indikátory průběhu nebo posuvníky, by měly být tyto hodnoty normalizovat.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="d3e8b-114">![Indikátor průběhu. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="d3e8b-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="d3e8b-115">Příklad indikátor průběhu, kde je hodnota typu celé číslo a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100</span><span class="sxs-lookup"><span data-stu-id="d3e8b-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="d3e8b-116">Požadované členy pro IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="d3e8b-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="d3e8b-117">Povinný člen</span><span class="sxs-lookup"><span data-stu-id="d3e8b-117">Required member</span></span>|<span data-ttu-id="d3e8b-118">Typ člena</span><span class="sxs-lookup"><span data-stu-id="d3e8b-118">Member type</span></span>|<span data-ttu-id="d3e8b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3e8b-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="d3e8b-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-120">Property</span></span>|<span data-ttu-id="d3e8b-121">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="d3e8b-122">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-122">Property</span></span>|<span data-ttu-id="d3e8b-123">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="d3e8b-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-124">Property</span></span>|<span data-ttu-id="d3e8b-125">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="d3e8b-126">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-126">Property</span></span>|<span data-ttu-id="d3e8b-127">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="d3e8b-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-128">Property</span></span>|<span data-ttu-id="d3e8b-129">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="d3e8b-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d3e8b-130">Property</span></span>|<span data-ttu-id="d3e8b-131">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="d3e8b-132">Metody</span><span class="sxs-lookup"><span data-stu-id="d3e8b-132">Methods</span></span>|<span data-ttu-id="d3e8b-133">Žádná</span><span class="sxs-lookup"><span data-stu-id="d3e8b-133">None</span></span>|  
  
 <span data-ttu-id="d3e8b-134">Tento model ovládací prvek nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d3e8b-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="d3e8b-135">Exceptions</span></span>  
 <span data-ttu-id="d3e8b-136">Poskytovatelé musí vyvolání následující výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d3e8b-137">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="d3e8b-137">Exception type</span></span>|<span data-ttu-id="d3e8b-138">Podmínka</span><span class="sxs-lookup"><span data-stu-id="d3e8b-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="d3e8b-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> je volána s hodnotou, která je větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="d3e8b-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3e8b-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3e8b-140">See also</span></span>
- [<span data-ttu-id="d3e8b-141">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e8b-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d3e8b-142">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e8b-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="d3e8b-143">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="d3e8b-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d3e8b-144">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e8b-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="d3e8b-145">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e8b-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
