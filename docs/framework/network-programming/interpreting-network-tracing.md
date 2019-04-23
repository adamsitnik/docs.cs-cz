---
title: Interpretace trasování sítě
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 00df193671255e7b40f5c4b86ee952a3e20e3a40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177564"
---
# <a name="interpreting-network-tracing"></a>Interpretace trasování sítě
Pokud je povoleno trasování sítě, můžete použít trasování pro zachycení volání, které vaše aplikace odešle do různých <xref:System.Net> členy třídy. Výstup z těchto volání může být podobně jako v následujících příkladech.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 V předchozím příkladu [588] je jedinečný identifikátor aktuálního vlákna. (4357) a (4387) jsou časové razítko označující počet milisekund uplynulých od spuštění aplikace. Data po časové razítko je vidět aplikace vstupující do a vystupující metodu **Socket.Send**. Objekt provádění **odeslat** metoda má 33574638 jako svůj jedinečný identifikátor. Trasování ukončovací metoda zahrnuje návratovou hodnotu (61 v předchozím příkladu).  
  
 Trasování sítě můžete zaznamenávat síťový provoz, který je odeslaných nebo přijatých aplikací pomocí protokolů úrovni aplikace, jako je protokol HTTP (Hypertext Transfer). Tato data se dají zachytit jako text a volitelně data v šestnáctkovém formátu. Šestnáctkové data jsou k dispozici, když zadáte **includehex** jako hodnotu **tracemode** atribut. (Podrobné informace o tomto atributu naleznete v tématu [jak: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Následující příklad trasování se vygeneroval pomocí **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Pokud chcete vynechat, nechte šestnáctkových dat., zadejte **protocolonly** hodnotu **tracemode** atribut. Následující příklad ukazuje trasování při **protocolonly** určena.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Viz také:

- [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
