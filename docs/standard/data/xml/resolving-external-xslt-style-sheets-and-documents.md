---
title: Překlad externích šablon stylů a dokumentů XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e956b96b27898e2cad4bed30996622ab0b86656
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170307"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Překlad externích šablon stylů a dokumentů XSLT
Existují několikrát během transformace, kdy budete muset vyřešit externím prostředkům.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework 2.0. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 Existují několikrát během transformace, když budete muset vyřešit externí prostředky:  
  
- Během <xref:System.Xml.Xsl.XslTransform.Load%2A> najít externí šabloně stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyřešit některé `<xsl:include>` nebo `<xsl:import>` prvky najít v šabloně stylů.  
  
- Během <xref:System.Xml.Xsl.XslTransform.Transform%2A> vyřešit některé `document()` funkce.  
  
## <a name="using-the-xmlresolver-class"></a>Pomocí třídy objekt XmlResolver  
 Pokud pro přístup k síťovému prostředku se vyžaduje ověření, použijte <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které mají <xref:System.Xml.XmlResolver> parametr předat <xref:System.Xml.XmlResolver> objektu, který obsahuje vlastnosti potřebné přihlašovací údaje nastavené.  
  
 Pokud máte vlastní <xref:System.Xml.XmlResolver> , že chcete použít, nebo pokud je potřeba zadat jiná pověření, následující tabulka uvádí úlohou, v závislosti na tom, kdy externí prostředek potřebuje řešení.  
  
|Jaký proces vyžaduje řešení|Nutná úloha|  
|--------------------------------------|-------------------|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> najít šablony stylů.|Zadat přetížené <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přebírá jako parametr, <xref:System.Xml.XmlResolver> Pokud šablona stylů je na prostředek, který vyžaduje přihlašovací údaje.|  
|Během <xref:System.Xml.Xsl.XslTransform.Load%2A> vyřešit `<xsl:include>` nebo `<xsl:import>`.|Zadat přetížené <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu, která přebírá jako parametr, <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů, odkazuje `import` nebo `include` příkazy. Pokud předáte v `null`, nejsou přeložit externí prostředky.|  
|Při transformaci vyřešit některé `document()` funkce.|Zadejte <xref:System.Xml.XmlResolver> při transformaci pomocí <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, která přebírá <xref:System.Xml.XmlResolver> argument.|  
  
 `document()` Funkce načte další materiály XML z šablony stylů, dále na počáteční data XML poskytnuté vstupního datového proudu. Protože tato funkce umožňuje zahrnutí dat XML, který může být umístěn jinde, <xref:System.Xml.XmlResolver> s `null` hodnota zadaná pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda zabraňuje `document()` funkce spuštění. Pokud chcete použít `document()` funkci, použijte <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, která přebírá <xref:System.Xml.XmlResolver> jako parametr, kromě nutnosti příslušná oprávnění nastavena.  
  
 Další informace o <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda a jeho použití <xref:System.Xml.XmlResolver>, naleznete v tématu <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je volána, oprávnění se počítají proti důkazu v okamžiku načtení a, která je přiřazena proces transformace celou sadu oprávnění. Pokud `document()` funkce se pokusí provést akci, která vyžaduje oprávnění nebyla nalezena v množině, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Transformace XSLT v různých úložištích](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [XsltArgumentList pro parametry šablon stylů a objektů rozšíření](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Šablona stylů XSLT skriptování pomocí \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [Podpora pro funkci msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
