---
title: Navigace oboru názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6facc047d87c503313015eff4e869861cd6b301
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957003"
---
# <a name="xpath-namespace-navigation"></a>Navigace oboru názvů XPath
Chcete-li používat dotazy XPath s dokumenty XML, je nutné správně adresovat obory názvů XML a prvky obsažené v oborech názvů. Obory názvů zabraňují nejednoznačnosti, ke kterým může dojít, když se názvy používají ve více než jednom kontextu. například název `ID` může odkazovat na více než jeden identifikátor přidružený k různým prvkům dokumentu XML. Syntaxe oboru názvů určuje identifikátory URI, názvy a předpony, které odlišují prvky dokumentu XML.  
  
 Příklad v tomto tématu ukazuje použití předpon v navigaci dokumentu XML s <xref:System.Xml.XPath.XPathNavigator>. Další informace o oborech názvů a syntaxi naleznete v tématu [soubory XML: porozumění oborům názvů XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).  
  
## <a name="namespace-declarations"></a>Deklarace oboru názvů  
 Deklarace oboru názvů umožňují, aby prvky dokumentu XML byly rozlišené a adresovatelné při použití instance <xref:System.Xml.XPath.XPathNavigator>. Předpony oboru názvů poskytují stručnou syntaxi pro adresování oborů názvů.  
  
 Předpony jsou definovány ve formě: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxi je prefixem "`e`" zkratka pro formální identifikátor URI oboru názvů. Element `Body` můžete identifikovat jako člen oboru názvů `Envelope` pomocí syntaxe: `e:Body`.  
  
 Následující dokument XML bude v navigačním příkladu v následující části odkazován jako `response.xml`.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Navigace podle předpony oboru názvů  
 Kód v této části používá @no__t objekty-0 a <xref:System.Xml.XmlNamespaceManager> k výběru prvku `Search` z dokumentu XML v předchozí části. Dotaz `xpath` zahrnuje předpony oboru názvů pro každý prvek v cestě. Určení přesné identity oborů názvů, které obsahují jednotlivé prvky, zajišťuje správné procházení prvku `Search` metodou <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +   
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 Přesnost plně kvalifikovaného oboru názvů a názvů je větší než pohodlí. Trochu experimentování s definicí dokumentu a kódem v předchozích příkladech ověří, zda navigace bez úplných názvů prvků vyvolá výjimky. Například definice elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">` a dotaz: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez předpony oboru názvů na elementu `Search` vrátí `null` namísto prvku `Search`.  
  
## <a name="see-also"></a>Viz také:

- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
