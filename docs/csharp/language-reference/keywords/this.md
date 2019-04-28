---
title: Toto klíčové slovo - C# odkaz
ms.custom: seodec18
description: Toto klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: af39ba6e20fb1a7c9e1a356ef5015afd885dbbca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660577"
---
# <a name="this-c-reference"></a>this (Referenční dokumentace jazyka C#)

`this` – Klíčové slovo odkazuje na aktuální instanci třídy a slouží také jako modifikátor první parametr metody rozšíření.

> [!NOTE]
> Tento článek popisuje způsob používání `this` instancemi třídy. Další informace o jeho použití v metodách rozšíření naleznete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

Tady jsou běžné způsoby použití `this`:

- K získání způsobilosti členy skryta podobnými názvy, například:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- K předání objektu jako parametr do jiné metody, například:

  ```csharp
  CalcTax(this);
  ```

- Chcete-li deklarovat indexery, například:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statické členské funkce, protože existují na úrovni třídy, nikoli jako součást objektu, není nutné `this` ukazatele. Jedná se o chybu k odkazování na `this` uvnitř statické metody.

## <a name="example"></a>Příklad

V tomto příkladu `this` se použijí pro kvalifikaci `Employee` členy, třídy `name` a `alias`, které jsou skryté, podobně jako názvy. Používá se také k objektu předat metodě `CalcTax`, který patří do jiné třídy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
