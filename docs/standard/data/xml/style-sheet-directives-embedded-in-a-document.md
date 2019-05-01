---
title: Direktivy šablon stylů vložené v dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65987c5e29d593758b21259d6367202c882df2de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026936"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Direktivy šablon stylů vložené v dokumentu

V některých případech existující kód XML obsahuje direktiva list stylu `<?xml:stylesheet?>`. Microsoft Internet Explorer přijímá to jako alternativu k `<?xml-stylesheet?>` syntaxe. Pokud XML data obsahuje `<?xml:stylesheet?>` direktiv, jak je znázorněno v následující data pokusu o načtení těchto dat do XML Document Object Model (DOM) dojde k výjimce.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

K tomu dochází, `<?xml:stylesheet?>` je považován za neplatný **ProcessingInstruction** do modelu DOM. Žádné **ProcessingInstruction**, podle oborů názvů ve specifikaci XML, může obsahovat jenom názvy no dvojtečka (NCNames), na rozdíl od kvalifikované názvy (QNames).

Z část 6 oborů názvů ve specifikaci XML, má vliv **zatížení** a **příkaz LoadXml** metody v souladu s specifikace, která je v dokumentu:

- Všechny názvy atributů a typy prvků obsahovat dvojtečku nebo vůbec.

- Žádné názvy entit, ProcessingInstruction cíle nebo názvy výpisů obsahovat jakékoli použití dvojteček.

S `<?xml:stylesheet?>` obsahuje dvojtečku, můžete nyní porušovat pravidla v druhém odrážky.

Podle World Wide Web Consortium (W3C) [přidružení šablony stylů XML dokumenty verze 1.0 doporučení](https://www.w3.org/TR/xml-stylesheet/), instrukce pro zpracování šablony stylů XSLT přidružení k dokumentu XML je `<?xml-stylesheet?>`, se nahrazení dvojtečka Dash.

## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
