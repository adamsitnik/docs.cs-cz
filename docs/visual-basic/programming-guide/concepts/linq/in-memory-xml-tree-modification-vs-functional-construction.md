---
title: Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 5b43d28390927fa1426f914fa6fd88a1a5d00b9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613610"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (Visual Basic)
Změna stromu XML v místě je tradiční přístup na měnící tvar dokumentu XML. Typická aplikace načte dokument do úložiště dat, jako je například modelu DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní pro vložení uzlů, odstraňovat uzly nebo změnit obsah uzlů a pak uloží do souboru XML nebo přenáší přes síť.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Další možností, které jsou užitečné v mnoha scénářích umožňuje *: funkční konstrukce*. Funkční konstrukce zpracovává změny dat, jako problém transformace, nikoli jako podrobné manipulaci s úložištěm dat. Pokud můžete vzít vyjádření data a transformovali je efektivní z jednoho formuláře do jiného, výsledek je stejný, jako by trvalo jednoho úložiště dat a manipulovat nějakým způsobem provést jiný tvar. Klíč k přístupu funkční konstrukce je předat výsledky dotazů pro <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> konstruktory.  
  
 V mnoha případech můžete napsat kód transformace, jehož za zlomek času, který by to obnášelo k práci s úložišti dat a tento kód je robustní a jednodušší správu. V těchto případech i v případě, že transformace, jehož přístupu může trvat více výpočetního výkonu, je efektivnější způsob, jak upravovat data. Pokud vývojář zkušenosti s funkční přístup, je výsledný kód v mnoha případech lze snáze pochopit. Je snadné kód, který upravuje jednotlivých součástí stromu.  
  
 Místo, kde upravíte XML stromu místní přístup je více do hloubky na mnoho programátorů modelu DOM, zatímco kód napsané s využitím funkční přístup může být nevypadá to povědomě pro vývojáře, kteří ještě nerozumí tento přístup. Pokud je nutné provést pouze malé změny do velké stromu XML, přístup místo, kde upravíte stromu je v mnoha případech bude trvat méně času procesoru.  
  
 V tomto tématu poskytuje příklad, který implementuje pomocí obou metod.  
  
## <a name="transforming-attributes-into-elements"></a>Transformace atributů na prvky  
 V tomto příkladu předpokládejme, že chcete změnit následující jednoduchý dokument XML tak, aby atributy stát elementů. Toto téma představuje první přístup tradiční místní úpravy. Potom zobrazí funkční konstrukce přístup.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Změna stromu XML  
 Můžete napsat kód procedury k vytváření prvků z atributů a atributů, odstraňte následujícím způsobem:  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Funkční konstrukce přístup  
 Naopak funkční přístup se skládá z kódu k vytvoření nové větve, výběru a Výběr elementů a atributů ze stromu zdrojového kódu a transformují je podle potřeby, jako jsou přidány do nového stromu. Funkční přístup vypadá takto:  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 V tomto příkladu vrátí stejné XML jako v prvním příkladu. Všimněte si však, že vidíte ve skutečnosti výsledný struktura nový kód XML v funkční přístup. Můžete zobrazit vytvořením `Root` elementu, kód, který si vyžádá `Child1` element ze stromu zdrojového kódu a kód, který transformuje atributy ze stromu zdrojového kódu na prvky do nového stromu.  
  
 Funkční příklad v tomto případě není žádná kratší než v prvním příkladu, a není ve skutečnosti jednodušší. Nicméně pokud máte mnoho změn tak, aby stromu XML nefunkční přístup se stanou poměrně složité a trochu obtuse. Naopak při použití funkční přístup, stále pouze formulář požadované XML vkládat dotazy a výrazy podle potřeby, aby se načetla požadovaný obsah. Funkční přístup poskytuje kód, který je snazší Údržba.  
  
 Všimněte si, že v tomto případě funkční přístup pravděpodobně nebude provádět úplně stejně přístup zpracování stromu. Hlavní problém je, že vytvoří funkční přístup více krátký povahy objekty. Výměnou za to však je efektivní jeden, pokud pomocí funkční přístup umožňuje vyšší produktivita programátorů.  
  
 To je velmi jednoduchý příklad, ale funguje zobrazíte filozofie rozdíl mezi dvěma přístupy. Funkční přístup poskytuje větší zvýšení produktivity pro transformaci větší dokumentů XML.  
  
## <a name="see-also"></a>Viz také:

- [Změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
