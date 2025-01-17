---
title: Předběžná Atomace objektů XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591492"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Předběžná Atomace objektů XName (LINQ to XML) (C#)
Jedním ze způsobů, jak zlepšit výkon v LINQ to XML, je atomizovat <xref:System.Xml.Linq.XName> objekty. Před vytvořením stromu XML pomocí konstruktorů <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> tříd a <xref:System.Xml.Linq.XAttribute> se před vytvořením stromu XML přiřadí řetězec k objektu. Místo předání řetězce konstruktoru, který by použil implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaný <xref:System.Xml.Linq.XName> objekt.  
  
 To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se konkrétní názvy opakují. Chcete-li to provést, deklarujete <xref:System.Xml.Linq.XName> a inicializujete objekty před vytvořením stromu XML a pak <xref:System.Xml.Linq.XName> použijte objekty namísto zadávání řetězců pro element a názvy atributů. Tato technika může přinést výrazné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.  
  
 Před tím, než se rozhodnete, jestli ho chcete použít, byste měli testovat předběžnou atomaci ve svém scénáři.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje to.  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Následující příklad ukazuje stejnou techniku, kde je dokument XML v oboru názvů:  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Následující příklad se podobá tomu, co se vám pravděpodobně setkáte v reálném světě. V tomto příkladu je obsah elementu dodán dotazem:  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 Předchozí příklad provede lepší, než následující příklad, ve kterém názvy nejsou předběžně atomované:  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a>Viz také:

- [Atomované XName a objekty XNamespace (LINQ to XML) (C#)](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
