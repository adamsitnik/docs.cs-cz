---
title: Vstup XmlDataDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5c2fb203a1a6975d2b30e47528b15a9005a2583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916021"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Vstup XmlDataDocument do XslTransform
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework implementuje XML model DOM (Document Object Model) (DOM) pro poskytnutí přístupu k datům v dokumentech XML a dalších tříd pro čtení, zápis a navigaci v dokumentech XML. Rozhraní <xref:System.Xml.XmlDataDocument>, které se nachází <xref:System.Xml> v oboru názvů, poskytuje relační přístup k datům s možností synchronizace s relačními daty v <xref:System.Data.DataSet>. Strukturovaný kód XML lze současně zobrazit a manipulovat prostřednictvím relační reprezentace <xref:System.Data.DataSet> nebo manipulovat s částečně strukturovaným kódem XML prostřednictvím reprezentace <xref:System.Xml.XmlDataDocument>modelu DOM. <xref:System.Xml.XmlDataDocument> Proto překračuje hranice XML a relační světů.  
  
 Pokud jsou data uložena v relační struktuře a chcete, aby byla vložena do transformace XSLT, můžete načítat relační data do <xref:System.Data.DataSet> a přidružit je <xref:System.Xml.XmlDataDocument>k. Vstupní hodnoty, <xref:System.Xml.XmlDataDocument> jsou<xref:System.Xml.XPath.IXPathNavigable> implementovány v rozhraní prostřednictvím rozhraní. <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XPath.XPathNavigator> Když narazíte na relační data, načteme je do <xref:System.Data.DataSet>a pomocí synchronizace <xref:System.Xml.XmlDataDocument>v rámci, v relačních datech teď můžou být provedené transformace XSLT.  
  
 Další informace o použití transformace na relační data naleznete v tématu [použití transformace XSLT na datovou sadu](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDataDocument>
- [Synchronizace datové sady a datového dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
