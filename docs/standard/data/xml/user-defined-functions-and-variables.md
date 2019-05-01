---
title: Uživatelem definované funkce a proměnné
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2ce474dac44de1ac72811ecd3bc294ba57ce40a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952019"
---
# <a name="user-defined-functions-and-variables"></a>Uživatelem definované funkce a proměnné
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které se používají k interakci s <xref:System.Xml.XPath.XPathDocument> data. Standardní funkce XPath můžete doplnit prostřednictvím implementace rozšíření funkce a proměnné pro použití ve výrazech dotazů XPath. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda může přijímat kontext uživatelem definované odvozený od <xref:System.Xml.Xsl.XsltContext>. Uživatelem definované funkce jsou vyřešené prostřednictvím vlastní místní.  
  
 Rozšíření funkcí a proměnných, může být užitečné při prevenci útoků prostřednictvím injektáže XML. V těchto scénářích uživatelský vstup je přiřazená vlastní proměnné a zpracovat pomocí funkcí rozšíření, nikoli jako vstup nezpracovaných dat, které jsou spojeny s instrukce pro zpracování. Rozšíření funkcí a proměnných obsahují uživatelský vstup, aby funguje jen na XML data tak, jak má návrhářem.  
  
 Použití rozšíření implementovat vlastní <xref:System.Xml.Xsl.XsltContext> třídy společně s rozhraní <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable> , které podporují funkce rozšíření a proměnné. <xref:System.Xml.XPath.XPathExpression> Přidá vstupu uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> vlastního <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Představuje kompilované dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracování uzly identifikovaný výraz.  
  
 Následující příklad ukazuje implementaci vlastní místní třídy odvozené z <xref:System.Xml.Xsl.XsltContext>. Komentáře v kódu popisují členy třídy a jejich použití v vlastní funkce. Implementace funkce a proměnné a ukázkové aplikace, která používá tyto implementace postupujte podle tohoto segmentu kódu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Třída, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> rozpozná a spustí uživatelem definované funkce. Tento příklad používá funkci identifikovaný deklarace: `private int CountChar(string title, char charTocount)`.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Tato třída překládá odkazy na uživatelské proměnné ve výrazech dotazů XPath v době běhu. Instance této třídy se vytvoří a vrátí přepsané <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda vlastní <xref:System.Xml.Xsl.XsltContext> třídy.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 S předchozí definice tříd v oboru, následující kód používá vlastní funkce k počítání znaků v elementech `Tasks.xml` dokumentu. Komentáře v kódu popisují kód, který zkompiluje vlastní funkce a spustí ho proti `Tasks.xml` dokumentu.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Tento příklad používá následující data XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
