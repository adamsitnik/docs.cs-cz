---
title: Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegátů &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; se neshodují
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638208"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="e3c1e-102">Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegátů &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; se neshodují</span><span class="sxs-lookup"><span data-stu-id="e3c1e-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="e3c1e-103">Visual Basic nemůže implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3c1e-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="e3c1e-104">Této chybě může dojít při definování více událostí v rozhraní a pak pokus o jejich implementaci společně se stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="e3c1e-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="e3c1e-105">Událost můžete implementovat dvě nebo více událostí pouze v případě, že vše je implementováno události jsou deklarovány pomocí `As` syntaxe a zadejte stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="e3c1e-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="e3c1e-106">**ID chyby:** BC31423</span><span class="sxs-lookup"><span data-stu-id="e3c1e-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3c1e-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e3c1e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e3c1e-108">Implementace události samostatně.</span><span class="sxs-lookup"><span data-stu-id="e3c1e-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="e3c1e-109">—nebo—</span><span class="sxs-lookup"><span data-stu-id="e3c1e-109">—or—</span></span>  
  
-   <span data-ttu-id="e3c1e-110">Definování události pomocí rozhraní `As` syntaxe a zadejte stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="e3c1e-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c1e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3c1e-111">See also</span></span>
- [<span data-ttu-id="e3c1e-112">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="e3c1e-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="e3c1e-113">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="e3c1e-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="e3c1e-114">Události</span><span class="sxs-lookup"><span data-stu-id="e3c1e-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
