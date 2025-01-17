---
title: 'Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje definice schématu XML'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 9b2cd67a1c4f30e6fe246124be5b8f7081c539a6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392860"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje definice schématu XML
Nástroj definici schématu XML (Xsd.exe) slouží ke generování schématu XML, která popisuje třídu nebo ke generování třídy definované ve schématu XML. Následující postupy ukazují, jak provádět tyto operace.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Chcete-li generovat třídy, které odpovídají určité schéma  
  
1. Otevřete příkazový řádek.  
  
2. Předejte schématu XML jako argument nástroj definici schématu XML, který vytvoří sadu tříd, které budou přesně odpovídat schématu XML, například:  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     Nástroj lze zpracovat pouze schémata, které odkazují na specifikaci World Wide Web Consortium XML ze dne 16. Jinými slovy obor názvů schématu XML musí být "http://www.w3.org/2001/XMLSchema", jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3. Upravte tříd pomocí metody, vlastnosti nebo pole, podle potřeby. Další informace o úpravách třídy s atributy naleznete v tématu [řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) a [atributů, které řídí serializaci kódovaných SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Často je užitečné si prohlédnout schématu XML datový proud, který je generována, když jsou serializovat instance třídy (nebo třídy). Například může publikovat vaše schéma ostatním uživatelům, nebo vám může porovnat s schématu, ke které se snaží dosáhnout shody.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Generovat dokument XML schématu ze sady tříd  
  
1. Zkompilujte třídu nebo třídy do knihovny DLL.  
  
2. Otevřete příkazový řádek.  
  
3. Předejte knihovny DLL jako argument Xsd.exe, například:  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     Schéma (nebo schémata), bude napsán, počínaje název "schema0.xsd".  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataSet>
- [Nástroj pro definici schématu XML a serializace XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Nástroj XML Schema Definition (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Postupy: Serializace objektu @ no__t-0
- [Postupy: Deserializace objektu @ no__t-0
