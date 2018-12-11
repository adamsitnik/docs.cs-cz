---
title: '[] – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 3e2ce5c4b74cbf79e00410791ffcc31368f78648
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243995"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a7202-102">[] – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a7202-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="a7202-103">Hranaté závorky (`[]`) se používají pro pole, indexery a atributy.</span><span class="sxs-lookup"><span data-stu-id="a7202-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="a7202-104">Můžete také používají s ukazateli.</span><span class="sxs-lookup"><span data-stu-id="a7202-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7202-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7202-105">Remarks</span></span>  
 <span data-ttu-id="a7202-106">Typ pole je typu, za nímž následuje `[]`:</span><span class="sxs-lookup"><span data-stu-id="a7202-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="a7202-107">O přístup k prvku pole, index požadovaný element uzavřený v hranatých závorkách:</span><span class="sxs-lookup"><span data-stu-id="a7202-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="a7202-108">Pokud pole indexu je mimo rozsah, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a7202-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="a7202-109">Pole indexování operátor nelze přetížit; typy však můžete definovat indexerů, které provést jeden nebo více parametrů.</span><span class="sxs-lookup"><span data-stu-id="a7202-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="a7202-110">Indexer parametry jsou uzavřeny do hranatých závorek, stejně jako indexy pole, ale mohou být deklarovány parametry indexer bude libovolný typ, na rozdíl od indexy pole, které musí být integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="a7202-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="a7202-111">Například rozhraní .NET Framework definuje `Hashtable` typ, který přidruží klíče a hodnoty libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="a7202-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="a7202-112">Hranaté závorky se také používají k určení [atributy](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="a7202-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="a7202-113">Hranaté závorky můžete použít k indexování vypnout ukazatel:</span><span class="sxs-lookup"><span data-stu-id="a7202-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="a7202-114">Žádné kontroly hranic, se provádí.</span><span class="sxs-lookup"><span data-stu-id="a7202-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a7202-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7202-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7202-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7202-116">See Also</span></span>

- [<span data-ttu-id="a7202-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7202-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a7202-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a7202-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a7202-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7202-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="a7202-120">Pole</span><span class="sxs-lookup"><span data-stu-id="a7202-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="a7202-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="a7202-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="a7202-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="a7202-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="a7202-123">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7202-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
