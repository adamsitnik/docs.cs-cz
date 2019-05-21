---
title: fixed Statement - C# odkaz
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2c49c8517e15534121b0f8dbc04902b46a92ef20
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959360"
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

`fixed` Příkaz zabraňuje přemístění přesouvatelný proměnné systému uvolňování paměti. `fixed` Příkaz je povolen pouze v [nebezpečné](unsafe.md) kontextu. Můžete také použít `fixed` – klíčové slovo k vytvoření [pevných vyrovnávacích pamětí velikost](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Příkaz nastaví ukazatel na proměnnou spravované a "kódy PIN" Tato proměnná během provádění příkazu. Odkazy na přesouvatelný spravované proměnné jsou užitečné pouze `fixed` kontextu. Bez `fixed` kontextu, uvolňování paměti může přemístit proměnné nepředvídatelné. Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel na proměnnou spravované v `fixed` příkazu.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Ukazatele lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ukazuje použití řetězce, pole a adresy proměnné:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Od verze C# 7.3, `fixed` příkaz funguje u dalších typů mimo pole, řetězce, vyrovnávací paměti pevné velikosti nebo nespravované proměnné. Libovolný typ, který implementuje metodu s názvem `GetPinnableReference` je možné připnout. `GetPinnableReference` Musí vrátit `ref` proměnné k nespravovaným typem. Naleznete v tématu o [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md) Další informace. Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedena v rozhraní .NET Core 2.0 Zkontrolujte použití tohoto modelu a je možné připnout. To je ukázáno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytváříte v tomto modelu typy, které by se měly podílet, přečtěte si téma <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> příklad implementace vzoru.

Většího počtu ukazatelů lze inicializovat v jednom příkazu, pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

K inicializaci ukazatele na různé typy, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po provedení kódu v příkazu jsou všechny připnuté proměnné nepřipnuté a uvolňování paměti. Proto neukazují na těchto proměnných mimo `fixed` příkazu. Proměnné deklarované v `fixed` příkaz mají rozsah, který tento příkaz, aby toto:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Ukazatele inicializované v `fixed` příkazy jsou proměnné určené jen pro čtení. Pokud chcete změnit hodnotu ukazatele, musí deklarovat proměnnou druhý ukazatel a upravit. Proměnná deklarovaná ve `fixed` nelze upravit – příkaz:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Můžete přidělit paměť v zásobníku, kde není časovač uvolněn z paměti a proto není potřeba připnout. Provedete to, které používají [ `stackalloc` operátor](stackalloc.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [příkazu fixed](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [unsafe](unsafe.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
