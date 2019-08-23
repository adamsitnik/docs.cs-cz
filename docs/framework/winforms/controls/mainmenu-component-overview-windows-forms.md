---
title: MainMenu – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952138"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="c5a20-102">MainMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c5a20-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="c5a20-103">I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="c5a20-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c5a20-104">Komponenta model Windows Forms <xref:System.Windows.Forms.MainMenu> zobrazuje v době běhu nabídku.</span><span class="sxs-lookup"><span data-stu-id="c5a20-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="c5a20-105">Všechny podnabídky hlavní nabídky a jednotlivé položky jsou <xref:System.Windows.Forms.MenuItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="c5a20-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="c5a20-106">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="c5a20-106">Key Properties</span></span>  
 <span data-ttu-id="c5a20-107">Položka nabídky může být označena jako výchozí položka <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> nastavením vlastnosti na. `true`</span><span class="sxs-lookup"><span data-stu-id="c5a20-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="c5a20-108">Výchozí položka se při kliknutí na nabídku zobrazí tučným textem.</span><span class="sxs-lookup"><span data-stu-id="c5a20-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="c5a20-109"><xref:System.Windows.Forms.MenuItem.Checked%2A> Vlastnost položky nabídky je buď `true` nebo `false`, a označuje, zda je vybrána položka nabídky.</span><span class="sxs-lookup"><span data-stu-id="c5a20-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="c5a20-110"><xref:System.Windows.Forms.MenuItem.RadioCheck%2A> Vlastnost položky nabídky přizpůsobí vzhled vybrané položky: je-li <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> parametr nastaven na `true`hodnotu, zobrazí se vedle položky přepínač. Pokud <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `false`hodnotu, zobrazí se vedle položky značka zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="c5a20-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a20-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5a20-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="c5a20-112">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="c5a20-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
