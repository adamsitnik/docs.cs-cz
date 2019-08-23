---
title: Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 83e54da5fdb75e3da44009ec700102d6bd7ae5e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937970"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="2fb42-102">Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb42-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="2fb42-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2fb42-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2fb42-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2fb42-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2fb42-105">Toto téma ukazuje, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jak lze použít k vystavení objektů vložených do obsahu ovládacího prvku text.</span><span class="sxs-lookup"><span data-stu-id="2fb42-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb42-106">Vložené objekty mohou obsahovat obrázky, hypertextové odkazy, tlačítka, tabulky nebo ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="2fb42-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="2fb42-107">Vložené objekty jsou považovány za podřízené [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] objekty poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="2fb42-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="2fb42-108">To umožňuje zveřejnění prostřednictvím stejné struktury stromu pro automatizaci uživatelského rozhraní jako všechny ostatní [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky.</span><span class="sxs-lookup"><span data-stu-id="2fb42-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="2fb42-109">Funkce jsou zase zpřístupněny prostřednictvím vzorů ovládacích prvků, které jsou obvykle vyžadovány typem ovládacího prvku vložené objekty (například protože hypertextové odkazy jsou založené na textu, <xref:System.Windows.Automation.TextPattern>budou podporovat).</span><span class="sxs-lookup"><span data-stu-id="2fb42-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="2fb42-110">![Vložené objekty v textovém kontejneru.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="2fb42-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="2fb42-111">Ukázkový dokument s textovým obsahem ("Víte, že víte?" ...) a dva vložené objekty (obrázek Whale a textový hypertextový odkaz) používané jako cíl pro příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="2fb42-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fb42-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fb42-112">Example</span></span>  
 <span data-ttu-id="2fb42-113">Následující příklad kódu ukazuje, jak načíst kolekci vložených objektů v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="2fb42-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="2fb42-114">Pro ukázkový dokument poskytnutý v úvodu by se vracely dva objekty (element obrázku a textový element).</span><span class="sxs-lookup"><span data-stu-id="2fb42-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb42-115">K elementu Image by měl být přidružen nějaký vnitřní text, který popisuje obrázek, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "modrý Whale").</span><span class="sxs-lookup"><span data-stu-id="2fb42-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="2fb42-116">Pokud se ale Získá rozsah textu, který pokrývá objekt obrázku, nevrátí se do textového streamu ani obrázek ani tento popisný text.</span><span class="sxs-lookup"><span data-stu-id="2fb42-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="2fb42-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fb42-117">Example</span></span>  
 <span data-ttu-id="2fb42-118">Následující příklad kódu ukazuje, jak získat textovou oblast z vloženého objektu v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu.</span><span class="sxs-lookup"><span data-stu-id="2fb42-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="2fb42-119">Načtený rozsah textu je prázdný rozsah, ve kterém následuje počáteční koncový bod...</span><span class="sxs-lookup"><span data-stu-id="2fb42-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="2fb42-120">spadající. (Space) "a koncový bod předchází konci". "představující vložený hypertextový odkaz (jak znázorňuje obrázek uvedený v úvodu).</span><span class="sxs-lookup"><span data-stu-id="2fb42-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="2fb42-121">I když se jedná o prázdný rozsah, není považován za negenerovaný rozsah, protože má nenulové rozpětí.</span><span class="sxs-lookup"><span data-stu-id="2fb42-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb42-122"><xref:System.Windows.Automation.TextPattern>může načíst textový vložený objekt, jako je hypertextový odkaz. sekundární <xref:System.Windows.Automation.TextPattern> objekt se však bude muset získat z vloženého objektu, aby bylo možné zobrazit jeho plnou funkčnost.</span><span class="sxs-lookup"><span data-stu-id="2fb42-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="2fb42-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fb42-123">See also</span></span>

- [<span data-ttu-id="2fb42-124">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb42-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="2fb42-125">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb42-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2fb42-126">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="2fb42-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2fb42-127">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb42-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="2fb42-128">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fb42-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
