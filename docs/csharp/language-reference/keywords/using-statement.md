---
title: pomocí příkazu - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 9569b04e4d4f7bfca90390bfd803cdd02b3f3632
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244593"
---
# <a name="using-statement-c-reference"></a>using – příkaz (Referenční dokumentace jazyka C#)
Poskytuje pohodlné syntaxe, který zajistí správné použití <xref:System.IDisposable> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `using` příkazu.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IO.File> a <xref:System.Drawing.Font> jsou příkladem spravované typy, které přístup k nespravovaným prostředkům (v této obslužné rutiny souborů případu a kontexty zařízení). Existuje mnoho dalších typů nespravované prostředky a typy v knihovně tříd, které provádí zapouzdření je. Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.  
  
Když životnosti `IDisposable` objektu je omezen na jedinou metodu, musí deklarovat a vytvoření instance v `using` příkaz. `using` Příkaz volá <xref:System.IDisposable.Dispose%2A> metodu na objekt správným způsobem a (pokud ji používáte jak je uvedeno výše) navíc způsobí, že objekt samotný dostaly mimo obor co nejdříve <xref:System.IDisposable.Dispose%2A> je volána. V rámci `using` blok, objekt je jen pro čtení a nelze upravovat nebo znovu přiřazen.  
  
 `using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> se nazývá i v případě, že dojde k výjimce v rámci `using` bloku. Můžete stejného výsledku dosáhnout vložení objektu uvnitř `try` bloku a následným voláním <xref:System.IDisposable.Dispose%2A> v `finally` blokovat; ve skutečnosti je to způsob, jak `using` příkaz je přeložen kompilátorem. Příklad kódu se dříve rozbalí v následujícím kódu v době kompilace (Všimněte si velmi složené závorky do vytvořit omezený obor pro objekt):  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 Další informace o `try` - `finally` prohlášení, najdete v článku [try-finally](try-finally.md) tématu.
  
 Více instancí typu mohou být deklarovány v `using` příkaz, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` příkazu, ale to není nejvhodnější. V takovém případě po ponechá ovládacího prvku `using` blokovat, objekt zůstane v oboru, ale pravděpodobně nemá přístup k jeho nespravovaných prostředků. Jinými slovy je inicializován není plně zobrazovat. Pokud se pokusíte použít objekt mimo `using` blokovat, riziko způsobuje vyvolání výjimky. Z tohoto důvodu je obecně lepší pro vytvoření instance objektu na `using` příkazu a omezit její obor `using` bloku.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Další informace o uvolnění `IDisposable` objekty, najdete [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md)  
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)  
- [Použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md)  
- [Rozhraní IDisposable](xref:System.IDisposable)
