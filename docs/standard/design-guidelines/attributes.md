---
title: Atributy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785564"
---
# <a name="attributes"></a><span data-ttu-id="f4d1c-102">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4d1c-102">Attributes</span></span>
<span data-ttu-id="f4d1c-103"><xref:System.Attribute?displayProperty=nameWithType> slouží k definování uživatelských atributů, které základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="f4d1c-104">Atributy jsou poznámky, které mohou být přidány pro programovací prvky, jako je například sestavení, typy, členy a parametry.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="f4d1c-105">Tyto jsou uložené v metadatech sestavení a je přístupný za běhu pomocí reflexe rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="f4d1c-106">Například rozhraní definuje <xref:System.ObsoleteAttribute>, který je možné použít u typu nebo člena k označení, že tento typ nebo člen je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="f4d1c-107">Atributy mohou mít jednu nebo více vlastností, které přenášejí další data související s atributem.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="f4d1c-108">Například `ObsoleteAttribute` by mohl provést další informace o verzi v které typ nebo člen je teď zastaralé a popis nové rozhraní API nahrazení zastaralé rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="f4d1c-109">Některé vlastnosti atributu je třeba zadat při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="f4d1c-110">Tyto jsou označovány jako požadované vlastnosti nebo povinné argumenty, protože jsou reprezentovány jako konstruktor poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="f4d1c-111">Například <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> vlastnost <xref:System.Diagnostics.ConditionalAttribute> je povinná.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="f4d1c-112">Vlastnosti, které není potřeba zadat, když se atribut používá, se nazývají volitelné vlastnosti (nebo nepovinné argumenty).</span><span class="sxs-lookup"><span data-stu-id="f4d1c-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="f4d1c-113">Jsou zobrazeny v nastavitelné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-113">They are represented by settable properties.</span></span> <span data-ttu-id="f4d1c-114">Kompilátory poskytují speciální syntax k nastavení těchto vlastností, při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="f4d1c-115">Například <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> představuje vlastnost nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="f4d1c-116">**✓ DO** název třídy vlastních atributů s příponou "Atribut."</span><span class="sxs-lookup"><span data-stu-id="f4d1c-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="f4d1c-117">**✓ DO** použít <xref:System.AttributeUsageAttribute> vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="f4d1c-118">**✓ DO** zadejte nastavit vlastnosti pro volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="f4d1c-119">**✓ DO** zadejte vlastnosti jen get pro povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="f4d1c-120">**✓ DO** zadat parametry konstruktor k chybě při inicializaci vlastnosti odpovídající povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="f4d1c-121">Každý parametr by měl mít stejný název (i když s jinou velikostí písmen) jako odpovídající vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="f4d1c-122">**X AVOID** poskytuje konstruktor parametry k chybě při inicializaci vlastnosti odpovídající volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="f4d1c-123">Jinými slovy nemají vlastnosti, které lze nastavit pomocí konstruktoru a setter.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="f4d1c-124">Toto pravidlo umožňuje velmi explicitní argumenty, které jsou volitelné a které jsou požadovány a díky tomu není nutné dva způsoby provedení stejného kroku.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="f4d1c-125">**X AVOID** přetížení konstruktory vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="f4d1c-126">Máte jenom jeden konstruktor jasně komunikuje uživateli argumenty, které se vyžadují a které jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="f4d1c-127">**✓ DO** zapečetit vlastní atribut třídy, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="f4d1c-128">Díky tomu vyhledávání pro atribut rychleji.</span><span class="sxs-lookup"><span data-stu-id="f4d1c-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="f4d1c-129">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="f4d1c-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f4d1c-130">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="f4d1c-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d1c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4d1c-131">See also</span></span>

- [<span data-ttu-id="f4d1c-132">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="f4d1c-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f4d1c-133">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="f4d1c-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
