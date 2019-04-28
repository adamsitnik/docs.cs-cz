---
title: Zapečetění
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: c8aeb5ce3d93755f30bf68732592a08d7af54957
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762056"
---
# <a name="sealing"></a><span data-ttu-id="9f089-102">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="9f089-102">Sealing</span></span>
<span data-ttu-id="9f089-103">Jednou z funkcí objektově orientované rozhraní je, že vývojáři můžete rozšířit a přizpůsobit způsoby neočekávané návrháři rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="9f089-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="9f089-104">Toto je výkon a nebezpečí extensible návrhu.</span><span class="sxs-lookup"><span data-stu-id="9f089-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="9f089-105">Při navrhování rozhraní framework je, proto velmi důležité, pečlivě navrhování pro rozšiřitelnost ho potřebujete a omezit rozšiřitelnosti, když je nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="9f089-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="9f089-106">Zapečetění je výkonný mechanismus, který brání rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="9f089-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="9f089-107">Můžete zapečeťte třídu nebo jednotlivé členy.</span><span class="sxs-lookup"><span data-stu-id="9f089-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="9f089-108">Zapečetění třídu zabraňuje uživatelům dědění ze třídy.</span><span class="sxs-lookup"><span data-stu-id="9f089-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="9f089-109">Zapečetění člen zabraňuje uživatelům v přepsání určitého člena.</span><span class="sxs-lookup"><span data-stu-id="9f089-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="9f089-110">**X DO NOT** zapečetit třídy bez nutnosti důvodem k tomu.</span><span class="sxs-lookup"><span data-stu-id="9f089-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="9f089-111">Zapečetění třídu, protože nelze myslíte, že rozšíření scénáře není dobrý důvod.</span><span class="sxs-lookup"><span data-stu-id="9f089-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="9f089-112">Dědit ze tříd z různých důvodů nonobvious, jako je přidání členů pohodlí, jako jsou uživatelé rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="9f089-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="9f089-113">Zobrazit [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md) příklady nonobvious důvodů uživatelé chtějí dědit z typu.</span><span class="sxs-lookup"><span data-stu-id="9f089-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="9f089-114">Oprávněné důvody pro zapečetění třídy zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="9f089-114">Good reasons for sealing a class include the following:</span></span>  
  
- <span data-ttu-id="9f089-115">Třída je statická třída.</span><span class="sxs-lookup"><span data-stu-id="9f089-115">The class is a static class.</span></span> <span data-ttu-id="9f089-116">Zobrazit [návrh statické třídy](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="9f089-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
- <span data-ttu-id="9f089-117">Třídy ukládá citlivé na zabezpečení tajné kódy ve zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="9f089-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
- <span data-ttu-id="9f089-118">Třída dědí mnoho virtuální členy a náklady na jejich jednotlivě zapečetění by převážit nad výhodami opuštění nezapečetěné třídy.</span><span class="sxs-lookup"><span data-stu-id="9f089-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
- <span data-ttu-id="9f089-119">Třída je atribut, který vyžaduje velmi rychlé zpracování runtime vyhledat.</span><span class="sxs-lookup"><span data-stu-id="9f089-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="9f089-120">Zapečetěné atributy mají mírně vyšší úrovně výkonu než nezapečetěné.</span><span class="sxs-lookup"><span data-stu-id="9f089-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="9f089-121">Zobrazit [atributy](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9f089-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="9f089-122">**X DO NOT** deklarovat chráněný nebo virtuální členy v zapečetěných typech.</span><span class="sxs-lookup"><span data-stu-id="9f089-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="9f089-123">Dle definice nelze dědit zapečetěné typy z.</span><span class="sxs-lookup"><span data-stu-id="9f089-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="9f089-124">To znamená, že nelze volat chráněné členy v zapečetěných typech a nedají se přepsat virtuální metody zapečetěných typů.</span><span class="sxs-lookup"><span data-stu-id="9f089-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="9f089-125">**✓ CONSIDER** zapečetění členů, které můžete přepsat.</span><span class="sxs-lookup"><span data-stu-id="9f089-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="9f089-126">Problémy, které můžou být výsledkem Představujeme virtuální členy (popsáno v [virtuální členy](../../../docs/standard/design-guidelines/virtual-members.md)) použít k přepsání, i když se do menší míry.</span><span class="sxs-lookup"><span data-stu-id="9f089-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="9f089-127">Zapečetění přepsání chrání před tyto problémy od tohoto bodu v hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="9f089-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="9f089-128">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9f089-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9f089-129">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="9f089-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f089-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f089-130">See also</span></span>

- [<span data-ttu-id="9f089-131">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9f089-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="9f089-132">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="9f089-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="9f089-133">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="9f089-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
