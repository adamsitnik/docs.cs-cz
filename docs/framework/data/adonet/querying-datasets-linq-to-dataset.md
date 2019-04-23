---
title: Dotazy na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: a1c316811ce08141999bcec4c9c8504f86c2e285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165240"
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazy na datové sady (LINQ to DataSet)
Po <xref:System.Data.DataSet> objekt naplněné daty, můžete začít ho dotazování. Formulování dotazů s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] podobá se to používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti jiné [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]– povolené zdroje. Nezapomeňte však, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty namísto výčet vlastního typu. To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy. Umožňuje vytvořit bohatě vybaveným a komplexní dotazy.  
  
 Stejně jako v jiných implementacích [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvořit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody. Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazů založených na volání metody k provedení dotazů na jedné tabulky v <xref:System.Data.DataSet>, proti více tabulek v <xref:System.Data.DataSet>, nebo na tabulky v typovaného <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy na jednu tabulku](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na jednu tabulku.  
  
 [Dotazy na křížovou tabulku](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na křížovou tabulku.  
  
 [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Popisuje, jak provádět dotazy zadali <xref:System.Data.DataSet> objekty.  
  
## <a name="see-also"></a>Viz také:

- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
