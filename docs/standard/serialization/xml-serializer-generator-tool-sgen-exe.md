---
title: Nástroj XML Serializer Generator (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 0eb937d003da02322c097d0eda0c3f8769f97dc8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468959"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Nástroj XML Serializer Generator (Sgen.exe)
Vytvoří generátor serializátor XML sestavení serializace XML pro typy v zadané sestavení s cílem zlepšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> při serializuje nebo deserializuje objekty zadaného typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sgen [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/a\[sestavení\]:**_název souboru_|Generuje kód serializace pro všechny typy, které jsou obsaženy v sestavení nebo spustitelný soubor určený *filename*. Lze zadat pouze jeden název souboru. Je-li tento argument se opakuje, se používá poslední název souboru.|  
|**/c\[ompiler\]:**_možnosti_|Určuje možnosti, které mají být předána do kompilátor jazyka C#. Všechny možnosti csc.exe jsou podporovány, jako jsou předávány kompilátoru. To lze použít k určení, že by měl být podepsáno sestavení a k určení souboru s klíčem.|  
|**/d\[ebug\]**|Generuje obrázek, který lze použít se ladicí program.|  
|**/f\[orce\]**|Vynutí přepsání existující sestavení se stejným názvem. Výchozí hodnota je **false**.|  
|**/ help nebo /?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/k\[achovat\]**|Potlačí odstranění vytvořených zdrojových souborů a jiné dočasné soubory, poté, co byl zkompilován sestavení serializace. To lze použít k určení, zda tento nástroj je generování kódu serializace pro určitý typ.|  
|**/n\[ologo\]**|Potlačí zobrazování úvodní nápis společnosti Microsoft.|  
|**/o\[ut\]:**_cesta_|Určuje adresář, do kterého chcete uložit vygenerované sestavení. **Poznámka:**  Název generované sestavení se skládá z názvu vstupní sestavení plus "xmlSerializers.dll".|  
|**/p\[roxytypes\]**|Generuje kód serializace pouze pro typy XML webové služby proxy serveru.|  
|**/r\[rnovat\]:**_assemblyfiles_|Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. Je možné zadat více souborů sestavení, oddělených čárkami.|  
|**/s\[ilent\]**|Potlačí zobrazování zpráv o úspěšném dokončení.|  
|**/t\[yp\]:**_typu_|Generuje kód serializace pouze u zadaného typu.|  
|**/v\[erbose\]**|Zobrazí podrobné informace pro ladění. Zobrazí seznam typů z cílového sestavení, které nelze serializovat, s <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není použit generátor serializátor XML, <xref:System.Xml.Serialization.XmlSerializer> generuje serializace kódu a sestavení serializace pro každý typ při každém spuštění aplikace. Pokud chcete zlepšit výkon při spuštění serializace XML, použijte nástroj Sgen.exe ke generování těchto sestavení předem. Tyto sestavení lze nasadit poté s aplikací.  
  
 Generátor serializátor XML můžete také zvýšit výkon klienty, kteří používají ke komunikaci se servery, protože proces serializace nesmí být účtovány výkonu, poté klikněte na tlačítko při prvním načtení typ proxy XML webové služby.  
  
 Tyto vygenerované sestavení nelze použít na straně serveru webové služby. Tento nástroj je jen pro scénáře ruční serializace a klienti webové služby.  
  
 Pokud sestavení obsahující typ k serializaci název MyType.dll, pak sestavení přidružené serializace bude pojmenován MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří sestavení s názvem Data.XmlSerializers.dll pro serializaci všechny typy, které jsou obsaženy v sestavení s názvem Data.dll.  
  
```  
sgen Data.dll   
```  
  
 Data.XmlSerializers.dll sestavení lze odkazovat z kódu, který potřebuje k serializaci a deserializaci typy v Data.dll.  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
