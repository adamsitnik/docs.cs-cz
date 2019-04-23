---
title: Tipy pro zvýšení výkonu rozhraní .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c825ccc15ff7eeb736169f7ae120b4a3692ffe39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216467"
---
# <a name="net-performance-tips"></a>Tipy pro zvýšení výkonu rozhraní .NET
Termín *výkonu* obecně označuje rychlost vykonávání programu. Někdy můžete zvýšit rychlost provádění dodržováním určitých základních pravidel ve zdrojovém kódu. V některých aplikacích je třeba pečlivě zkoumat kód a ujistěte se, že běží tak rychle za pomocí profilerů. V jiných programech není nutné provést takovou optimalizaci, protože je kód spuštěn přijatelně rychle při zápisu. Tento článek uvádí některé běžné oblasti, kde může být výkon negativně a tipy pro zlepšení ji taky odkazy na další témata výkonu. Další informace o plánování a měření výkonu najdete v tématu [výkonu](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení  
 Je nejvhodnější hodnot typů v situacích, kdy musí být Častokrát zabaleny časů, například v obecné kolekce tříd, jako <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Zabalení typů hodnot se můžete vyhnout použitím obecných kolekcí <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Zabalení a rozbalení jsou výpočetně náročné procesy. Když je typ hodnoty v poli, je nutné vytvořit zcela nový objekt. Může to trvat až 20krát déle než jednoduché přidělení odkazu. Při rozbalení přetypování proces může trvat čtyřikrát co nejdelší přiřazení. Další informace najdete v tématu [zabalení a rozbalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Řetězce  
 Při zřetězení velkého počtu proměnných řetězce například v těsné smyčce použijte <xref:System.Text.StringBuilder?displayProperty=nameWithType> místo C# [+ – operátor](~/docs/csharp/language-reference/operators/addition-operator.md) nebo Visual Basic [operátory zřetězení](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Další informace najdete v tématu [jak: Řetězení více řetězců](../../csharp/how-to/concatenate-multiple-strings.md) a [operátory řetězení v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Prázdné destruktory se nesmí používat. Pokud třída obsahuje destruktor, je vytvořena položka ve frontě dokončit. Pokud je volán destruktor, je vyvolána systému uvolňování paměti ke zpracování fronty. Pokud je destruktor prázdný, jednoduše vede ke ztrátě výkonu. Další informace najdete v tématu [destruktory](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) a [doba života objektu: Způsob vytváření a zničení objektů](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Další zdroje  
  
-   [Rychlejší psaní spravovaného kódu: Vědět, kolik věci stojí](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Vytváření vysoce výkonné spravované aplikace: A Primer](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Základní informace o uvolňování paměti a typech výkonu](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Tipy ke zvýšení výkonu a tipy v aplikacích .NET](https://go.microsoft.com/fwlink/?LinkId=99297)  

-   [Výkon Tidbits pro Rico Mariani](https://go.microsoft.com/fwlink/?LinkId=115679)  

-   [Blog daňové Morrison](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Viz také:

- [Výkon](../../../docs/framework/performance/index.md)
- [Průvodce programováním v jazyce Visual Basic](../../visual-basic/programming-guide/index.md)
- [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)
