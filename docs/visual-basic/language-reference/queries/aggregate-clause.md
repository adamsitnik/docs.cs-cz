---
title: Aggregate – klauzule (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 50a53cd45cc428541c90fbf82089518be2212fae
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004804"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate – klauzule (Visual Basic)
Aplikuje jednu nebo více agregačních funkcí na kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. Proměnná použitá pro iteraci prvků kolekce.|  
|`type`|Volitelné. Typ `element`. Pokud není zadán žádný typ, je typ `element` odvozen z `collection`.|  
|`collection`|Požadováno. Odkazuje na kolekci, na které se má pracovat.|  
|`clause`|Volitelné. Jedna nebo více klauzulí dotazu, jako je například klauzule `Where`, pro upřesnění výsledku dotazu pro použití agregační klauzule nebo klauzule na.|  
|`expressionList`|Požadováno. Jeden nebo více výrazů oddělených čárkami, které identifikují agregační funkci, která se má použít pro kolekci. Můžete použít alias pro agregační funkci a zadat název člena pro výsledek dotazu. Pokud není zadán žádný alias, je použit název agregační funkce. Příklady najdete v části o agregačních funkcích dále v tomto tématu.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzuli `Aggregate` lze použít k zahrnutí agregačních funkcí do dotazů. Agregační funkce provádějí kontroly a výpočty přes sadu hodnot a vracejí jedinou hodnotu. K vypočtené hodnotě můžete přistupovat pomocí členu typu výsledku dotazu. Standardní agregované funkce, které můžete použít, jsou funkce `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min` a `Sum`. Tyto funkce jsou známé vývojářům, kteří jsou obeznámeni s agregacemi v SQL. Jsou popsány v následující části tohoto tématu.  
  
 Výsledek agregační funkce je zahrnut ve výsledku dotazu jako pole typu výsledku dotazu. Můžete zadat alias pro výsledek agregační funkce pro určení názvu člena typu výsledku dotazu, který bude obsahovat agregovanou hodnotu. Pokud není zadán žádný alias, je použit název agregační funkce.  
  
 Klauzule `Aggregate` může spustit dotaz nebo může být do dotazu vložena jako další klauzule. Pokud klauzule `Aggregate` zahájí dotaz, výsledkem je jediná hodnota, která je výsledkem agregační funkce zadané v klauzuli `Into`. Je-li v klauzuli `Into` zadána více než jedna agregační funkce, dotaz vrátí jeden typ s samostatnou vlastností, aby odkazoval na výsledek každé agregační funkce v klauzuli `Into`. Pokud je klauzule `Aggregate` zahrnutá jako další klauzule v dotazu, bude mít typ vrácený v kolekci dotazů samostatnou vlastnost, která bude odkazovat na výsledek každé agregační funkce v klauzuli `Into`.  
  
## <a name="aggregate-functions"></a>Agregační funkce

Níže jsou uvedené standardní agregační funkce, které lze použít s klauzulí `Aggregate`.  
  
### <a name="all"></a>Všechny

Vrátí `true`, pokud všechny prvky v kolekci odpovídají zadané podmínce. v opačném případě vrátí `false`. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Jakýmikoli

Vrátí `true`, pokud kterýkoli prvek v kolekci splňuje zadanou podmínku. v opačném případě vrátí `false`. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Vypočítat

Vypočítá průměr všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Výpočtu

Spočítá počet prvků v kolekci. Můžete zadat volitelný výraz `Boolean`, který bude počítat pouze počet prvků v kolekci, které splní podmínku. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Skupina

Odkazuje na výsledky dotazu, které jsou seskupeny jako výsledek klauzule `Group By` nebo `Group Join`. Funkce `Group` je platná pouze v klauzuli `Into` klauzule `Group By` nebo `Group Join`. Další informace a příklady najdete v tématu [klauzule GROUP by](../../../visual-basic/language-reference/queries/group-by-clause.md) a [Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Spočítá počet prvků v kolekci. Můžete zadat volitelný výraz `Boolean`, který bude počítat pouze počet prvků v kolekci, které splní podmínku. Vrátí výsledek jako `Long`. Příklad naleznete v agregační funkci `Count`.

### <a name="max"></a>Počet

Vypočítá maximální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Dlouhé

Vypočítá minimální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Zapůjčen

Vypočítá součet všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Následuje příklad:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak použít klauzuli `Aggregate` pro použití agregačních funkcí pro výsledek dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Vytváření agregačních funkcí definovaných uživatelem

 Do výrazu dotazu můžete přidat vlastní agregační funkce přidáním rozšiřujících metod do typu <xref:System.Collections.Generic.IEnumerable%601>. Vaše vlastní metoda potom může provést výpočet nebo operaci na vyčíslitelné kolekci, která odkazovala na agregační funkci. Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Například následující příklad ukazuje vlastní agregační funkci, která vypočítá medián hodnoty kolekce čísel. Existují dvě přetížení metody rozšíření `Median`. První přetížení akceptuje jako vstup kolekci typu `IEnumerable(Of Double)`. Pokud je pro pole dotazu typu `Double` volána agregační funkce `Median`, bude volána Tato metoda. Druhé přetížení metody `Median` lze předat všem obecným typům. Obecné přetížení metody `Median` přebírá druhý parametr, který odkazuje na výraz lambda `Func(Of T, Double)`, aby prokáže hodnotu typu (z kolekce) jako odpovídající hodnotu typu `Double`. Poté deleguje výpočet střední hodnoty k druhé přetížení metody `Median`. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 Následující příklad ukazuje Ukázkové dotazy, které volají agregační funkci `Median` pro kolekci typu `Integer` a kolekci typu `Double`. Dotaz, který volá agregační funkci `Median` na kolekci typu `Double` volá přetížení metody `Median`, která přijímá jako vstup, kolekci typu `Double`. Dotaz, který volá agregační funkci `Median` na kolekci typu `Integer` volá obecné přetížení metody `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
