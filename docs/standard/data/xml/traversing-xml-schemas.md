---
title: Procházení schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6040a7aa8f3244ea0ce2e66042537bc45c347b05
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037857"
---
# <a name="traversing-xml-schemas"></a>Procházení schémat XML

Procházení schématu XML pomocí rozhraní API modelu SOM (Schema Object Model) poskytuje přístup k prvkům, atributům a typům uloženým v modelu SOM. Procházení schématu XML načteného do modelu SOM je zároveň prvním krokem v úpravách schématu XML pomocí rozhraní SOM API.

## <a name="traversing-an-xml-schema"></a>Procházení schématu XML

Následující vlastnosti <xref:System.Xml.Schema.XmlSchema> třídy poskytují přístup ke kolekci všech globálních položek přidaných do schématu XML.

|Vlastnost|Typ objektu uložený v kolekci nebo poli|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>nebo<xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject>(poskytuje přístup ke všem prvkům, atributům a typům globální úrovně).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute>(poskytuje přístup k atributům, které nepatří do oboru názvů schématu)|

> [!NOTE]
> Všechny vlastnosti uvedené v tabulce výše, s výjimkou <xref:System.Xml.Schema.XmlSchema.Items%2A> vlastnosti, jsou vlastnosti post-Schema-Compilation-pSCI, které nejsou k dispozici, dokud schéma nebude zkompilováno. <xref:System.Xml.Schema.XmlSchema.Items%2A> Vlastnost je vlastnost kompilace před schématy, kterou lze použít před zkompilováním schématu pro přístup a úpravy všech prvků, atributů a typů globální úrovně.
>
> <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Vlastnost poskytuje přístup ke všem atributům, které nepatří do oboru názvů schématu. Tyto atributy procesor schématu nezpracovává.

Následující příklad kódu ukazuje procházení schématu zákazníka vytvořeného v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) . Příklad kódu ukazuje procházení schématu pomocí výše popsaných kolekcí a zapisuje všechny prvky a atributy ve schématu do konzoly.

Ukázka projde schéma zákazníka v následujících krocích.

1. Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje. <xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu.

2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).

3. Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> v kolekci kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> , která zapisuje název každého elementu do konzoly.

4. Získá komplexní typ `Customer` elementu <xref:System.Xml.Schema.XmlSchemaComplexType> pomocí třídy.

5. Má-li komplexní typ nějaké atributy, získá a <xref:System.Collections.IDictionaryEnumerator> provede výčet každého <xref:System.Xml.Schema.XmlSchemaAttribute> a zapíše jeho název do konzoly.

6. Získá částice sekvence komplexního typu pomocí <xref:System.Xml.Schema.XmlSchemaSequence> třídy.

7. Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> v kolekci, která zapisuje název každého podřízeného elementu do konzoly.

Následuje příklad kompletního příkladu kódu.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

Vlastnost může být <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo<xref:System.Xml.Schema.XmlSchemaComplexType> , pokud se jedná o uživatelsky definovaný jednoduchý typ nebo komplexní typ. <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Může to být <xref:System.Xml.Schema.XmlSchemaDatatype> také v případě, že se jedná o jeden z předdefinovaných DataType definovaných v doporučení schématu W3C XML. Ve <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> schématu <xref:System.Xml.Schema.XmlSchemaComplexType> zákazníkaje`FirstName` `LastName` element a prvky<xref:System.Xml.Schema.XmlSchemaSimpleType>a. `Customer`

Příklad kódu v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) použili <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekci k přidání atributu `CustomerId` do `Customer` elementu. Toto je vlastnost předběžného schématu kompilace. Odpovídající vlastnost post-Schema-Compilation- <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> CollectionName je kolekce, která obsahuje všechny atributy komplexního typu, včetně těch, které jsou zděděny prostřednictvím odvození typu.

## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
