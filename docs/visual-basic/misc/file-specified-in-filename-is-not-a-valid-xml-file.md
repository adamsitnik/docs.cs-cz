---
title: Soubor zadaný v názvu souboru není platný soubor XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: ffa39653c20127bb6af5e85654fee940a191fe5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603521"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Soubor zadaný v názvu souboru není platný soubor XML
Název souboru, který jste zadali, není platný soubor XML. K určení povolených struktuře a obsahu dokumentu XML, můžete dokumentu typ definice (DTD), Microsoft XML-Data Reduced (XDR) schématu nebo jazyk (XSD) schématu definice schématu XML. XSD schémata jsou preferovaným způsobem, jak určit gramatiky XML v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].

> [!NOTE]
>  V některých dřívějších verzích sady Visual Studio **XML – návrhář** se návrhář pro typové datové sady a schématu XML. **XML – návrhář** je stále možné vytvářet a upravovat soubory schémat XML. V sadě Visual Studio 2012, návrháře pro vytváření a úpravu typové datové sady je ale **Návrhář Dataset**. Další informace najdete v tématu [vytváření a úpravy typované datové sady](/visualstudio/data-tools/creating-and-editing-typed-datasets).

## <a name="to-correct-this-error"></a>Oprava této chyby

-   Zkontrolujte, že zadáváte správný název souboru.

-   Zkontrolujte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete zkontrolovat do **XML – návrhář**. Z **XML** nabídky, klikněte na tlačítko **ověřit XML**. Chyby zobrazují v **seznamu úkolů**.

-   Pokud má soubor XML přidružené schéma XML, zkontrolujte, že se elementy zobrazí ve struktuře definovaná a, obsah jednotlivých prvků odpovídá deklarovanému datovému typy určená ve schématu.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml>
- [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)