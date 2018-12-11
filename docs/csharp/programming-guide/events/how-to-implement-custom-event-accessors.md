---
title: 'Postupy: Implementace vlastních přístupových objektů událostí - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: aaf58307cb4e33a1caa7b1ef8584fbb33decea3f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240070"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="12318-102">Postupy: Implementace vlastních přístupových objektů událostí (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="12318-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="12318-103">Událost je zvláštní druh vícesměrového vysílání delegát, který lze vyvolat pouze z v rámci třídy, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="12318-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="12318-104">Klientský kód se přihlásí k odběru události zadáním odkazu na metodu, která má být volána, když se aktivuje událost.</span><span class="sxs-lookup"><span data-stu-id="12318-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="12318-105">Tyto metody se přidají do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají přistupující objekty vlastnosti, s tím rozdílem, že přístupové objekty událostí jsou pojmenovány `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="12318-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="12318-106">Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="12318-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="12318-107">Pokud ve vašem kódu jsou dodány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="12318-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="12318-108">Nicméně v některých případech budete muset poskytnout vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="12318-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="12318-109">Jeden takový případ je uveden v tématu [jak:  Implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="12318-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12318-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="12318-110">Example</span></span>  
 <span data-ttu-id="12318-111">Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="12318-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="12318-112">I když můžete nahradit všechny kód uvnitř přístupové objekty, doporučujeme uzamknout událostí, než přidáte nebo odeberete nové metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="12318-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="12318-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="12318-113">See Also</span></span>

- [<span data-ttu-id="12318-114">Události</span><span class="sxs-lookup"><span data-stu-id="12318-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="12318-115">event</span><span class="sxs-lookup"><span data-stu-id="12318-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)