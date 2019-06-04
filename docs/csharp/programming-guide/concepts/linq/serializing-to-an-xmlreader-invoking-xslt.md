---
title: Serializace do třídy XmlReader (vyvolání XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487190"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="3e0d3-102">Serializace do třídy XmlReader (vyvolání XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e0d3-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="3e0d3-103">Při použití <xref:System.Xml?displayProperty=nameWithType> funkce interoperability [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> k vytvoření <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3e0d3-104">Modul, který čte z tohoto <xref:System.Xml.XmlReader> přečte uzlů ze stromu XML a zpracovává je odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="3e0d3-105">Vyvolání transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="3e0d3-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="3e0d3-106">Jedním z využití pro tuto metodu je při vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="3e0d3-107">Můžete vytvořit stromu XML, vytvořit <xref:System.Xml.XmlReader> ze stromu XML vytvoříte nový textový dokument a pak vytvořte <xref:System.Xml.XmlWriter> k zápisu do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="3e0d3-108">Potom můžete vyvolat transformace XSLT, při předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="3e0d3-109">Po úspěšném dokončení transformace stromu XML nové naplněný výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="3e0d3-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="3e0d3-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3e0d3-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e0d3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e0d3-111">See also</span></span>

- [<span data-ttu-id="3e0d3-112">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3e0d3-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
