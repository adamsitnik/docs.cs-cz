---
title: Dotazy v technologii LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 52f48fcacd6fbd92e4fd0531c5e1fa3577496941
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738479"
---
# <a name="queries-in-linq-to-entities"></a>Dotazy v technologii LINQ to Entities
Dotaz je výraz, který načítá data ze zdroje dat. Dotazy jsou obvykle vyjádřené ve specializovaném dotazovacím jazyce, jako je SQL pro relační databáze a XQuery pro XML. Proto se vývojářům musel naučit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který dotazuje. LINQ (Language-Integrated Query) nabízí jednodušší a konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. V dotazu LINQ vždy pracujete s programováním objektů.  
  
 Operace dotazu LINQ se skládá ze tří akcí: získat zdroje dat nebo zdroje, vytvořit dotaz a spustit dotaz.  
  
 Zdroje dat, které implementují obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> obecné rozhraní, se dají dotazovat prostřednictvím LINQ. Instance obecné <xref:System.Data.Objects.ObjectQuery%601> třídy, které implementují obecné rozhraní <xref:System.Linq.IQueryable%601>, slouží jako zdroj dat pro LINQ to Entities dotazy. <xref:System.Data.Objects.ObjectQuery%601> obecná třída reprezentuje dotaz, který vrací kolekci nula nebo více typových objektů. Můžete také nechat kompilátor odvodit typ entity pomocí C# klíčového slova `var` (Dim in Visual Basic).  
  
 V dotazu zadáte přesně informace, které chcete načíst ze zdroje dat. Dotaz může také určit, jak se mají tyto informace seřadit, seskupit a tvarovat před tím, než se vrátí. V LINQ je dotaz uložen v proměnné. Pokud dotaz vrátí sekvenci hodnot, musí být proměnná dotazu typu Queryable. Tato proměnná dotazu neprovádí žádnou akci a nevrátí žádná data. ukládá pouze informace o dotazu. Po vytvoření dotazu musíte spustit dotaz, aby se načetla nějaká data.  
  
## <a name="query-syntax"></a>Syntaxe dotazu  
 Dotazy LINQ to Entities můžou být složené ve dvou různých syntaxech: syntax výrazů dotazů a syntaxe dotazů založených na metodách. Syntaxe výrazu dotazu je nová v C# 3,0 a Visual Basic 9,0 a skládá se ze sady klauzulí napsané v deklarativní syntaxi podobně jako Transact-SQL nebo XQuery. .NET Framework Common Language Runtime (CLR) ale nemůže přečíst samotný syntax výrazu dotazu. Proto v době kompilace jsou výrazy dotazu přeloženy na něco, co aplikace CLR rozumí: volání metody. Tyto metody jsou známé jako *standardní operátory dotazu*. Jako vývojář máte možnost je volat přímo pomocí syntaxe metody namísto použití syntaxe dotazu. Další informace naleznete v tématu [syntaxe dotazu a syntaxe metody v jazyce LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazů jsou deklarativní syntaxí dotazu. Tato syntaxe umožňuje vývojářům psát dotazy v jazyce vysoké úrovně, který je formátován podobný jazyku Transact-SQL. Pomocí syntaxe výrazu dotazu můžete provádět i složité filtrování, řazení a seskupování operací se zdroji dat s minimálním kódem. Další informace najdete v [základních operacích dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Příklady, které ukazují, jak použít syntaxi výrazu dotazu, najdete v následujících tématech:  
  
- [Příklady syntaxe výrazů dotazů: Projekce](query-expression-syntax-examples-projection.md)  
  
- [Příklady syntaxe výrazů dotazů: Filtrování](query-expression-syntax-examples-filtering.md)  
  
- [Příklady syntaxe výrazů dotazů: Řazení](query-expression-syntax-examples-ordering.md)  
  
- [Příklady syntaxe výrazů dotazů: Agregační operátory](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Dělení](query-expression-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory spojení](query-expression-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory elementů](query-expression-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Seskupení](query-expression-syntax-examples-grouping.md)  
  
- [Příklady syntaxe výrazů dotazů: Navigace v relacích](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazů založená na metodách  
 Dalším způsobem, jak vytvářet dotazy LINQ to Entities, je použití dotazů založených na metodách. Syntaxe dotazu založená na metodách je sekvence volání přímých metod operátorů LINQ a předávání výrazů lambda jako parametrů. Další informace naleznete v tématu [lambda výrazy](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Příklady, které ukazují, jak použít syntaxi založenou na metodách, najdete v následujících tématech:  
  
- [Příklady syntaxe dotazů založených na volání metody: Projekce](method-based-query-syntax-examples-projection.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Filtrování](method-based-query-syntax-examples-filtering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Řazení](method-based-query-syntax-examples-ordering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Agregační operátory](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Dělení](method-based-query-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Převod](method-based-query-syntax-examples-conversion.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory spojení](method-based-query-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory elementů](method-based-query-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Seskupení](method-based-query-syntax-examples-grouping.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Navigace v relacích](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Entities](linq-to-entities.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Začínáme pomocí LINQ v Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Entity Framework možnosti sloučení a zkompilované dotazy](https://go.microsoft.com/fwlink/?LinkId=199591)
