---
title: do – vazby
description: Zjistěte, jak F# "do" vazby se používá k provádění kódu bez definování funkce nebo hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: d29f8557fda06097d2e85748ab6286f0415730b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683376"
---
# <a name="do-bindings"></a><span data-ttu-id="da9a8-103">do – vazby</span><span class="sxs-lookup"><span data-stu-id="da9a8-103">do Bindings</span></span>

<span data-ttu-id="da9a8-104">A `do` vazby se používá k provádění kódu bez definování funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="da9a8-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="da9a8-105">Také proveďte vazby může být použit ve třídách, naleznete v tématu [ `do` vazby ve třídách](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="da9a8-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="da9a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da9a8-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="da9a8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da9a8-107">Remarks</span></span>

<span data-ttu-id="da9a8-108">Použití `do` vazby, pokud chcete spustit kód bez ohledu na jejich definici funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="da9a8-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="da9a8-109">Výraz v `do` vazby musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="da9a8-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="da9a8-110">Kód v nejvyšší úrovni `do` vazby je proveden při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="da9a8-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="da9a8-111">Klíčové slovo `do` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="da9a8-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="da9a8-112">Atributy lze použít na nejvyšší úrovni `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="da9a8-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="da9a8-113">Například pokud program používá zprostředkovatele komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašemu programu.</span><span class="sxs-lookup"><span data-stu-id="da9a8-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="da9a8-114">Můžete to provést pomocí atributu na `do` vazbu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="da9a8-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="da9a8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da9a8-115">See also</span></span>

- [<span data-ttu-id="da9a8-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="da9a8-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="da9a8-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="da9a8-117">Functions</span></span>](index.md)