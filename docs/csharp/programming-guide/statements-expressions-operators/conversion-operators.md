---
title: Operátory převodu - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: a55a2148ce161deca79d8ba8e64a217e474f0284
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236814"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="80b18-102">Operátory převodu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="80b18-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="80b18-103">C# umožňuje programátorům deklarovat převody na třídy nebo struktury tak, aby třídy nebo struktury lze převést na nebo z jiné třídy nebo struktury nebo základní typy.</span><span class="sxs-lookup"><span data-stu-id="80b18-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="80b18-104">Převody jsou definovány jako operátory a jsou pojmenovány pro typ, ke kterému převodu.</span><span class="sxs-lookup"><span data-stu-id="80b18-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="80b18-105">Typ argumentu, který má být převeden nebo typ výsledku převodu, ale ne obojí, musí být nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="80b18-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="80b18-106">Přehled operátorů převodů</span><span class="sxs-lookup"><span data-stu-id="80b18-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="80b18-107">Operátory převodu mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="80b18-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="80b18-108">Převody deklarovány jako `implicit` automaticky provedou, když je povinný.</span><span class="sxs-lookup"><span data-stu-id="80b18-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="80b18-109">Převody deklarovány jako `explicit` vyžaduje přetypování, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="80b18-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="80b18-110">Musí být všechny převody deklarovány jako `static`.</span><span class="sxs-lookup"><span data-stu-id="80b18-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80b18-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="80b18-111">Related Sections</span></span>  
 <span data-ttu-id="80b18-112">Další informace:</span><span class="sxs-lookup"><span data-stu-id="80b18-112">For more information:</span></span>  
  
-   [<span data-ttu-id="80b18-113">Použití operátorů převodu</span><span class="sxs-lookup"><span data-stu-id="80b18-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="80b18-114">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="80b18-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="80b18-115">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="80b18-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="80b18-116">explicit</span><span class="sxs-lookup"><span data-stu-id="80b18-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="80b18-117">implicit</span><span class="sxs-lookup"><span data-stu-id="80b18-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="80b18-118">static</span><span class="sxs-lookup"><span data-stu-id="80b18-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="80b18-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="80b18-119">See Also</span></span>

- <xref:System.Convert>  
- [<span data-ttu-id="80b18-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="80b18-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="80b18-121">Zřetězit uživatelem definované explicitní převody v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="80b18-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
