---
title: implicitní - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: d3e1cb9d6fb37617c6e2aa7070b006c594d39762
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661474"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="ee6fe-102">implicit (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ee6fe-102">implicit (C# Reference)</span></span>

<span data-ttu-id="ee6fe-103">`implicit` – Klíčové slovo se používá k deklaraci implicitního uživatelem definovaného typu operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="ee6fe-104">Pokud převod je zaručeno, že způsobit ztrátu dat, použijte ji Pokud chcete povolit implicitní převody mezi uživatelem definovaného typu a jiného typu.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>

## <a name="example"></a><span data-ttu-id="ee6fe-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee6fe-105">Example</span></span>

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

<span data-ttu-id="ee6fe-106">Odstraněním nepotřebných přetypování implicitní převod může zlepšit čitelnost zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="ee6fe-107">Ale protože implicitní převody nevyžadují, aby programátoři explicitně přetypovat z jednoho typu na druhý, musí věnovat pozornost zabránit neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="ee6fe-108">Operátory implicitního převodu by měla obecně platí, nikdy nevyvolají výjimky a tak, aby bylo možné bezpečně bez sledování serverů programátora nikdy dojít ke ztrátě informací.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="ee6fe-109">Pokud se operátor převodu nemůže splnění těchto kritérií, by měla být označena `explicit`.</span><span class="sxs-lookup"><span data-stu-id="ee6fe-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="ee6fe-110">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ee6fe-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee6fe-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee6fe-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ee6fe-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee6fe-112">See also</span></span>

- [<span data-ttu-id="ee6fe-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee6fe-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ee6fe-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ee6fe-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ee6fe-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee6fe-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ee6fe-116">explicit</span><span class="sxs-lookup"><span data-stu-id="ee6fe-116">explicit</span></span>](explicit.md)
- [<span data-ttu-id="ee6fe-117">– Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ee6fe-117">operator (C# Reference)</span></span>](operator.md)
- [<span data-ttu-id="ee6fe-118">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="ee6fe-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
