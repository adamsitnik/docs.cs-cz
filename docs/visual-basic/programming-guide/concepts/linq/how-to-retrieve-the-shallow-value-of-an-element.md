---
title: 'Postupy: načtení omezené hodnoty elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 184186a92865b022118b9989633a97c75274e7f4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320437"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>Postupy: načtení omezené hodnoty elementu (Visual Basic)

Toto téma ukazuje, jak získat omezené hodnoty elementu. Nedávná hodnota je hodnota pouze konkrétního prvku, na rozdíl od hloubkové hodnoty, která zahrnuje hodnoty všech podřízených prvků zřetězených do jednoho řetězce.

Při načítání hodnoty prvku pomocí přetypování nebo vlastnosti <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> načtete hloubkovou hodnotu. K načtení omezené hodnoty můžete použít rozšiřující metodu `ShallowValue`, jak je znázorněno v následujícím příkladu. Načtení omezené hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.

V následujícím příkladu je deklarována metoda rozšíření, která načte s nejomezeným hodnotou elementu. Potom používá metodu rozšíření v dotazu k vypsání všech prvků, které obsahují počítanou hodnotu.

## <a name="example"></a>Příklad

Následující textový soubor, Report. XML, je zdrojem tohoto příkladu.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

Tento příklad vytvoří následující výstup:

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
