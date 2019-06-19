---
title: Vstup XmlDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c80cb772f280c064e420e83a99b5f7ce41fe05e3
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170821"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="f9520-102">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="f9520-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="f9520-103"><xref:System.Xml.XmlDocument> Třída poskytuje možnosti úprav pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="f9520-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="f9520-104">Pokud XML se musí upravit nebo změnit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody načtení XML do <xref:System.Xml.XmlDocument>, upravit ji a odeslat ho do <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="f9520-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9520-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f9520-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="f9520-106">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="f9520-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f9520-107">Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="f9520-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f9520-108"><xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, tak může být předán dokumentu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda po dokončení úprav.</span><span class="sxs-lookup"><span data-stu-id="f9520-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="f9520-109">Z důvodu úprav schopnost <xref:System.Xml.XmlDocument>s použitím <xref:System.Xml.XmlDocument> třídy jako vstup pro transformaci je nižší než při použití <xref:System.Xml.XPath.XPathDocument> pro rozšiřitelné jazyk šablony stylů transformace XSLT () transformaci jako <xref:System.Xml.XPath.XPathDocument> je optimalizované pro dotazy jazyk XML Path (XPath) z důvodu interní úložiště.</span><span class="sxs-lookup"><span data-stu-id="f9520-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9520-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9520-110">Example</span></span>  
 <span data-ttu-id="f9520-111">Následující příklad kódu ukazuje jak <xref:System.Xml.XmlDocument> mohou být poskytnuty <xref:System.Xml.Xsl.XslTransform>, s výstupem odesílat <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="f9520-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9520-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9520-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="f9520-113">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="f9520-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="f9520-114">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="f9520-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="f9520-115">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="f9520-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="f9520-116">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="f9520-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="f9520-117">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="f9520-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="f9520-118">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="f9520-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
