---
title: Ukázka technologie základní serializace
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 803f45db008dc6d12566868ba4a8c61642687d89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486397"
---
# <a name="basic-serialization-technology-sample"></a>Ukázka technologie základní serializace
[Stáhněte si ukázky](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Tento příklad znázorňuje možnost common language runtime k serializaci grafu objektů v paměti do datového proudu. V tomto příkladu můžete použít buď <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pro serializaci. Odkazovaného seznamu, vyplněno data, je serializován nebo deserializován nebo z datový proud souboru. V obou případech se zobrazí v seznamu, aby mohli zobrazit výsledky. Propojený seznam je typu `LinkedList`, typu definované v tomto příkladu.  
  
 Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>K vytvoření vzorku pomocí příkazového řádku  
  
1. Přejděte do jednoho podadresáře konkrétní jazyk do adresáře Technologies\Serialization\Runtime Serialization\Basic, pomocí příkazového řádku.  
  
2. Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** nebo **msbuild SerializationVB.sln**, v závislosti na požadovaném programovací jazyk, v příkazový řádek.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1. Otevřete Průzkumníka souborů a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.  
  
2. Poklepejte na ikonu souboru SerializationCS.sln, SerializationJSL.sln nebo SerializationVB.sln podle svého výběru: programovací jazyk, k otevření souboru v sadě Visual Studio.  
  
3. V **sestavení** nabídce vyberte možnost **sestavit řešení**.  
  
 Vzorová aplikace bude vytvořen v podadresáři \bin nebo \bin\Debug výchozí.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Přejděte do adresáře, který obsahuje připravené spustitelný soubor.  
  
2. Typ **Serialization.exe**, spolu s hodnotami parametrů vyžadujete, na příkazovém řádku.  
  
    > [!NOTE]
    >  Tato ukázka vytvoří aplikace konzoly. Musí spusťte ji pomocí příkazového řádku, aby bylo možné zobrazit její výsledek.  
  
## <a name="remarks"></a>Poznámky  
 Ukázkové aplikace, který přijme parametry příkazového řádku, která určuje, které můžete testovat se má provést. K serializaci seznam 10 uzel do souboru s názvem **Test.xml** pomocí formátovacího modulu protokolu SOAP, použijte parametry **sx Test.xml 10**.  
  
 Příklad:  
  
 **Serialize.exe - sx Test.xml 10**  
  
 K deserializaci **Test.xml** soubor z předchozího příkladu, použijte parametry **dx Test.xml**.  
  
 Příklad:  
  
 **Serialize.exe -dx Test.xml**  
  
 V obou výše uvedených příkladech "x" v přepínačem příkazového řádku udává, že serializace XML SOAP. "B" můžete místo ní používat binární serializace. Pokud chcete akci serializace s velmi velkým počtem uzlů, můžete chtít přesměrovat výstup konzoly do souboru.  
  
 Příklad:  
  
 **Serialize.exe - sb Test.bin 10000 > somefile.txt**  
  
 Následující odrážky Krátce popište, třídy a technologie používané v tomto příkladu.  
  
- Modul runtime serializace  
  
    - <xref:System.Runtime.Serialization.IFormatter> Používá k odkazování na buď <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> objektu.  
  
    - <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Slouží k serializaci odkazovaného seznamu do datového proudu v binárním formátu. Binární formátovací modul používá formát pouze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> znalost typu. Data jsou však stručné.  
  
    - <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Slouží k serializaci odkazovaného seznamu do datového proudu ve formátu protokolu SOAP. Protokol SOAP je ve standardním formátu.  
  
- I/O proudu  
  
    - <xref:System.IO.Stream> Slouží k serializaci a deserializaci. Typ konkrétní datového proudu, který je použit v tomto příkladu je <xref:System.IO.FileStream> typu. Serializace však lze používat s libovolného typu odvozeného z <xref:System.IO.Stream>.  
  
    - <xref:System.IO.File> Umožňuje vytvořit <xref:System.IO.FileStream> objektů pro čtení a vytváření souborů na disku.  
  
    - <xref:System.IO.FileStream> Slouží k serializaci a deserializaci propojené seznamy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [Základní serializace](../../../docs/standard/serialization/basic-serialization.md)
- [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)
- [Řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Serializace](../../../docs/standard/serialization/index.md)
- [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
