---
title: 'Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 837a94f716c87a1671b5577f8a21a520d4314ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668065"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (C#)
Výraz XPath umožňuje najít sjednocení výsledky ze dvou možných cest umístění XPath.  
  
 Výraz XPath je:  
  
 `//Category|//Price`  
  
 Můžete dosáhnout stejných výsledků pomocí <xref:System.Linq.Enumerable.Concat%2A> standardní operátor dotazu.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá všechny `Category` elementy a všechny `Price` elementy a zřetězí do jedné kolekce. Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazování volání <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> řazení výsledků. Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
