---
title: Předdefinované typy – C# odkaz na tabulku
ms.custom: seodec18
description: Klíčová slova pro předdefinované C# typy
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 22bdfa197e3ce9c119203c74eeb0eb8217022a68
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422911"
---
# <a name="built-in-types-table-c-reference"></a>Tabulka předdefinovaných typů (C# Referenční dokumentace)

V následující tabulce jsou uvedena klíčová slova pro předdefinované C# typy, což jsou aliasy předdefinovaných typů v oboru názvů <xref:System>:

|C#textový|Typ .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Poznámky

Všechny typy v tabulce, kromě `object` a `string`, se označují jako jednoduché typy.

Typy rozhraní .NET a jejich C# aliasy jejich typu jsou zaměnitelné. Můžete například deklarovat celočíselnou proměnnou pomocí kterékoli z následujících deklarací:

```csharp
int x = 123;
System.Int32 y = 123;
```

Použijte operátor [typeof](../operators/type-testing-and-cast.md#typeof-operator) k získání <xref:System.Type?displayProperty=nameWithType> instance, která představuje zadaný typ:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy hodnot](value-types.md)
- [Typy odkazů](reference-types.md)
- [Tabulka výchozích hodnot](default-values-table.md)
- [dynamic](../builtin-types/reference-types.md)
