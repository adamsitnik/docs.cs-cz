---
title: Vícerozměrná pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 4547bd94a0870dbb3955c4980361c8be0453616d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642409"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="8d262-102">Vícerozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8d262-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8d262-103">Pole může mít více než jeden rozměr.</span><span class="sxs-lookup"><span data-stu-id="8d262-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="8d262-104">Například následující deklaraci vytvoří dvourozměrné pole čtyři řádky a dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="8d262-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="8d262-105">Následující deklarace je vytvořeno pole tří dimenze, 4, 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="8d262-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="8d262-106">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="8d262-106">Array Initialization</span></span>

 <span data-ttu-id="8d262-107">Inicializovat pole při deklaraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8d262-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="8d262-108">Také můžete inicializovat pole bez určení pořadí.</span><span class="sxs-lookup"><span data-stu-id="8d262-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="8d262-109">Pokud se rozhodnete pro deklaraci proměnné pole bez inicializace, je nutné použít `new` operátor přiřazení pole do proměnné.</span><span class="sxs-lookup"><span data-stu-id="8d262-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="8d262-110">Použití `new` je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8d262-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="8d262-111">Následující příklad přiřadí hodnotu konkrétního pole elementu.</span><span class="sxs-lookup"><span data-stu-id="8d262-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="8d262-112">Obdobně následující příklad získá hodnotu prvku konkrétní pole a přiřadí ji k proměnné `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="8d262-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="8d262-113">Následující příklad kódu inicializuje prvky pole, které mají výchozí hodnoty (s výjimkou vícenásobných polí).</span><span class="sxs-lookup"><span data-stu-id="8d262-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8d262-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d262-114">See also</span></span>

- [<span data-ttu-id="8d262-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8d262-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8d262-116">Pole</span><span class="sxs-lookup"><span data-stu-id="8d262-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="8d262-117">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8d262-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="8d262-118">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="8d262-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
