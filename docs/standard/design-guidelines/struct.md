---
title: Návrh struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: cc5b8d7effda31b0236477b217bccf5cf2137f8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646604"
---
# <a name="struct-design"></a><span data-ttu-id="744ec-102">Návrh struktury</span><span class="sxs-lookup"><span data-stu-id="744ec-102">Struct Design</span></span>
<span data-ttu-id="744ec-103">Typ hodnoty pro obecné účely se nejčastěji označuje jako struktury, jeho klíčové slovo C#.</span><span class="sxs-lookup"><span data-stu-id="744ec-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="744ec-104">Tato část obsahuje pokyny pro návrh obecné struktury.</span><span class="sxs-lookup"><span data-stu-id="744ec-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="744ec-105">**X DO NOT** zadejte výchozí konstruktor pro struktury.</span><span class="sxs-lookup"><span data-stu-id="744ec-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="744ec-106">Za toto pravidlo umožňuje pole struktur, který se má vytvořit bez nutnosti spuštění konstruktoru pro každou položku pole.</span><span class="sxs-lookup"><span data-stu-id="744ec-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="744ec-107">Všimněte si, že C# nepovoluje struktury mají výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="744ec-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="744ec-108">**X DO NOT** definování typů měnitelný hodnotu.</span><span class="sxs-lookup"><span data-stu-id="744ec-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="744ec-109">Proměnlivé hodnoty typy mají několik problémů.</span><span class="sxs-lookup"><span data-stu-id="744ec-109">Mutable value types have several problems.</span></span> <span data-ttu-id="744ec-110">Například typ hodnoty návratu metoda getter vlastnosti volající obdrží kopii.</span><span class="sxs-lookup"><span data-stu-id="744ec-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="744ec-111">Vzhledem k tomu, že kopie je vytvořena implicitně, vývojáři se nemusíte být vědomi, mutace kopii a na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="744ec-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="744ec-112">Některé jazyky (dynamické jazyky, zejména) také mít problémy pomocí proměnlivé hodnoty typů, protože i lokální proměnné, při dereferenci, způsobit, že kopie má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="744ec-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="744ec-113">**✓ DO** jistotu, že stav, kde všechny instance dat je nastavený na nulu, false, nebo hodnotu null (podle potřeby) je platný.</span><span class="sxs-lookup"><span data-stu-id="744ec-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="744ec-114">To zabraňuje nechtěnému vytváření instancí neplatný při vytváření pole struktury.</span><span class="sxs-lookup"><span data-stu-id="744ec-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="744ec-115">**✓ DO** implementovat <xref:System.IEquatable%601> u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="744ec-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="744ec-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Metoda u typů hodnot způsobí, že zabalení a jeho výchozí implementace není velmi efektivní, protože používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="744ec-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="744ec-117"><xref:System.IEquatable%601.Equals%2A> může mít mnohem lepší výkon a může být implementováno tak, aby nezpůsobí zabalení.</span><span class="sxs-lookup"><span data-stu-id="744ec-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="744ec-118">**X DO NOT** explicitně rozšířit <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="744ec-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="744ec-119">Ve skutečnosti většina jazyků to neumožňuje.</span><span class="sxs-lookup"><span data-stu-id="744ec-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="744ec-120">Obecně platí struktury může být velmi užitečné, ale by měla sloužit pouze pro malé, jednu, neměnné hodnoty, které se nesmí použít boxing. často.</span><span class="sxs-lookup"><span data-stu-id="744ec-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="744ec-121">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="744ec-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="744ec-122">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="744ec-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744ec-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="744ec-123">See also</span></span>

- [<span data-ttu-id="744ec-124">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="744ec-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="744ec-125">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="744ec-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="744ec-126">Volba mezi třídou a strukturou</span><span class="sxs-lookup"><span data-stu-id="744ec-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
