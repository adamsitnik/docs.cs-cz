---
title: Otázky LINQ (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 659e3ba02367feee4539a984b679173ee4544d17
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894313"
---
# <a name="linq-considerations-wcf-data-services"></a>Otázky LINQ (WCF Data Services)
Toto téma poskytuje informace o způsobu, jakým se dotazy LINQ skládají a provádějí při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta a omezení použití LINQ k dotazování datové služby, která implementuje rozhraní. [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Další informace o sestavování a spouštění dotazů [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]na základě datové služby založené na službě najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Vytváření dotazů LINQ  
 LINQ umožňuje vytvářet dotazy proti kolekci objektů, které implementují <xref:System.Collections.Generic.IEnumerable%601>. Dialogové okno **Přidat odkaz na službu** v aplikaci Visual Studio a nástroj DataSvcUtil. exe slouží k vygenerování reprezentace [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby jako třídy kontejneru entit, ze <xref:System.Data.Services.Client.DataServiceContext>které dědí, a také objektů, které představují entity vracené v informačních kanálech Tyto nástroje také generují vlastnosti třídy kontejneru entit pro kolekce, které jsou zpřístupněny jako informační kanály služby. Každá z těchto vlastností třídy, která zapouzdřuje datovou službu, vrátí <xref:System.Data.Services.Client.DataServiceQuery%601>. Vzhledem k tomu, že <xref:System.Linq.IQueryable%601> TřídaimplementujerozhranídefinovanétechnologiíLINQ,můžetevytvořitdotazLINQnainformačníkanályvystavenédatovouslužbou,kteréjsoupřeloženyklientskouknihovnounaidentifikátorURIžádostiodotaz,kterýjeodeslándodatovéslužbyna<xref:System.Data.Services.Client.DataServiceQuery%601> realizaci.  
  
> [!IMPORTANT]
> Sada dotazů vyhodnotit v syntaxi LINQ je širší než ty, které jsou povoleny v syntaxi identifikátoru URI používané [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] datovými službami. <xref:System.NotSupportedException> Je vyvolána, když dotaz nelze namapovat na identifikátor URI v cílové datové službě. Další informace naleznete v tématu [nepodporované metody LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) v tomto tématu.  
  
 Následující příklad je dotaz LINQ, který vrací `Orders` náklady na dopravné více než $30 a seřadí výsledky podle data expedice počínaje nejnovějším datem expedice:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Tento dotaz LINQ se převede na následující identifikátor URI dotazu, který se spustí pro službu [rychlého](quickstart-wcf-data-services.md) startu dat založenou na Northwind:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Obecnější informace o technologii LINQ naleznete v tématu [Language-Integrated Query (LINQ) C# ](../../../csharp/programming-guide/concepts/linq/index.md) nebo [LINQ (Language-Integrated Query)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ umožňuje vytvářet dotazy pomocí deklarativní syntaxe dotazu specifické pro jazyk, jak je znázorněno v předchozím příkladu, a také sadu metod dotazů označovaných jako standardní operátory dotazu. Ekvivalentní dotaz na předchozí příklad lze sestavit pouze pomocí syntaxe založené na metodě, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient je schopen přeložit oba druhy složených dotazů do identifikátoru URI dotazu a můžete roztáhnout dotaz LINQ připojením metod dotazu do výrazu dotazu. Při vytváření dotazů LINQ přidáním syntaxe metody do výrazu dotazu nebo <xref:System.Data.Services.Client.DataServiceQuery%601>dojde k přidání operací do identifikátoru URI dotazu v pořadí, ve kterém jsou metody volány. To je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody pro přidání jednotlivých možností dotazu k identifikátoru URI dotazu.  
  
## <a name="executing-linq-queries"></a>Provádění dotazů LINQ  
 Některé metody dotazů LINQ, jako <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> je například nebo <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, při připojení k dotazu, způsobují spuštění dotazu. Dotaz je také proveden při implicitním vyčíslení výsledků, například během `foreach` smyčky nebo při přiřazení dotazu `List` do kolekce. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
 Klient spustí dotaz LINQ ve dvou částech. Kdykoliv je to možné, výrazy LINQ v dotazu se nejprve vyhodnotí na klientovi a pak se vygeneruje dotaz založený na identifikátorech URI a pošle se do datové služby pro vyhodnocení dat ve službě. Další informace najdete v části [klient porovnání se serverem](querying-the-data-service-wcf-data-services.md#executingQueries) při [dotazování na datovou službu](querying-the-data-service-wcf-data-services.md).  
  
 Pokud dotaz LINQ nelze přeložit v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]identifikátoru URI dotazu, který je kompatibilní, je vyvolána výjimka při pokusu o provedení. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Příklady dotazů LINQ  
 Příklady v následujících částech ukazují typy dotazů LINQ, které mohou být provedeny proti [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] službě.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrování  
 Příklady dotazů LINQ v této části filtrují data v informačním kanálu vrácené službou.  
  
 V následujících příkladech jsou ekvivalentní dotazy, které filtrují vrácené `Orders` entity, aby byly vráceny pouze objednávky s náklady na dopravení větší než $30:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]     
  
- Použití metod dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]       
  
- Možnost řetězce `$filter` dotazu identifikátoru URI:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Všechny předchozí příklady jsou přeloženy na identifikátor URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Řazení  
 Následující příklady znázorňují ekvivalentní dotazy, které řadí vracená data podle názvu společnosti i poštovního kódu, sestupné:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]        
  
- Použití metod dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]        
  
- Možnost řetězce `$orderby` dotazu identifikátoru URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Všechny předchozí příklady jsou přeloženy na identifikátor URI dotazu: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projekce  
 Následující příklady znázorňují ekvivalentní dotazy, které Project vrátil data do užšího `CustomerAddress` typu:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]         
  
- Použití metod dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]         

> [!NOTE]
> Možnost dotazu nelze přidat k identifikátoru URI dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pomocí metody. `$select` Doporučujeme použít metodu LINQ <xref:System.Linq.Enumerable.Select%2A> , pokud má klient `$select` generovat možnost dotazu v identifikátoru URI požadavku.  
  
 Oba předchozí příklady jsou přeloženy na identifikátor URI dotazu: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Stránkování klienta  
 Následující příklady znázorňují ekvivalentní dotazy, které požadují stránku seřazených objednávek, které obsahují 25 objednávek, přeskočí prvních 50 objednávek:  
  
- Použití metod dotazů na dotaz LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]     
  
- Řetězec `$skip` a`$top` možnosti dotazu identifikátoru URI:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Oba předchozí příklady jsou přeloženy na identifikátor URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 Když se dotazuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] na datovou službu, můžete požádat o to, aby entity související s entitou, které cílí na dotaz, zahrnovaly vrácený kanál. Metoda je volána <xref:System.Data.Services.Client.DataServiceQuery%601> v pro sadu entit, která je cílem dotazu LINQ, spolu s názvem `path` sady entit, která je zadána jako parametr. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).  
  
 Následující příklady ukazují ekvivalentní způsoby použití <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody v dotazu:  
  
- V syntaxi dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- Pomocí metod dotazů LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]       

 Oba předchozí příklady jsou přeloženy na identifikátor URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Nepodporované metody LINQ  
 Následující tabulka obsahuje třídy metod LINQ nejsou podporovány a nelze je zahrnout do dotazu spuštěného [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] na službu:  
  
|Typ operace|Nepodporovaná – metoda|  
|--------------------|------------------------|  
|Nastavit operátory|Všechny nastavené operátory nejsou u typu <xref:System.Data.Services.Client.DataServiceQuery%601>, který obsahuje následující:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operátory řazení|Následující operátory řazení, které vyžadují <xref:System.Collections.Generic.IComparer%601> , nejsou podporovány <xref:System.Data.Services.Client.DataServiceQuery%601>proti:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Operátory projekce a filtrování|Následující operátory projekce a filtrování, které přijímají poziční argument, nejsou podporovány proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operátory seskupení|Všechny operátory seskupení nejsou u typu <xref:System.Data.Services.Client.DataServiceQuery%601>"nepodporované", včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operace seskupení se musí provádět na klientovi.|  
|Agregační operátory|Všechny agregované operace nejsou u typu <xref:System.Data.Services.Client.DataServiceQuery%601>, včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Agregační operace musí být provedeny buď na klientovi, nebo musí být zapouzdřeny operací služby.|  
|Operátory stránkování|Následující operátory stránkování nejsou podporovány proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A>**Poznámka:**  Operátory stránkování, které jsou spuštěny v prázdné sekvenci, vrací hodnotu null.|  
|Jiné operátory|Následující jiné operátory nejsou podporovány pro <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Podporované funkce výrazu  
 Následující metody a vlastnosti modulu CLR (Common Language Runtime) jsou podporovány, protože je lze přeložit ve výrazu dotazu pro zahrnutí do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby v identifikátoru URI požadavku na službu:  
  
|<xref:System.String>Člen|Podporovaná [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime>Člen<sup>1</sup>|Podporovaná [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup> Jsou podporovány také ekvivalentní vlastnosti <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> data a času a také metoda v Visual Basic.  
  
|<xref:System.Math>Člen|Podporovaná [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Člen|Podporovaná [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient může být také schopný vyhodnotit další funkce CLR na straně klienta. <xref:System.NotSupportedException> Je vyvolána pro libovolný výraz, který nelze vyhodnotit na straně klienta a nelze ho přeložit na platný identifikátor URI žádosti pro vyhodnocení na serveru.  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Projekce dotazů](query-projections-wcf-data-services.md)
- [Materializace objektů](object-materialization-wcf-data-services.md)
- [OData: Konvence identifikátoru URI](https://go.microsoft.com/fwlink/?LinkID=185564)
