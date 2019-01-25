---
title: Vložené výrazy v XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: c02b6ea0895d8b22ac71d0cb3ea6950861de47df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678756"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="c9db6-102">Vložené výrazy v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9db6-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="c9db6-103">Vložené výrazy umožňují vytváření literálů XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c9db6-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="c9db6-104">Syntaxe pro vložený výraz je `<%=` `expression` `%>`, která je stejná jako syntaxe používané [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9db6-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="c9db6-105">Například můžete vytvořit XML element literál, kombinování vložené výrazy s obsahem prostý text.</span><span class="sxs-lookup"><span data-stu-id="c9db6-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="c9db6-106">Pokud `isbnNumber` obsahuje celé číslo 12345 a `modifiedDate` obsahuje datum 3/5/2006, když tento kód se vykoná, hodnota `book` je:</span><span class="sxs-lookup"><span data-stu-id="c9db6-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="c9db6-107">Vložený výraz umístění a ověřování</span><span class="sxs-lookup"><span data-stu-id="c9db6-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="c9db6-108">Vložené výrazy se může zobrazit jenom na určité umístění v rámci výrazů literálu XML.</span><span class="sxs-lookup"><span data-stu-id="c9db6-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="c9db6-109">Ovládací prvky výraz umístění, které typy výraz se můžete vrátit a jak `Nothing` se zpracovává.</span><span class="sxs-lookup"><span data-stu-id="c9db6-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="c9db6-110">Následující tabulka popisuje povolených umístění a typy vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="c9db6-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="c9db6-111">Umístění v literálu</span><span class="sxs-lookup"><span data-stu-id="c9db6-111">Location in literal</span></span>|<span data-ttu-id="c9db6-112">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="c9db6-112">Type of expression</span></span>|<span data-ttu-id="c9db6-113">Zpracování `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c9db6-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="c9db6-114">Název elementu XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="c9db6-115">Chyba</span><span class="sxs-lookup"><span data-stu-id="c9db6-115">Error</span></span>|  
|<span data-ttu-id="c9db6-116">Obsah elementu XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-116">XML element content</span></span>|<span data-ttu-id="c9db6-117">`Object` nebo pole `Object`</span><span class="sxs-lookup"><span data-stu-id="c9db6-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="c9db6-118">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="c9db6-118">Ignored</span></span>|  
|<span data-ttu-id="c9db6-119">Název atributu XML element</span><span class="sxs-lookup"><span data-stu-id="c9db6-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="c9db6-120">Chyba, pokud hodnota atributu je také `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c9db6-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="c9db6-121">Hodnota atributu XML element</span><span class="sxs-lookup"><span data-stu-id="c9db6-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="c9db6-122">Atribut deklarace se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="c9db6-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="c9db6-123">Atribut – element XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-123">XML element attribute</span></span>|<span data-ttu-id="c9db6-124"><xref:System.Xml.Linq.XAttribute> nebo kolekce <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="c9db6-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="c9db6-125">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="c9db6-125">Ignored</span></span>|  
|<span data-ttu-id="c9db6-126">Kořenový element dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-126">XML document root element</span></span>|<span data-ttu-id="c9db6-127"><xref:System.Xml.Linq.XElement> kolekce jednoho nebo <xref:System.Xml.Linq.XElement> objektu a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty</span><span class="sxs-lookup"><span data-stu-id="c9db6-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="c9db6-128">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="c9db6-128">Ignored</span></span>|  
  
-   <span data-ttu-id="c9db6-129">Příklad vložený výraz v název elementu XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="c9db6-130">Příklad vložený výraz v obsahu prvku XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="c9db6-131">Příklad vložený výraz v atributu název elementu XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="c9db6-132">Příklad vložený výraz v hodnotě atributu – element XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="c9db6-133">Příklad vložený výraz v atributu – element XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="c9db6-134">Příklad vložený výraz v kořenový element dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="c9db6-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="c9db6-135">Pokud povolíte `Option Strict`, kompilátor kontroluje, že na požadovaný typ rozšiřuje typ každý vložený výraz.</span><span class="sxs-lookup"><span data-stu-id="c9db6-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="c9db6-136">Jedinou výjimkou je pro kořenový element dokumentu XML, který je ověřen při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="c9db6-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="c9db6-137">Pokud kompilujete bez `Option Strict`, můžete vložit výrazy typu `Object` a jejich typ je ověřený v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c9db6-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="c9db6-138">V umístění, kde je volitelné, obsah vložené výrazy, které obsahují `Nothing` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="c9db6-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="c9db6-139">To znamená, že není potřeba zkontrolovat obsah elementu hodnoty atributů a prvky pole nejsou `Nothing` před použitím literál XML.</span><span class="sxs-lookup"><span data-stu-id="c9db6-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="c9db6-140">Požadované hodnoty, jako jsou názvy prvků a atributů nemůžou být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c9db6-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="c9db6-141">Další informace o použití vloženého výrazu v konkrétním typu literál najdete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c9db6-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="c9db6-142">Pravidla vytváření oborů</span><span class="sxs-lookup"><span data-stu-id="c9db6-142">Scoping Rules</span></span>  
 <span data-ttu-id="c9db6-143">Kompilátor převede každý literál XML volání konstruktoru pro příslušný typ literálu.</span><span class="sxs-lookup"><span data-stu-id="c9db6-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="c9db6-144">Literálový obsah a vložené výrazy v literálu XML jsou předány jako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c9db6-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="c9db6-145">To znamená, že všechny dostupné pro literál XML programovací prvky jazyka Visual Basic jsou také k dispozici pro jeho vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="c9db6-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="c9db6-146">V rámci literál XML, můžete přístup k oboru názvů XML předpony deklarována s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c9db6-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="c9db6-147">Můžete deklarovat novou předponu oboru názvů XML nebo předponu existujícího oboru názvů XML v elementu s použitím stínové `xmlns` atribut.</span><span class="sxs-lookup"><span data-stu-id="c9db6-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="c9db6-148">Nový obor názvů je k dispozici do podřízených uzlů daného prvku, ale ne do literálů XML ve vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="c9db6-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9db6-149">Pokud deklarujete předponu oboru názvů XML s použitím `xmlns` atribut oboru názvů, hodnota atributu musí být konstanty typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="c9db6-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="c9db6-150">V tomto ohledu pomocí `xmlns` atribut je například `Imports` příkaz deklarujte obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="c9db6-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="c9db6-151">Chcete-li určit hodnotu oboru názvů XML nelze použít vložený výraz.</span><span class="sxs-lookup"><span data-stu-id="c9db6-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9db6-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9db6-152">See also</span></span>
- [<span data-ttu-id="c9db6-153">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9db6-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="c9db6-154">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="c9db6-155">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="c9db6-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="c9db6-156">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="c9db6-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c9db6-157">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="c9db6-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c9db6-158">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="c9db6-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
