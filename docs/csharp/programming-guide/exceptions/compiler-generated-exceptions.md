---
title: Výjimky - generovaný kompilátorem C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: e21b75e5b7e338bda54ca00abaa733775865fdb9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238387"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="77352-102">Výjimky generované kompilátorem (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="77352-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="77352-103">Některé výjimky jsou vyvolány automaticky modulem CLR rozhraní .NET Framework common language runtime (CLR), když dojde k selhání základních operací.</span><span class="sxs-lookup"><span data-stu-id="77352-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="77352-104">Tyto výjimky a jejich chybové podmínky jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="77352-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="77352-105">Výjimka</span><span class="sxs-lookup"><span data-stu-id="77352-105">Exception</span></span>|<span data-ttu-id="77352-106">Popis</span><span class="sxs-lookup"><span data-stu-id="77352-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="77352-107">Základní třída pro výjimky, ke kterým dochází při aritmetické operace, jako například <xref:System.DivideByZeroException> a <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="77352-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="77352-108">Vyvolána, když pole Nejde uložit daného elementu, protože skutečný typ elementu, který není kompatibilní s skutečný typ pole.</span><span class="sxs-lookup"><span data-stu-id="77352-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="77352-109">Vyvolána, když je proveden pokus o se má dělit celočíselnou hodnotu nulou.</span><span class="sxs-lookup"><span data-stu-id="77352-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="77352-110">Vyvolána, když je proveden pokus o indexu pole, pokud je index menší než nula nebo mimo hranice pole.</span><span class="sxs-lookup"><span data-stu-id="77352-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="77352-111">Vyvolána, když selže explicitní převod z typu základní rozhraní nebo odvozeného typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="77352-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="77352-112">Vyvolána, jestliže se pokusíte odkazovat na objekt, jehož hodnota je [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="77352-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="77352-113">Při pokusu o přidělení paměti pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md) operátor selže.</span><span class="sxs-lookup"><span data-stu-id="77352-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="77352-114">To znamená, že byly vyčerpány paměť dostupnou pro modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="77352-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="77352-115">Vyvolána, když v aritmetické operace `checked` kontextu přetečení.</span><span class="sxs-lookup"><span data-stu-id="77352-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="77352-116">Vyvolána, když se vyčerpá zásobníku spouštění tak, že příliš mnoho volání metody čekající; obvykle označuje velmi podrobné nebo nekonečné rekurzi.</span><span class="sxs-lookup"><span data-stu-id="77352-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="77352-117">Vyvolána, když statický konstruktor vyvolá výjimku a žádné kompatibilní `catch` existuje klauzule má zachytit.</span><span class="sxs-lookup"><span data-stu-id="77352-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77352-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="77352-118">See Also</span></span>

- [<span data-ttu-id="77352-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="77352-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="77352-120">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="77352-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
- [<span data-ttu-id="77352-121">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="77352-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [<span data-ttu-id="77352-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="77352-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="77352-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="77352-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
- [<span data-ttu-id="77352-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="77352-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
