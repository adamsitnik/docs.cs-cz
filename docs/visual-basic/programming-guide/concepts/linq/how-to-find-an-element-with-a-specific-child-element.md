---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 4df2f8f55a516665c02d12c3bdf6569601db30c2
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249915"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Postupy: Vyhledání elementu s konkrétním podřízeným elementem (Visual Basic)
Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.  
  
## <a name="example"></a>Příklad  
 Příklad vyhledá prvek `Test`, který má podřízený element `CommandLine` s hodnotou "Examp2. EXE".  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
0002  
0006  
```  
  
 Všimněte si, že v tomto příkladu je použita [vlastnost podřízená osa XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)a [vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: konfigurace testu v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a>Související témata

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
