---
title: Dotazy na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ec4ee345835294499f7ac9f665a9b79e2efc0f64
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504664"
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazy na datové sady (LINQ to DataSet)
Po <xref:System.Data.DataSet> objekt naplněné daty, můžete začít ho dotazování. Formulování dotazy pomocí jazyka LINQ k datové sadě je podobný používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti jiné [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]– povolené zdroje. Nezapomeňte však, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty namísto výčet vlastního typu. To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy. Umožňuje vytvořit bohatě vybaveným a komplexní dotazy.  
  
 Stejně jako v jiných implementacích [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvoření LINQ to DataSet dotazy ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody. Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazů založených na volání metody k provedení dotazů na jedné tabulky v <xref:System.Data.DataSet>, proti více tabulek v <xref:System.Data.DataSet>, nebo na tabulky v typovaného <xref:System.Data.DataSet>.  
  
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
