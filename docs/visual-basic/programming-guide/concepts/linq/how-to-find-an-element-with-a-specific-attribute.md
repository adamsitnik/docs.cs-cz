---
title: 'Postupy: Vyhledání elementu s konkrétním atributem (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
ms.openlocfilehash: 615dc9bb4ee9b90c0e7b9ecb86d9342bc688f3b1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710277"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a>Postupy: Vyhledání elementu s konkrétním atributem (Visual Basic)
Toto téma ukazuje, jak najít element, který má atribut, který má konkrétní hodnotu.  
  
## <a name="example"></a>Příklad  
 Příklad ukazuje, jak najít `Address` prvek, který `Type` má atribut s hodnotou "vyúčtování".  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 Tento kód generuje následující výstup:  
  
```xml  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 Všimněte si, že v tomto příkladu je použita [vlastnost podřízená osa XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)a [vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
