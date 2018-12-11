---
title: objekt – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: a1917a7925d4ed90ede40248fa394f9c45d09b4e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238962"
---
# <a name="object-c-reference"></a><span data-ttu-id="436f0-102">object (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="436f0-102">object (C# Reference)</span></span>

<span data-ttu-id="436f0-103">`object` Typ je alias pro <xref:System.Object> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="436f0-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="436f0-104">V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="436f0-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="436f0-105">Můžete přiřadit proměnné typu hodnoty libovolného typu `object`.</span><span class="sxs-lookup"><span data-stu-id="436f0-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="436f0-106">Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*.</span><span class="sxs-lookup"><span data-stu-id="436f0-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="436f0-107">Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*.</span><span class="sxs-lookup"><span data-stu-id="436f0-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="436f0-108">Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="436f0-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="436f0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="436f0-109">Example</span></span>

<span data-ttu-id="436f0-110">Následující ukázkový ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu dat a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="436f0-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="436f0-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="436f0-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="436f0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="436f0-112">See also</span></span>

- [<span data-ttu-id="436f0-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="436f0-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="436f0-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="436f0-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="436f0-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="436f0-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="436f0-116">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="436f0-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="436f0-117">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="436f0-117">Value Types</span></span>](value-types.md)