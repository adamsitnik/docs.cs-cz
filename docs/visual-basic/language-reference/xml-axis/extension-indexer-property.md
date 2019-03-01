---
title: Vlastnost indexeru rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 4aa8dd030d95e0404c037b2c8b674463bb51b267
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972539"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="51825-102">Vlastnost indexeru rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51825-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="51825-103">Poskytuje přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="51825-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51825-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="51825-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="51825-105">Parts</span></span>  
  
|<span data-ttu-id="51825-106">Termín</span><span class="sxs-lookup"><span data-stu-id="51825-106">Term</span></span>|<span data-ttu-id="51825-107">Definice</span><span class="sxs-lookup"><span data-stu-id="51825-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="51825-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="51825-108">Required.</span></span> <span data-ttu-id="51825-109">Dotazovatelná kolekce.</span><span class="sxs-lookup"><span data-stu-id="51825-109">A queryable collection.</span></span> <span data-ttu-id="51825-110">To znamená, že kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="51825-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="51825-111">(</span><span class="sxs-lookup"><span data-stu-id="51825-111">(</span></span>|<span data-ttu-id="51825-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="51825-112">Required.</span></span> <span data-ttu-id="51825-113">Označuje začátek vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="51825-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="51825-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="51825-114">Required.</span></span> <span data-ttu-id="51825-115">Celočíselný výraz, který určuje pozice s nulovým základem elementu kolekce.</span><span class="sxs-lookup"><span data-stu-id="51825-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="51825-116">)</span><span class="sxs-lookup"><span data-stu-id="51825-116">)</span></span>|<span data-ttu-id="51825-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="51825-117">Required.</span></span> <span data-ttu-id="51825-118">Označuje konec vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="51825-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="51825-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51825-119">Return Value</span></span>  
 <span data-ttu-id="51825-120">Objekt v zadaném umístění v kolekci, nebo `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="51825-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51825-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51825-121">Remarks</span></span>  
 <span data-ttu-id="51825-122">Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="51825-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="51825-123">Tato vlastnost indexeru se obvykle používá ve výstupu vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="51825-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="51825-124">Podřízené XML a vlastnosti XML podřízené osy vrací kolekce <xref:System.Xml.Linq.XElement> objekty nebo hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="51825-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="51825-125">Kompilátor jazyka Visual Basic převede vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metody.</span><span class="sxs-lookup"><span data-stu-id="51825-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="51825-126">Na rozdíl od pole indexer `ElementAtOrDefault` vrátí metoda `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="51825-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="51825-127">Toto chování je užitečné, když nelze snadno určit počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="51825-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="51825-128">Tato vlastnost indexer je jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, kolekce nemá výchozí vlastnost nebo indexer.</span><span class="sxs-lookup"><span data-stu-id="51825-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="51825-129">Pro přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, můžete použít XML `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="51825-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="51825-130">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="51825-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51825-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="51825-131">Example</span></span>  
 <span data-ttu-id="51825-132">Následující příklad ukazuje, jak používat indexovací modul rozšíření pro přístup k druhý podřízený uzel v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="51825-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="51825-133">Kolekce lze přistupovat pomocí vlastnost podřízené osy, který získá všechny podřízené prvky s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="51825-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="51825-134">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="51825-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="51825-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51825-135">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="51825-136">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="51825-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="51825-137">Literály XML</span><span class="sxs-lookup"><span data-stu-id="51825-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="51825-138">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51825-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="51825-139">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="51825-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
