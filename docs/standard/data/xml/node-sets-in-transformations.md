---
title: Sady uzlů v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbcd9b93f63d48229c174b0f6518fd0150e98e18
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957035"
---
# <a name="node-sets-in-transformations"></a>Sady uzlů v transformacích
Sady uzlů jsou jedním ze čtyř základních datových typů, které jsou vráceny ze výrazů jazyka XML Path (XPath). Sada uzlů, což je neuspořádaná kolekce uzlů bez duplicit, vytvořená v pořadí dokumentů, může být přiřazena proměnné v šabloně stylů.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci XSLT pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform>. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Sady uzlů jsou jedním ze čtyř základních datových typů, které jsou vráceny ze výrazů XPath. Sada uzlů, což je neuspořádaná kolekce uzlů bez duplicit, vytvořená v pořadí dokumentů, může být přiřazena proměnné v šabloně stylů. Tato sada uzlů, která je výsledkem výrazu XPath použitého v atributu `select` v transformaci, má stejné chování jako sada uzlů z XML model DOM (Document Object Model) (DOM). Můžete procházet sadu uzlů pomocí sady metod, které jsou zobrazeny v [uzlu sada uzlů navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), na rozdíl od fragmentu stromu výsledku nebo fragmentu stromu výsledků, který používá <xref:System.Xml.XPath.XPathNodeIterator> pro navigaci.  
  
 Následující ukázka kódu ukazuje, jak iterovat v rámci sady uzlů, když je prvek `variable` nebo `parameter` v šabloně stylů vyhodnocen jako sada uzlů.  
  
## <a name="style-sheet"></a>Šablona stylů  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Vstup  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Výstup  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
