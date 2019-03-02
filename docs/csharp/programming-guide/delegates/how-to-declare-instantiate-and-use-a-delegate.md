---
title: 'Postupy: Deklarování, vytváření instancí a použití delegáta - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7166c27a946fb76c9351647ac6465c151866a2ad
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202558"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Postupy: Deklarování, vytváření instancí a použití delegáta (C# Průvodce programováním v)
V jazyce C# 1.0 nebo novější delegáty lze deklarovat, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C# 2.0 umožňuje jednodušší způsob, jak napsat předchozí prohlášení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 V jazyce C# 2.0 nebo novější, je také možné použít k deklaraci a inicializaci anonymní metoda [delegovat](../../../csharp/language-reference/keywords/delegate.md), jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 V jazyce C# 3.0 nebo novější můžete delegáti také deklarovány a vytvořit instanci pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad ukazuje deklarování, vytváření instancí a použití delegáta. `BookDB` Třída zapouzdří knihkupectví databázi, která udržuje databázi knihy. Zpřístupní metodu, `ProcessPaperbackBooks`, který najde všechny tištěné verze knih v databázi a volání delegáta pro každé z nich. `delegate` Má typ, který se používá název `ProcessBookDelegate`. `Test` Třída používá k vytištění názvy a průměrná cena formátu brožované knih, které tato třída.  
  
 Použití delegátů podporuje dobré oddělení funkcí mezi knihkupectví databáze a klientský kód. Klientský kód je vůbec nezná způsob uložení knih nebo jak knihkupectví kód najde formátu brožované knihy. Kód knihkupectví nemá žádné znalosti z jaké zpracování probíhá ve formátu brožované knihy po nich najde.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   Deklarace delegáta.  
  
     Následující příkaz deklaruje nový typ delegáta.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Každý typ delegáta popisuje počet a typy argumentů a typ vrácené hodnoty metod, které může zapouzdřit. Pokaždé, když je potřeba nová sada typy argumentů nebo typ vrácené hodnoty, musí být deklarován nový typ delegáta.  
  
-   Vytvoření instance delegáta.  
  
     Poté, co je deklarovaný typ delegáta, objektu delegáta musí vytvořit a přidružený k určité metodě. V předchozím příkladu, můžete to provést předáním `PrintTitle` metodu `ProcessPaperbackBooks` metody jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Tím se vytvoří nový objekt delegáta přidružený k [statické](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`. Podobně, nestatické metody `AddBookToTotal` objektu `totaller` je předán jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     V obou případech je předat objekt delegáta `ProcessPaperbackBooks` metody.  
  
     Po vytvoření delegáta metodě je přidružen k nikdy změny. Delegát objekty jsou neměnné.  
  
-   Volání delegáta.  
  
     Po vytvoření objektu delegáta objekt delegáta je obvykle předat jiným kódem, který bude volání delegáta. Objekt delegáta je volána za použití názvu objektu delegáta, za nímž následuje argumenty v závorce má být předán delegáta. Následuje příklad volání delegáta:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Delegát může být buď volat synchronně, jako v následujícím příkladu, nebo asynchronně pomocí `BeginInvoke` a `EndInvoke` metody.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
