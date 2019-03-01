---
title: Omezení přístupnosti přístupového objektu - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 24df3a78487cf054a2682b3fbdf8d78b37c4ea6b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979447"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="1a7ef-102">Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1a7ef-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="1a7ef-103">[Získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) části vlastnost nebo indexer, se nazývají *přistupující objekty*.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="1a7ef-104">Ve výchozím nastavení tyto přístupové objekty mít stejnou úroveň viditelnosti nebo přístup k vlastnosti nebo indexeru, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="1a7ef-105">Další informace najdete v tématu [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1a7ef-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="1a7ef-106">Někdy je však užitečný k omezení přístupu k jednomu z těchto přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="1a7ef-107">Obvykle to zahrnuje omezení přístupnost `set` přístupového objektu při zachování `get` přistupující objekt veřejně přístupná.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="1a7ef-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="1a7ef-109">V tomto příkladu vlastnost s názvem `Name` definuje `get` a `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="1a7ef-110">`get` Přistupující objekt obdrží úrovni přístupu, samotná hodnota vlastnosti `public` v tomto případě while `set` přístupový objekt je explicitně s omezením pomocí specifikátoru použitím [chráněné](../../../csharp/language-reference/keywords/protected.md) modifikátor přístupu k přístupový objekt samotný.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="1a7ef-111">Omezení přístupu modifikátory přístupu na přístupových objektů</span><span class="sxs-lookup"><span data-stu-id="1a7ef-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="1a7ef-112">Pomocí modifikátory přistupující objekt vlastnosti nebo indexery podléhá tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="1a7ef-113">Přístupový objekt Modifikátory nelze použít na rozhraní nebo explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace členu.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="1a7ef-114">Modifikátory přístupového objektu můžete použít pouze v případě, že vlastnost nebo indexovací člen jsou obě `set` a `get` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="1a7ef-115">V takovém případě modifikátor smí obsahovat pouze pro jednu ze dvou přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
-   <span data-ttu-id="1a7ef-116">Pokud má vlastnost nebo indexer [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor, modifikátor přístupového objektu musí odpovídat přistupující objekt přepsané přístupového objektu, případné.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="1a7ef-117">Usnadnění úrovní na přistupujícím objektu musí být více omezující než úroveň přístupnost na vlastnost nebo indexovací člen, samotného.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="1a7ef-118">Modifikátory přístupu pro přepsání přístupové objekty</span><span class="sxs-lookup"><span data-stu-id="1a7ef-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="1a7ef-119">Při přepsání vlastnost nebo indexovací člen přepsané přistupující objekty musí být přístupná pro přepsání kódu.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="1a7ef-120">Navíc přístupnost vlastnost nebo indexer a jeho přístupových objektů musí odpovídat odpovídající přepsané vlastnosti nebo indexeru a jeho přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="1a7ef-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="1a7ef-122">Implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a7ef-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="1a7ef-123">Při použití přístupový objekt pro implementaci rozhraní přistupujícím objektu nemusí mít modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="1a7ef-124">Nicméně Pokud implementujete rozhraní pomocí jeden přistupující objekt, jako například `get`, další přístupový objekt může mít modifikátor přístupu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="1a7ef-125">Doména přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="1a7ef-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="1a7ef-126">Pokud použijete modifikátor přístupu nastaven na přístupový objekt, [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md) přistupujícím objektu je určen tento modifikátor.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="1a7ef-127">Pokud jste nepoužili modifikátor přístupu nastaven na přistupujícím objektu, tak doména přístupnosti přístupového objektu se určuje podle úrovně přístupnosti vlastnost nebo indexer.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a7ef-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a7ef-128">Example</span></span>  
 <span data-ttu-id="1a7ef-129">Následující příklad obsahuje tři třídy `BaseClass`, `DerivedClass`, a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="1a7ef-130">Existují dvě vlastnosti na `BaseClass`, `Name` a `Id` v obou třídách.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="1a7ef-131">Tento příklad ukazuje, jak vlastnost `Id` na `DerivedClass` může být skryta vlastnost `Id` na `BaseClass` při použití modifikátor omezení přístupu, jako [chráněné](../../../csharp/language-reference/keywords/protected.md) nebo [ privátní](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="1a7ef-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="1a7ef-132">Proto když přiřadit hodnoty této vlastnosti, vlastnost na `BaseClass` třída se nazývá místo.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="1a7ef-133">Nahrazení modifikátor přístupu podle [veřejné](../../../csharp/language-reference/keywords/public.md) zpřístupní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="1a7ef-134">Tento příklad také ukazuje, že modifikátor omezení přístupu, jako `private` nebo `protected`na `set` přistupující objekt `Name` vlastnost v `DerivedClass` brání v přístupu k přistupujícím objektu a vygeneruje chybu, pokud přiřadíte ho.</span><span class="sxs-lookup"><span data-stu-id="1a7ef-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="1a7ef-135">Komentáře</span><span class="sxs-lookup"><span data-stu-id="1a7ef-135">Comments</span></span>  
 <span data-ttu-id="1a7ef-136">Všimněte si, že pokud nahradíte deklarace `new private string Id` podle `new public string Id`, získáte výstup:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="1a7ef-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a7ef-137">See also</span></span>

- [<span data-ttu-id="1a7ef-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1a7ef-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1a7ef-139">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1a7ef-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="1a7ef-140">Indexery</span><span class="sxs-lookup"><span data-stu-id="1a7ef-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="1a7ef-141">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="1a7ef-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
