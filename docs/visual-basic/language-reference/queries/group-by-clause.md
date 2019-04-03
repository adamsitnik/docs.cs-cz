---
title: Group By – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 71e0ffc7f03a27a878aeb48eda9fbc58e5faae82
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839870"
---
# <a name="group-by-clause-visual-basic"></a>Group By – klauzule (Visual Basic)
Seskupuje prvky sady výsledků dotazu. Můžete také použít k aplikaci agregačních funkcí na každou skupinu. Operace seskupení je založená na jeden nebo více klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Součásti  
  
-   `listField1`, `listField2`  
  
     Volitelné. Jedno nebo více polí proměnné dotazu nebo proměnné, které explicitně určete pole, které mají být zahrnuty ve výsledku seskupené. Pokud nebyla určena žádná pole, všechna pole, proměnná dotazu nebo proměnné jsou zahrnuty ve výsledku seskupené.  
  
-   `keyExp1`  
  
     Povinný parametr. Výraz, který určuje klíč pro použití k určení skupiny prvků. Můžete zadat více než jeden klíč k určení složený klíč.  
  
-   `keyExp2`  
  
     Volitelné. Jeden nebo více dalších klíčů, které jsou spojené s `keyExp1` vytvoření složeného klíče.  
  
-   `aggregateList`  
  
     Povinný parametr. Jeden nebo více výrazů, které určují, jak se agregují skupiny. Chcete-li zjistit název člena pro seskupené výsledky, použijte `Group` – klíčové slovo, které může být v některém z následujících forem:  
  
    ```  
    Into Group  
    ```  
  
     -nebo-  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Může také obsahovat agregační funkce, které chcete aplikovat ve skupině.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Group By` klauzule přerušení výsledků dotazu do skupin. Seskupení podle klíče nebo složený klíč skládající se z více klíčů. Prvky, které jsou spojeny s odpovídající hodnoty klíče jsou součástí stejné skupiny.  
  
 Můžete použít `aggregateList` parametr `Into` klauzule a `Group` – klíčové slovo k identifikaci názvu členu, který se používá k odkazování skupiny. Můžete použít také v agregačních funkcí `Into` klauzule k výpočtu hodnot seskupených elementů. Seznam standardní agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu seskupí seznam zákazníků na základě jejich umístění (a případně zemi) a poskytuje počet zákazníků v každé skupině. Výsledky jsou seřazené podle názvu země. Seskupené výsledky jsou řazeny podle název města.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
