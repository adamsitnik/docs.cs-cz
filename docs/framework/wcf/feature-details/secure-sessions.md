---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084951"
---
# <a name="secure-sessions"></a>Zabezpečené relace
Funkce služby Windows Communication Foundation (WCF) je spolehlivé relace, které zaručuje, že jsou zprávy přijímány v pořadí, ve kterém byly odeslány. Témata v této části popisují vliv zabezpečení můžete zvážit při vytváření spolehlivé relace. Další informace o spolehlivých relací najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Když zosobnění je potřeba na Windows XP, použijte k tomu zabezpečenou relaci bez tokenu kontextu zabezpečení stavové (SCT). Když zosobnění, se používají stavové SCTs <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|||  
|-|-|  
|[Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Zabezpečené konverzace a zabezpečené relace je shodný. Toto téma popisuje způsob, jakým funguje zabezpečené konverzace a kdy a proč k použití vzoru.|  
|[Postupy: Vytvoření zabezpečené relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Vás provede základy práce vytváření zabezpečenou relaci.|  
|[Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Vás provede kroky k vytvoření webové farmy, která bude spravovat stav a relace s klienty.|  
|[Důležité informace o zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Popisuje důležité informace pro zabezpečené relace.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Související oddíly  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolit zjišťování opakování zpráv](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
