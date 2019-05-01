---
title: Odvození schémat z dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b4727ead8abb9b3618f8b9dda8f7a9eb4b2321f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968139"
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="68666-102">Odvození schémat z dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="68666-102">Inferring Schemas from XML Documents</span></span>
<span data-ttu-id="68666-103">Toto téma popisuje způsob použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodit jazyk (XSD) schématu definice schématu XML ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="68666-104">Procesu odvození schématu</span><span class="sxs-lookup"><span data-stu-id="68666-104">The Schema Inference Process</span></span>  
 <span data-ttu-id="68666-105"><xref:System.Xml.Schema.XmlSchemaInference> Třídu <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů se používá ke generování jednoho nebo více schémat jazyk (XSD) definice schématu XML ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="68666-106">Vygenerovaný schémata slouží k ověření původního dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="68666-107">Jako XML je zpracován dokumentu <xref:System.Xml.Schema.XmlSchemaInference> třídy, <xref:System.Xml.Schema.XmlSchemaInference> třída provede předpoklady o schéma komponenty, které popisují prvky a atributy v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="68666-108"><xref:System.Xml.Schema.XmlSchemaInference> Třídy také odvodí schéma komponenty omezeným způsobem podle odvození typu nejvíce omezující pro konkrétní elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="68666-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="68666-109">Jak se shromažďují Další informace o dokumentu XML, tato omezení jsou uvolnit podle odvození typů méně omezující.</span><span class="sxs-lookup"><span data-stu-id="68666-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="68666-110">Je nejméně restriktivní typ, který jde odvodit `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="68666-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="68666-111">Vezměme si jako příklad následující část dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 <span data-ttu-id="68666-112">V příkladu výše, kdy `attribute1` zjištěn atribut s hodnotou `6` podle <xref:System.Xml.Schema.XmlSchemaInference> procesu, předpokládá se typ `xs:unsignedByte`.</span><span class="sxs-lookup"><span data-stu-id="68666-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="68666-113">Při druhý `parent` nalezen element podle <xref:System.Xml.Schema.XmlSchemaInference> zpracovat, je tak, že upravíte typ, který chcete uvolnit omezení `xs:string` protože hodnotu `attribute1` je atribut `A`.</span><span class="sxs-lookup"><span data-stu-id="68666-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="68666-114">Podobně `minOccurs` atribut pro všechny `child` odvodit ve schématu elementy jsou uvolnit na `minOccurs="0"` protože druhý nadřazený element neobsahuje žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="68666-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="68666-115">Odvození schémat z dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="68666-115">Inferring Schemas from XML Documents</span></span>  
 <span data-ttu-id="68666-116"><xref:System.Xml.Schema.XmlSchemaInference> Používá třídy, dvě přetížené <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody pro odvození schématu z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="68666-117">První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k vytvoření schématu podle dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="68666-118">Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá pro odvození schématu, který popisuje několik dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="68666-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="68666-119">Například může zadat více dokumentů XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda současně vytvořit schéma, které popisuje celou sadu dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="68666-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="68666-120">První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda odvodí schéma z dokumentu XML, který je součástí <xref:System.Xml.XmlReader> objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt, který obsahuje odvozené schématu.</span><span class="sxs-lookup"><span data-stu-id="68666-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="68666-121">Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda vyhledává <xref:System.Xml.Schema.XmlSchemaSet> jako dokument XML obsažených v objektu pro schéma s stejný cílový obor názvů <xref:System.Xml.XmlReader> zpřesnění existující schéma objektu a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt, který obsahuje odvozené schéma.</span><span class="sxs-lookup"><span data-stu-id="68666-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="68666-122">Změny provedené v kontrast schématu jsou založeny na novou strukturu nalezen v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68666-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="68666-123">Například jako provázán dokument XML, předpoklady probíhají o datových typech, najít a vytvořit schéma na základě těchto domněnek.</span><span class="sxs-lookup"><span data-stu-id="68666-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="68666-124">Pokud ale dat dochází na druhý odvození pass, která se liší od původní předpoklad, schéma je kontrast.</span><span class="sxs-lookup"><span data-stu-id="68666-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="68666-125">Následující příklad znázorňuje proces vylepšení.</span><span class="sxs-lookup"><span data-stu-id="68666-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="68666-126">V příkladu používá následující soubor `item1.xml`, jako první vstup.</span><span class="sxs-lookup"><span data-stu-id="68666-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="68666-127">V příkladu provede `item2.xml` soubor jako druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="68666-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="68666-128">Když `productID` v první dokument XML, hodnota je zjištěn atribut `123456789` je považován za `xs:unsignedInt` typu.</span><span class="sxs-lookup"><span data-stu-id="68666-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="68666-129">Ale pokud je druhý dokument XML pro čtení a hodnota `A53-246` nenajde, `xs:unsignedInt` typ může již nebude předpokládat, že.</span><span class="sxs-lookup"><span data-stu-id="68666-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="68666-130">Schéma je kontrast a typ `productID` se změní na `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="68666-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="68666-131">Kromě toho `minOccurs` atribut pro `supplierID` prvek je nastaven na `0`, protože druhý dokument XML neobsahuje žádné `supplierID` elementu.</span><span class="sxs-lookup"><span data-stu-id="68666-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="68666-132">Následuje schéma odvodit z první dokument XML.</span><span class="sxs-lookup"><span data-stu-id="68666-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="68666-133">Následuje schéma odvodit z první dokument XML, kontrast druhý dokument XML.</span><span class="sxs-lookup"><span data-stu-id="68666-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="68666-134">Vložené schémata</span><span class="sxs-lookup"><span data-stu-id="68666-134">Inline Schemas</span></span>  
 <span data-ttu-id="68666-135">Pokud jazyk (XSD) schématu definice schématu XML vložené dochází během <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="68666-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="68666-136">Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span><span class="sxs-lookup"><span data-stu-id="68666-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="68666-137">Schémata, která se nesmí Refined</span><span class="sxs-lookup"><span data-stu-id="68666-137">Schemas that Cannot be Refined</span></span>  
 <span data-ttu-id="68666-138">Existují W3C XML schématu, která vytvoří jazyk (XSD) schématu definice schématu XML <xref:System.Xml.Schema.XmlSchemaInference> proces nemůže zpracovat, pokud zadaný typ Upřesnit a způsobí vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="68666-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="68666-139">Například komplexní typ, jehož složku nejvyšší úrovně je nic jiného než sekvenci.</span><span class="sxs-lookup"><span data-stu-id="68666-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="68666-140">V schématu objektu modelu (SOM), to odpovídá <xref:System.Xml.Schema.XmlSchemaComplexType> jehož <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> vlastnost není instance <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="68666-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68666-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68666-141">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="68666-142">Model objektu schématu (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="68666-142">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [<span data-ttu-id="68666-143">Odvození schématu XML</span><span class="sxs-lookup"><span data-stu-id="68666-143">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [<span data-ttu-id="68666-144">Pravidla pro odvození typů a struktury uzlů schémat</span><span class="sxs-lookup"><span data-stu-id="68666-144">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [<span data-ttu-id="68666-145">Pravidla pro odvození jednoduchých typů</span><span class="sxs-lookup"><span data-stu-id="68666-145">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
