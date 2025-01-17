---
title: sizeof – C# operátor odkazu
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 32103043d4c3a8b38f4c8aad80282f6c0555719f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038940"
---
# <a name="sizeof-operator-c-reference"></a>sizeof – operátorC# (Referenční dokumentace)

Operátor `sizeof` vrátí počet bajtů obsazených proměnnou daného typu. Argument operátoru `sizeof` musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.

Operátor `sizeof` vyžaduje [nezabezpečený](../keywords/unsafe.md) kontext. Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:

|Výraz|Hodnota konstanty|
|---------|---------------|
|`sizeof(sbyte)`|první|
|`sizeof(byte)`|první|
|`sizeof(short)`|odst|
|`sizeof(ushort)`|odst|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|odst|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16bitovém|
|`sizeof(bool)`|první|

Nemusíte také používat nezabezpečený kontext, pokud je Operand operátoru `sizeof` název typu [výčtu](../keywords/enum.md) .

Následující příklad ukazuje použití operátoru `sizeof`:

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

Operátor `sizeof` vrací počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti. U typů [struktury](../keywords/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad. Výsledek operátoru `sizeof` se může lišit od výsledku metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, která vrací velikost typu v *nespravované* paměti.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazateli](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
