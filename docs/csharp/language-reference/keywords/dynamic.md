---
title: dynamické - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: d2aef5b2ed291aab917573408abf26b9fbedfbd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661773"
---
# <a name="dynamic-c-reference"></a>dynamic (Referenční dokumentace jazyka C#)

`dynamic` Typ umožní operace, ve kterých se vyskytuje obejít kontrolu typu v době kompilace. Tyto operace jsou místo toho přeložit v době běhu. `dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API automatizace sady Office a taky dynamické rozhraní API, jako jsou knihovny Ironpythonu a do HTML Document Object Model (DOM).

Typ `dynamic` se chová jako typ `object` ve většině případů. Nicméně operace, které obsahují výrazy typu `dynamic` nevyřešených nebo typ zaškrtnutí kompilátorem. Čas spuštění kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci. Jako součást procesu proměnné typu `dynamic` jsou kompilovány do proměnné typu `object`. Proto zadejte `dynamic` existuje pouze v době kompilace, ne za běhu.

V následujícím příkladu se liší od proměnné typu `dynamic` na proměnnou typu `object`. Ověření typu každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy. Technologie IntelliSense zobrazuje **dynamické** pro `dyn` a **objekt** pro `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

`WriteLine` Příkazy zobrazuje typy za běhu `dyn` a `obj`. V tomto okamžiku mají stejný typ celé číslo. Následující výstup je vytvořen:

`System.Int32`

`System.Int32`

Pokud chcete zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi prohlášení a `WriteLine` příkazů v předchozím příkladu.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Chyba kompilátoru hlášené pro pokus o přidání celého čísla a objekt ve výrazu `obj + 3`. Však žádná chybová zpráva pro `dyn + 3`. Výraz, který obsahuje `dyn` nepovolenou v době kompilace, protože typ `dyn` je `dynamic`.

## <a name="context"></a>Kontext

`dynamic` – Klíčové slovo se může objevit přímo, nebo jako součást sady konstruovaný typ v následujících situacích:

- V deklaracích jako typ vlastnosti, pole, indexovací člen, parametr návratová hodnota místní proměnné nebo omezení typu. Následující třídy definice používá `dynamic` v několika různých deklaracích.

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- V explicitní převody typu, jako cílový typ převodu.

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- V libovolném kontextu, ve kterém se typy sloužit jako hodnoty, například na pravé straně `is` operátor nebo `as` operátor nebo jako argument `typeof` konstruovaný typ v rámci. Například `dynamic` lze použít v těchto výrazů.

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a>Příklad

Následující příklad používá `dynamic` v několika deklarace. `Main` Metoda se také liší od typu v době kompilace kontroly s kontrolu typu za běhu.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

Další informace a příklady najdete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [object](../../../csharp/language-reference/keywords/object.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [as](../../../csharp/language-reference/keywords/as.md)
- [typeof](../../../csharp/language-reference/keywords/typeof.md)
- [Postupy: Bezpečné přetypování pomocí porovnávání vzorů, jako například operátorů a is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Návod: Vytváření a používání dynamických objektů](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
