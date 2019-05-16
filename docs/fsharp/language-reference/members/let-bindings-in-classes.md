---
title: Vazby let ve třídách
description: Zjistěte, jak definovat privátní pole a soukromé funkce pro F# třídy pomocí vazeb let' v definici třídy.
ms.date: 05/16/2016
ms.openlocfilehash: 29f843e3e065837a53fd5eb26c79088bc0778c76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645178"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="000f2-103">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="000f2-103">let Bindings in Classes</span></span>

<span data-ttu-id="000f2-104">Můžete definovat privátní pole a soukromé funkce pro F# třídy pomocí `let` vazby v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="000f2-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="000f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="000f2-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="000f2-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="000f2-106">Remarks</span></span>

<span data-ttu-id="000f2-107">Předchozí syntaxi se zobrazí po deklarace záhlaví a dědičnost tříd, ale před všechny definice členů.</span><span class="sxs-lookup"><span data-stu-id="000f2-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="000f2-108">Syntaxe je stejně jako u `let` vazby mimo třídy, ale názvy definované ve třídě mají obor, který je omezená na třídu.</span><span class="sxs-lookup"><span data-stu-id="000f2-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="000f2-109">A `let` vazbou soukromé pole nebo funkce; ke zveřejňování dat nebo funkce deklarovat veřejně, vlastnost nebo metodu member.</span><span class="sxs-lookup"><span data-stu-id="000f2-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="000f2-110">A `let` vazby, která není statická nazývá instance `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="000f2-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="000f2-111">Instance `let` vazby spustí, když jsou vytvořeny objekty.</span><span class="sxs-lookup"><span data-stu-id="000f2-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="000f2-112">Statické `let` vazby jsou součástí statický inicializátor pro třídu, která je zaručeno, že ke spuštění před první typ slouží.</span><span class="sxs-lookup"><span data-stu-id="000f2-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="000f2-113">Kód v rámci instance `let` vazby můžete použít parametry primárního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="000f2-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="000f2-114">Atributy a modifikátory dostupnosti nejsou u povolené `let` vazby ve třídách.</span><span class="sxs-lookup"><span data-stu-id="000f2-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="000f2-115">Následující příklady kódu znázorňují několik typů `let` vazby ve třídách.</span><span class="sxs-lookup"><span data-stu-id="000f2-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="000f2-116">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="000f2-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="000f2-117">Alternativní způsoby, jak vytvořit pole</span><span class="sxs-lookup"><span data-stu-id="000f2-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="000f2-118">Můžete také použít `val` – klíčové slovo vytvořit soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="000f2-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="000f2-119">Při použití `val` – klíčové slovo, pole není zadána hodnota, pokud objekt je vytvořen, ale místo toho se inicializuje s výchozí hodnotou.</span><span class="sxs-lookup"><span data-stu-id="000f2-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="000f2-120">Další informace najdete v tématu [explicitní pole: Val – klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="000f2-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="000f2-121">Můžete také definovat privátní pole v třídě pomocí definice členské a přidáním klíčového slova `private` na definici.</span><span class="sxs-lookup"><span data-stu-id="000f2-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="000f2-122">To může být užitečné, pokud očekáváte, změňte přístupnost člena bez přepsání kódu.</span><span class="sxs-lookup"><span data-stu-id="000f2-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="000f2-123">Další informace najdete v tématu [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="000f2-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="000f2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="000f2-124">See also</span></span>

- [<span data-ttu-id="000f2-125">Členové</span><span class="sxs-lookup"><span data-stu-id="000f2-125">Members</span></span>](index.md)
- [<span data-ttu-id="000f2-126">`do` Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="000f2-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="000f2-127">`let` Vazby</span><span class="sxs-lookup"><span data-stu-id="000f2-127">`let` Bindings</span></span>](../functions/let-bindings.md)
