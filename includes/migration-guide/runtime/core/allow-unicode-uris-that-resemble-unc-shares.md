---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856952"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povolit kódování Unicode v identifikátory URI, které se podobají UNC sdílené složky

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>sestavením souboru identifikátory URI obsahující oba UNC název sdílené složky a znaky znakové sady Unicode již nebude v identifikátoru URI se neplatný vnitřní stav. Chování se změní, pouze pokud všechny tyto jsou splněny:<ul><li>Identifikátor URI obsahuje schéma <code>file:</code> a je následována čtyři nebo více lomítek.</li><li>Název hostitele začíná podtržítkem nebo jiný nerezervované symbol.</li><li>Identifikátor URI obsahuje znaky kódování Unicode.</li></ul>|
|Doporučení|Aplikace pracující s identifikátory URI obsahující konzistentně Unicode mohli případně použít toto chování Pokud chcete zakázat odkazy na sdílené složky UNC. Tyto aplikace by měly používat <xref:System.Uri.IsUnc> místo.|
|Scope|Edge|
|Version|4.7.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

