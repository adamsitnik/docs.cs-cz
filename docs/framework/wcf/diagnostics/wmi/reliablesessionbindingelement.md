---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973106"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Metody  
 Element ReliableSessionBindingElement Třída nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Element ReliableSessionBindingElement třída má následující vlastnosti:  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval, který místo určení čeká, než odešle oznámení zdroji zprávy ohledně stabilních kanálů, které jsou vytvořeny procesem.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda je povolena kontrola toku.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Určuje maximální dobu, po kterou je kanál povolí druhé komunikující straně nechcete poslat žádnou zprávu před přerušením kanálu.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet kanálů, které mohou čekat na přijetí na naslouchací proces.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet pokusů bezpečný kanál pokusí znovu poslat zprávu neobdržel potvrzení, voláním `Send` na svém základním kanálu.  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální velikost okna přenosu pro bezpečnou relaci.  
  
### <a name="ordered"></a>Řazení  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota, která určuje, zda je zaručená zprávy doručeny v pořadí, v jakém byly odeslány.  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 Datový typ: celé číslo  
  
 Typ přístupu: jen pro čtení  
  
 Celé číslo, které určuje verzi protokolu WS-ReliableMessaging používá ve stabilní relaci.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
