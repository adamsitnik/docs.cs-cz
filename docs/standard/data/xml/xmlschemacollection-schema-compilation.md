---
title: XmlSchemaCollection Schema Compilation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40d7ef11dde882d99c21fe541c2689c52a634edf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915941"
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection Schema Compilation
**XmlSchemaCollection** je mezipaměť nebo knihovna, kde mohou být uloženy a ověřeny schémata XML-data redukovaná (XDR) a XML Schema Definition Language (XSD). **XmlSchemaCollection** vylepšuje výkon ukládáním schémat do paměti místo přístupu ze souboru nebo adresy URL.  
  
> [!NOTE]
> I když třída XmlSchemaCollection ukládá schémata XDR i schémata XML, jakákoliv metoda a vlastnost, která přijímá nebo vrací objekt **XmlSchema** , podporuje pouze schémata XML.  
  
> [!IMPORTANT]
> Třída je nyní zastaralá a byla nahrazena <xref:System.Xml.Schema.XmlSchemaSet> třídou. <xref:System.Xml.Schema.XmlSchemaCollection> Další informace o <xref:System.Xml.Schema.XmlSchemaSet> třídě naleznete v tématu Třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Přidání schémat do kolekce  
 Schémata jsou načtena do kolekce pomocí metody **Add** kolekce **XmlSchemaCollection**, v níž je schéma přidruženo k identifikátoru URI oboru názvů. V případě schémat XML bude identifikátor URI oboru názvů obvykle cílovým oborem názvů schématu. V případě schémat XDR je identifikátor URI oboru názvů zadaný při přidání schématu do kolekce.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Vyhledat schéma v kolekci  
 Můžete zjistit, zda je schéma v kolekci, pomocí metody **Contains** . Metoda **Contains** přebírá buď objekt **XmlSchema** (pouze schémata XML), nebo řetězec představující identifikátor URI oboru názvů přidruženého ke schématu (pro schémata XML schémat a XDR).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Načtení schématu z kolekce  
 Schéma můžete z kolekce načíst pomocí vlastnosti **Item** . Vlastnost **Item** přebírá řetězec představující identifikátor URI oboru názvů přidružený ke schématu, obvykle jeho cílový obor názvů a vrací objekt **XmlSchema** . Vlastnost **Item** se vztahuje pouze na schémata XML. Návratová hodnota je vždy nulový odkaz pro schémata XDR, protože nemají k dispozici objektový model.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Ověřování dokumentů XML pomocí XmlSchemacollection  
 Dokument instance XML můžete ověřit pomocí kolekce XmlSchemaCollection vytvořením objektu XmlSchemaCollection , přidáním schémat do kolekce a nastavením vlastnosti schemas v **XmlValidatingReader** na hodnotu Přiřaďte vytvořenou **kolekci XmlSchemaCollection** k **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Vylepšený výkon  
 Doporučuje se, pokud ověřujete více než jeden dokument proti stejnému schématu, že použijete sadu XmlSchemaCollection , protože poskytuje lepší výkon ukládáním schémat do mezipaměti v paměti.  
  
 Následující příklad kódu vytvoří objekt **XmlSchemaCollection** , přidá schémata do kolekce a nastaví vlastnost **schemas** .  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Viz také:

- [Ověření XDR s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [Ověření schématu XML (XSD) s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
