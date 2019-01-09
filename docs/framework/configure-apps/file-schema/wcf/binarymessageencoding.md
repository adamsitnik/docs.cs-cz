---
title: '&lt;binaryMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 2e29721104400c8a0352ebf5cd292689de0d6b14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150120"
---
# <a name="ltbinarymessageencodinggt"></a>&lt;binaryMessageEncoding&gt;
Definuje kodér binárních zpráv, který binárně kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince.  
  
 \<system.serviceModel>  
\<vazby >  
\<třídě customBinding >  
\<Vytvoření vazby >  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|maxReadPoolSize|Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 64.|  
|maxSessionSize|Celé kladné číslo nastavující velikost v bajtech, použité pro kódování vyrovnávací paměti. Větší vyrovnávací paměť zvyšuje kódování rychlost na úkor velikost pracovní sady. Výchozí hodnota je hodnotu 2048.|  
|maxWritePoolSize|Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 16.|  
|verze messageVersion|Určuje zprávu protokolu SOAP a WS-Addressing verze, které jsou používány nebo očekávání.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávu do sekvence bajtů. Dekódování je opačný proces. Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).  
  
 `binaryMessageEncoding` Prvek Určuje binární formát .NET pro XML a má možností určení kódování znaků a verze protokolu SOAP a WS-Addressing má být použit. Kodér binárních zpráv kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince. Když toto kódování má za následek velmi rychlé zpracování přenos zpráv, vzájemná funkční spolupráce podle WS-* standardů se ztratí.  
  
## <a name="example"></a>Příklad  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<třídě customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
