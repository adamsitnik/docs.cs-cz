---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f51a657135d9e22d960743b428057e13c1b23804
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590367"
---
# <a name="outputs-from-an-xsltransform"></a>Výstupy z XslTransform
Protože šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atributu, jsou popsány v následující tabulce je formát výstupu, kdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a je výstupní formát deklarovat jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Protože šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atributu, jsou popsány v následující tabulce je formát výstupu, kdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a je výstupní formát deklarovat jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>. Následující tabulka popisuje, co se stane, když není deklarována typem výstupu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda ve spojení s použitím `<xsl:output>` – příkaz:  
  
|\<Metoda elementu xsl: Output = > atribut|Výsledný formát|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Text|  
  
> [!NOTE]
>  Poznámka: `<xsl:output>` Příkaz je ignorován při výstupu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.  
  
 Jsou podporovány následující atributy při <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupu metody je <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:  
  
- encoding*  
  
- omit-xml-declaration  
  
- samostatný  
  
- doctype-public  
  
- doctype-system  
  
- cdata-section-elements  
  
- Odsazení  
  
    > [!NOTE]
    >  * kódování atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> odesílá svůj výstup do metody <xref:System.IO.TextWriter>. Vlastnost kódování na <xref:System.IO.TextWriter> místo ní se použije.  
  
 Tento atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupu metody je <xref:System.IO.Stream>:  
  
- verze: verze je vždy 1.0  
  
- typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální uvozovací znaky  
 `<xsl:text disable-output-escaping>` Značka se používá k označení, zda musí být do formuláře XML uvozeny řídicími znaky speciální znaky (například pomocí `<&lt>` místo `"<"` symbol) nebo left ve přítomna podmínka. `disable-output-escaping` Atribut se ignoruje při transformování do <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektů a nemá žádný vliv na speciální znaky.  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
