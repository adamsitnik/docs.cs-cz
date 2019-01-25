---
title: Vlastnost osy nástupce XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 3b8d13e606f28896cae88162d572470e49af3739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730279"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="2f2a7-102">Vlastnost osy nástupce XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f2a7-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="2f2a7-103">Poskytuje přístup k následníky z následujících akcí: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f2a7-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="2f2a7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2f2a7-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="2f2a7-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-106">Required.</span></span> <span data-ttu-id="2f2a7-107"><xref:System.Xml.Linq.XElement> Objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="2f2a7-108">...<</span><span class="sxs-lookup"><span data-stu-id="2f2a7-108">...<</span></span>  
 <span data-ttu-id="2f2a7-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-109">Required.</span></span> <span data-ttu-id="2f2a7-110">Označuje začátek vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="2f2a7-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-111">Required.</span></span> <span data-ttu-id="2f2a7-112">Název podřízených uzlů pro přístup k ve tvaru [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="2f2a7-113">Část</span><span class="sxs-lookup"><span data-stu-id="2f2a7-113">Part</span></span>|<span data-ttu-id="2f2a7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2f2a7-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="2f2a7-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-115">Optional.</span></span> <span data-ttu-id="2f2a7-116">Předpona oboru názvů XML pro uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="2f2a7-117">Musí být globální obor názvů XML, který je definován s použitím `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="2f2a7-118">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-118">Required.</span></span> <span data-ttu-id="2f2a7-119">Místní název uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-119">Local name of the descendant node.</span></span> <span data-ttu-id="2f2a7-120">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2f2a7-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="2f2a7-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-121">Required.</span></span> <span data-ttu-id="2f2a7-122">Označuje konec vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f2a7-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f2a7-123">Return Value</span></span>  
 <span data-ttu-id="2f2a7-124">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f2a7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f2a7-125">Remarks</span></span>  
 <span data-ttu-id="2f2a7-126">Můžete použít vlastnost osy nástupce XML pro přístup k následnickým uzlů podle názvu ze <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="2f2a7-127">Použít XML `Value` pro přístup k hodnotě první uzel potomka v kolekci vrácené vlastností.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="2f2a7-128">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="2f2a7-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="2f2a7-129">Kompilátor jazyka Visual Basic převede vlastnosti osy nástupce na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="2f2a7-130">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="2f2a7-130">XML Namespaces</span></span>  
 <span data-ttu-id="2f2a7-131">Název v vlastnost Následnické osy můžete použít pouze obory názvů XML globálně deklarované s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="2f2a7-132">Místně deklarované v rámci elementu literály XML obory názvů XML nemůže používat.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="2f2a7-133">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2f2a7-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f2a7-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f2a7-134">Example</span></span>  
 <span data-ttu-id="2f2a7-135">Následující příklad ukazuje, jak přistupovat k hodnotě prvního následníky uzel s názvem `name` a hodnoty všech podřízených uzlů s názvem `phone` z `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="2f2a7-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="2f2a7-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="2f2a7-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f2a7-137">Example</span></span>  
 <span data-ttu-id="2f2a7-138">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="2f2a7-139">Poté použije předponu oboru názvů k vytvoření literálu XML a přistupovat k hodnotě první podřízený uzel s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="2f2a7-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="2f2a7-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="2f2a7-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f2a7-141">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2f2a7-142">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="2f2a7-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="2f2a7-143">Literály XML</span><span class="sxs-lookup"><span data-stu-id="2f2a7-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="2f2a7-144">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f2a7-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2f2a7-145">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="2f2a7-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
