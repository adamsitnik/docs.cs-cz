---
title: Transformace dat pomocí LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 8dd57a43f814d7e41ec74af3eeb6d797fef41c9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418623"
---
# <a name="data-transformations-with-linq-c"></a>Transformace dat pomocí LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] není pouze o načítání dat. Je to také výkonný nástroj pro transformaci dat. Pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ho dotazu můžete jako vstup použít zdrojovou sekvenci a upravit ji mnoha způsoby, abyste mohli vytvořit novou výstupní sekvenci. Samotnou sekvenci můžete změnit, aniž byste museli měnit prvky řazením a seskupením. Ale pravděpodobně nejúčinnější funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů je schopnost vytvářet nové typy. To je dosaženo v klauzuli [Select](../../../language-reference/keywords/select-clause.md) . Můžete například provádět následující úlohy:  
  
- Sloučí více vstupních sekvencí do jedné výstupní sekvence, která má nový typ.  
  
- Vytvořte výstupní sekvence, jejichž prvky se skládají pouze z jedné nebo několika vlastností každého prvku ve zdrojové sekvenci.  
  
- Vytvořte výstupní sekvence, jejichž prvky se skládají z výsledků operací provedených ve zdrojových datech.  
  
- Vytvořte výstupní sekvence v jiném formátu. Můžete například transformovat data z řádků nebo textových souborů SQL do XML.  
  
 Jsou to jenom několik příkladů. Tyto transformace je samozřejmě možné v jednom dotazu zkombinovat různými způsoby. Kromě toho se výstupní sekvence jednoho dotazu dá použít jako vstupní sekvence nového dotazu.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Spojování více vstupů do jedné výstupní sekvence  
 Můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz k vytvoření výstupní sekvence, která obsahuje prvky z více než jedné vstupní sekvence. Následující příklad ukazuje, jak kombinovat dvě datové struktury v paměti, ale stejné zásady lze použít pro kombinování dat z XML nebo SQL nebo datových zdrojů. Předpokládejme následující dva typy tříd:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Následující příklad ukazuje dotaz:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Výběr podmnožiny jednotlivých zdrojových elementů  
 Existují dva hlavní způsoby, jak vybrat podmnožinu každého prvku ve zdrojové sekvenci:  
  
1. Chcete-li vybrat pouze jednoho člena zdrojového prvku, použijte operaci tečka. V následujícím příkladu Předpokládejme, že objekt `Customer` obsahuje několik veřejných vlastností včetně řetězce s názvem `City`. Při spuštění tento dotaz vytvoří výstupní sekvenci řetězců.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Chcete-li vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového elementu, můžete použít inicializátor objektu s pojmenovaným objektem nebo anonymním typem. Následující příklad ukazuje použití anonymního typu k zapouzdření dvou vlastností z každého prvku `Customer`:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Další informace naleznete v tématu [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformace objektů v paměti do jazyka XML  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy usnadňují transformaci dat mezi datovými strukturami v paměti, databázemi SQL, ADO.NET datasadami a datovými proudy XML nebo dokumenty. Následující příklad transformuje objekty v datové struktuře v paměti do elementů XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kód generuje následující výstup XML:  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Další informace naleznete v tématu [vytváření stromů XML v C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Provádění operací se zdrojovými elementy  
 Výstupní sekvence nemusí obsahovat žádné elementy nebo vlastnosti elementu ze zdrojové sekvence. Výstupem může být například sekvence hodnot, které jsou vypočítány pomocí zdrojového prvku jako vstupní argumenty. Následující jednoduchý dotaz, když je proveden, výstupuje sekvenci řetězců, jejichž hodnoty reprezentují výpočet na základě zdrojové sekvence prvků typu `double`.  
  
> [!NOTE]
> Volání metod ve výrazech dotazů není podporováno, pokud bude dotaz přeložen do jiné domény. Například nemůžete volat běžnou C# metodu v [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], protože pro ni SQL Server nemá kontext. Uložené procedury však lze namapovat na metody a volat je. Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Viz také:

- [Dotaz integrovaný na jazyku (LINQ)C#()](./index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](./linq-to-xml-overview.md)
- [Výrazy dotazů LINQ](../../../linq/index.md)
- [select – klauzule](../../../language-reference/keywords/select-clause.md)
