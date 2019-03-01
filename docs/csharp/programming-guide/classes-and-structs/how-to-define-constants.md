---
title: 'Postupy: Definování konstant vC#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: cf57589df2eb375f34d175939a7f685a4abf59a2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975417"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="e8362-102">Postupy: Definování konstant v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="e8362-102">How to: Define Constants in C\#</span></span>
<span data-ttu-id="e8362-103">Konstanty jsou pole, jejichž hodnoty se nastavují v době kompilace a nikdy se dá změnit.</span><span class="sxs-lookup"><span data-stu-id="e8362-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="e8362-104">Použijte k poskytnutí smysluplné názvy namísto číselných literálů ("čísla magic") pro zvláštní hodnoty konstant.</span><span class="sxs-lookup"><span data-stu-id="e8362-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8362-105">V jazyce C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) direktivy preprocesoru nelze použít pro definování konstant ve způsobu, jakým se obvykle používá v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="e8362-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="e8362-106">Pro definování hodnot konstanty celočíselných typů (`int`, `byte`, a tak dále) použijte výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="e8362-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="e8362-107">Další informace najdete v tématu [výčtu](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="e8362-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="e8362-108">Definovat konstanty neintegrálních, jedním z přístupů je seskupovat je do jedné statickou třídu s názvem `Constants`.</span><span class="sxs-lookup"><span data-stu-id="e8362-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="e8362-109">To vyžaduje, aby všechny odkazy na konstanty být uvozena řetězcem názvu třídy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e8362-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8362-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8362-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="e8362-111">Použití kvalifikátoru název třídy pomáhá, ujistěte se, že můžete vy a ostatní, kteří používají konstanta pochopit, že je konstantní a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="e8362-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8362-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8362-112">See also</span></span>

- [<span data-ttu-id="e8362-113">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="e8362-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
