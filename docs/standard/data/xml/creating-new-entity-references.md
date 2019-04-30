---
title: Vytváření nových odkazů na entity
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934488"
---
# <a name="creating-new-entity-references"></a>Vytváření nových odkazů na entity
**CreateEntityReference** metoda vytvoří nový **XmlEntityReference** uzlu. Pokud chcete zobrazit, pokud je už deklarovaný název entity, na kterou se odkazuje vypadá XML Document Object Model (DOM). Pokud ano, podřízené uzly **XmlEntityReference** uzlu jsou zkopírovány z uzlu entity prohlášení. Pokud neexistuje žádná deklarace entity, který odpovídá, prázdný textový uzel je připojen jako jediný podřízený uzel odkazu entity. Protože podřízené uzly **XmlEntityReference** uzlu jsou kopie jiných uzlech, tyto podřízené uzly jsou jen pro čtení a nelze ji změnit.  
  
 Když se zkopírují uzly, může být oboru názvů v oboru místě odkaz na entitu. Tento obor názvů má vliv na konfiguraci jakéhokoli uzlu elementu nebo atributu vygenerována.  
  
> [!NOTE]
>  Přidá podřízené uzly modelu DOM **EntityReference** pouze při vložení **EntityReference** uzel v dokumentu. Nově vytvořené **EntityReference** uzly obsahovat podřízené uzly.  
  
 I když **XmlDataDocument** je odvozenou třídu **třídou XMLDocument nastavenou na**, **objektu XmlDataDocument** nepodporuje vytváření odkazů na entity. Důvodem je, že **EntityReference** podřízené objekty jsou jen pro čtení. Podřízené objekty daného **EntityReference** uzel může zahrnovat více než jedné oblasti. V takovém případě část řádku přidružené k oblasti, která obsahuje součást **EntityReference** budou jen pro čtení.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
