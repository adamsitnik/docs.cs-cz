---
title: Události a zpětná volání
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: KrzysztofCwalina
ms.openlocfilehash: 3609d6ac4847cb081740fd698869df4976f83f8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525479"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="d8a49-102">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="d8a49-102">Events and Callbacks</span></span>
<span data-ttu-id="d8a49-103">Zpětná volání nejsou body rozšiřitelnosti, které umožňují rozhraní pro zpětné volání do uživatelského kódu prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="d8a49-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="d8a49-104">Jsou tyto delegáty rozhraní Framework obvykle předat prostřednictvím parametru metody.</span><span class="sxs-lookup"><span data-stu-id="d8a49-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="d8a49-105">Události jsou zvláštním případem zpětná volání, která podporuje syntaxi pohodlný a konzistentní vzhledem k aplikacím pro poskytnutí delegáta (Obslužná rutina události).</span><span class="sxs-lookup"><span data-stu-id="d8a49-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="d8a49-106">Kromě toho dokončování příkazů sady Visual Studio a návrháři poskytnutí nápovědy v rozhraní API založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="d8a49-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="d8a49-107">(Viz [návrh události](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="d8a49-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="d8a49-108">**✓ CONSIDER** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d8a49-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="d8a49-109">**✓ CONSIDER** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.</span><span class="sxs-lookup"><span data-stu-id="d8a49-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="d8a49-110">**✓ DO** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8a49-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="d8a49-111">**X AVOID** pomocí zpětná volání rozhraní API náročné na výkon.</span><span class="sxs-lookup"><span data-stu-id="d8a49-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="d8a49-112">**✓ DO** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="d8a49-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="d8a49-113">`Func<...>` a `Action<...>` představují obecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="d8a49-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="d8a49-114">`Expression<...>` představuje definice funkcí, které mohou být zkompilovány a následně vyvolá za běhu, ale mohou také být serializován a předat vzdálených procesů.</span><span class="sxs-lookup"><span data-stu-id="d8a49-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="d8a49-115">**✓ DO** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.</span><span class="sxs-lookup"><span data-stu-id="d8a49-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="d8a49-116">`Expression<...>` typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegátů.</span><span class="sxs-lookup"><span data-stu-id="d8a49-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="d8a49-117">Hlavní rozdíl mezi nimi je, že delegáty jsou určena pro použití ve scénářích místní proces. výrazy jsou určené pro případech, kdy je výhodné a je to možné, k vyhodnocení výrazu v vzdálený proces nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="d8a49-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="d8a49-118">**✓ DO** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="d8a49-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="d8a49-119">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="d8a49-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d8a49-120">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="d8a49-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a49-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8a49-121">See also</span></span>

- [<span data-ttu-id="d8a49-122">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="d8a49-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="d8a49-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="d8a49-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
