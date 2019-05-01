---
title: Funkční transformace XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 62edd7adf425f8a36128497a6dae445a3e9cbfc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968477"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Funkční transformace XML (Visual Basic)
Toto téma popisuje čistě funkční transformace přístup k úpravě XML dokumenty a liší se od procedurálního přístupu.  
  
## <a name="modifying-an-xml-document"></a>Úpravy dokumentu XML  
 Jeden z nejčastějších úloh pro programátor XML je transformace XML z jednoho obrazce na jiný. Tvar dokument XML je struktura dokument, který zahrnuje následující:  
  
- Hierarchie vyjádřený v dokumentu.  
  
- Názvy prvků a atributů.  
  
- Datové typy elementů a atributů.  
  
 Obecně platí největší efektivity dosáhnete, přístup k transformaci XML z jednoho obrazce na jiný je čistě funkční transformace. V takovém případě se má úloha primární programátor vytvoření transformace, která se použije pro celý dokument XML (nebo na jeden nebo více uzly striktně definované). Funkční transformace je pravděpodobně nejsnadněji kódu (po programátor zkušenosti s přístupem), poskytuje nejvíc udržovatelného kódu a je často více než přístupy komprimovat.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční transformace, jehož technologie XML  
 Společnost Microsoft nabízí dvě technologie funkční transformace pro použití v dokumentech XML: XSLT a LINQ to XML. XSLT se podporuje v <xref:System.Xml.Xsl> spravované obor názvů a v nativní implementaci modelu COM MSXML. I když XSLT je robustní technologie pro manipulaci s XML dokumenty, vyžaduje znalosti týkající se specializované domény, a to jazyka XSLT a jeho podpůrné rozhraní API.  
  
 Technologie LINQ to XML poskytuje nástroje potřebné k čistě funkčním transformacím kód výkonná a výrazová způsobem, v rámci kódu C# nebo Visual Basic. Například mnoho příkladů v LINQ k dokumentaci XML pomocí čistě funkční přístup. Také v [kurzu: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu používáme LINQ to XML v funkční přístup k manipulaci s informace v dokumentu aplikace Microsoft Word.  
  
 Podrobnější srovnání technologie LINQ to XML s dalšími technologiemi Microsoftu XML, naleznete v tématu [LINQ to XML versus. Jiné technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT je doporučeným nástrojem pro zaměřené na dokument transformace, když zdrojový dokument má nestandardní strukturu. Však technologie LINQ to XML můžete také provádět transformace zaměřené na dokument. Další informace najdete v tématu [jak: Použití anotací transformace stromů LINQ to XML ve stylu XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Viz také:

- [Úvod k čistě funkčním transformacím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Technologie LINQ to XML versus jiné technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
