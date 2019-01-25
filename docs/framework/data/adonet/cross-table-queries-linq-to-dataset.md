---
title: Dotazy na křížovou tabulku (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 117043a461779dee19f1c99361c44a33f5904993
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583519"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Dotazy na křížovou tabulku (LINQ to DataSet)
Kromě dotazování jedné tabulky, můžete také provádět dotazy na křížovou tabulku v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. To se provádí pomocí *spojení*. Je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat, jako je například produkt nebo se obraťte na ID spojení Vztahy mezi objekty v objektově orientované programování, jsou relativně snadno vyhledávat, protože každý objekt má člena, který odkazuje na jiný objekt. V tabulkách externí databáze ale navigace v relacích není tak přímočaré. Databázové tabulky neobsahují integrované vztahy. V těchto případech můžete použít operace spojení tak, aby odpovídaly prvky z každého zdroje. Například s ohledem dvou tabulek, které obsahují informace o produktu a informace o prodeji, můžete použít operaci join tak, aby odpovídaly informace o prodeji a produktů pro stejnou prodejní objednávku.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework obsahuje dva operátory, spojení <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto operátory provádějí *operátorem*: to znamená, spojení, které odpovídají do dvou datových zdrojů, pouze při jejich klíče rovnají. (Oproti tomu [!INCLUDE[tsql](../../../../includes/tsql-md.md)] podporuje operátory spojení jiné než `equals`, například `less than` operátor.)  
  
 Relační databáze řečeno <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřního spojení. Vnitřní spojení je typ spojení v které se vrátí pouze ty objekty, které mají shoda v opačné datové sady.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operátory nemají žádný přímý ekvivalent v relační databázi podmínky; implementují nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí všechny prvky objektu první kolekce (vlevo), i když nemá žádné korelační prvky v druhé kolekci.  
  
 Další informace o spojení najdete v tématu [operace Join](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí tradiční spojení `SalesOrderHeader` a `SalesOrderDetail` tabulek z ukázkové databáze AdventureWorks získat online objednávky v srpnu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Viz také:
- [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Dotazy na jednu tabulku](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Operace sjednocení](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)
- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
