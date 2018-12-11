---
title: Použití operátorů převodu - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 908067c3ad6cae34dd223bd608a74ba1cd7a88a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236866"
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="2e017-102">Použití operátorů převodu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2e017-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="2e017-103">Je možné použít operátory převodů `implicit`, které jsou jednodušší, nebo operátory převodů `explicit`, které jasně označují každému, kdo čte kód, že převádíte typ.</span><span class="sxs-lookup"><span data-stu-id="2e017-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="2e017-104">Toto téma ukazuje oba typy operátorů převodu.</span><span class="sxs-lookup"><span data-stu-id="2e017-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e017-105">Informace o převodech jednoduchého typu naleznete v tématu [jak: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [jak: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), nebo <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="2e017-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e017-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e017-106">Example</span></span>  
 <span data-ttu-id="2e017-107">Toto je příklad explicitního operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="2e017-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="2e017-108">Tento operátor převede typ <xref:System.Byte> na hodnotu s názvem `Digit`.</span><span class="sxs-lookup"><span data-stu-id="2e017-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="2e017-109">Vzhledem k tomu, že ne všechny bajty mohou být převedeny na číslice, je převod explicitní a znamená, že musí být použito přetypování, jak je znázorněno v metodě `Main`.</span><span class="sxs-lookup"><span data-stu-id="2e017-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2e017-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e017-110">Example</span></span>  
 <span data-ttu-id="2e017-111">Tento příklad ukazuje operátor implicitního převodu definováním operátoru převodu, který vrátí zpět, co předchozí příklad udělal: převede z hodnotové třídy s názvem `Digit` na integrál typu <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="2e017-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="2e017-112">Protože libovolná číslice může být převedena na <xref:System.Byte>, není potřeba přinutit uživatele k explicitnímu převodu.</span><span class="sxs-lookup"><span data-stu-id="2e017-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2e017-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e017-113">See Also</span></span>

- [<span data-ttu-id="2e017-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e017-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2e017-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2e017-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2e017-116">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="2e017-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [<span data-ttu-id="2e017-117">is</span><span class="sxs-lookup"><span data-stu-id="2e017-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
