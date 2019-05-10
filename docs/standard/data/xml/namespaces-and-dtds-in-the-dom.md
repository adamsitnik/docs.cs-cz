---
title: Obory názvů a specifikace DTD v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3a3ec957a55ff23dec728ccd31fe9e1f52ce78f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590215"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Obory názvů a specifikace DTD v modelu DOM
Podpora dokumentu typ definice (DTD) complicate oboru názvů. Například následující kód XML obsahuje výchozí atributy obsahující dvojteček při jejich názvy.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Následující jsou uvedena možná řešení, pokud je povolený tento konstruktor:  
  
- `x:` Je zpracováván jako předponu oboru názvů, ale tuto předponu, musí být možné přeložit pomocí `xmlns:x` deklarace oboru názvů, který musí taky existovat někde jinde v DTD. Jedná se o chybu pro tuto předponu mapování na něco jiného v dokumentu instance.  
  
- `x:` Je považován za předponu oboru názvů, ale tato předpona je vždy přeložit v rámci prvků instance. To znamená, že předpona, která by mohla ve skutečnosti mapují na jiný obor názvů Uniform Resource Identifier (identifikátory URI), v závislosti na rozsahu oboru názvů ve kterém `item` element objeví. Toto chování je předvídatelnější než uvedené v předchozích odrážky rozlišení, ale má jiné složité následky, protože vyžaduje materializace výchozí atributy.  
  
- Dvojtečka je ignorován, protože je v DTD a název atributu je `x:y`, žádná předpona a žádný obor názvů identifikátoru URI.  
  
- Dvojtečka ve výchozí atribut vyvolá výjimku, informacemi o tom, že se nepodporují použití dvojteček v názvech definici DTD. Výsledkem je předvídatelný chování, ale znamená, že nelze načíst řadu World Wide Web Consortium (W3C) publikovaný specifikace DTD.  
  
- Když uživatel požádá o ověření DTD, podpora oboru názvů pro celý dokument je vypnutý. Umožňuje načíst W3C DTD a výsledkem je předvídatelný chování.  
  
 Kód XML v rozhraní Microsoft .NET Framework implementuje druhou možnost pro maximální kompatibility W3C.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
