---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7db1b0fe3d4b884bca2c2b00cc95c0872bfa7e7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61958896"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Ověření schématu XML (XSD) s třídou XmlSchemaSet
Dokumenty XML můžete ověřit proti schématu jazyk (XSD) definice schématu XML v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Ověření XML dokumenty  
 Dokumenty XML je ověřen <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy. K ověření dokumentu XML, vytvoření <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schéma jazyka (XSD) definice schématu XML pomocí kterého se má ověřit dokument XML.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Obor názvů obsahuje rozšiřující metody, které usnadňují ověřit stromu XML proti souboru XSD, při použití [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Další informace o ověřování dokumentů XML pomocí LINQ to XML, naleznete v tématu [jak: Ověření pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [jak: Ověření pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Jednotlivé schématu nebo sadu schémat (jako <xref:System.Xml.Schema.XmlSchemaSet>) lze přidat do <xref:System.Xml.Schema.XmlSchemaSet> předáním jednu jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet>. Všimněte si, že při ověřování dokumentu, musí odpovídat oboru názvů cílového dokumentu cílový obor názvů schématu v sadě schémat.  
  
 Následuje příklad dokumentu XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Následuje schéma, které ověří ukázkový dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 V následujícím příkladu kódu, přidá se výše uvedeného schématu do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings> Objekt je předán jako parametr, který se <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objektu, který ověřuje výše uvedeného dokumentu XML.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Vlastnost <xref:System.Xml.XmlReaderSettings> je nastaven na `Schema` k vynucení ověřování dokumentu XML pomocí <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objektu. A <xref:System.Xml.Schema.ValidationEventHandler> se přidá do <xref:System.Xml.XmlReaderSettings> objekt zpracována <xref:System.Xml.Schema.XmlSeverityType.Warning> nebo <xref:System.Xml.Schema.XmlSeverityType.Error> události vyvolané službou chyby zjištěné při procesu ověřování dokumentu XML a schéma.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
