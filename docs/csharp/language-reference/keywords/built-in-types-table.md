---
title: Tabulka předdefinovaných typů - C# odkaz
ms.custom: seodec18
description: Klíčová slova pro předdefinované typy jazyka C#
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: d93176b850d84753106accef3bcaedab38f4ddc7
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306801"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="04d28-103">Tabulka předdefinovaných typů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="04d28-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="04d28-104">V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="04d28-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="04d28-105">Typ jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04d28-105">C# type</span></span>|<span data-ttu-id="04d28-106">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="04d28-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="04d28-107">bool</span><span class="sxs-lookup"><span data-stu-id="04d28-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-108">byte</span><span class="sxs-lookup"><span data-stu-id="04d28-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="04d28-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-110">char</span><span class="sxs-lookup"><span data-stu-id="04d28-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-111">decimal</span><span class="sxs-lookup"><span data-stu-id="04d28-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-112">double</span><span class="sxs-lookup"><span data-stu-id="04d28-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-113">float</span><span class="sxs-lookup"><span data-stu-id="04d28-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-114">int</span><span class="sxs-lookup"><span data-stu-id="04d28-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-115">uint</span><span class="sxs-lookup"><span data-stu-id="04d28-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-116">long</span><span class="sxs-lookup"><span data-stu-id="04d28-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-117">ulong</span><span class="sxs-lookup"><span data-stu-id="04d28-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-118">object</span><span class="sxs-lookup"><span data-stu-id="04d28-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-119">short</span><span class="sxs-lookup"><span data-stu-id="04d28-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-120">ushort</span><span class="sxs-lookup"><span data-stu-id="04d28-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="04d28-121">string</span><span class="sxs-lookup"><span data-stu-id="04d28-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="04d28-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04d28-122">Remarks</span></span>

<span data-ttu-id="04d28-123">Všechny typy v tabulce, s výjimkou `object` a `string`, jsou označovány jako jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="04d28-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="04d28-124">Jazyce C# zadejte klíčová slova a jejich aliasy jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="04d28-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="04d28-125">Například je možné deklarovat celočíselné proměnné pomocí některé z následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="04d28-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="04d28-126">Použití [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) operátor zobrazíte <xref:System.Type?displayProperty=nameWithType> instanci, která představuje zadaný typ:</span><span class="sxs-lookup"><span data-stu-id="04d28-126">Use the [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="04d28-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04d28-127">See also</span></span>

- [<span data-ttu-id="04d28-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04d28-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="04d28-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="04d28-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="04d28-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04d28-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="04d28-131">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="04d28-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="04d28-132">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="04d28-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="04d28-133">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="04d28-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="04d28-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="04d28-134">dynamic</span></span>](dynamic.md)
