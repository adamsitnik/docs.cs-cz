---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 384a1cdb6d39f4d6ecd2353a15c0da7c6d2e82bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758116"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
Určuje nastavení, které povoluje auditování událostí zabezpečení během operací služby.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|auditLogLocation|Určuje umístění protokolu auditu. Platné hodnoty patří:<br /><br /> – Výchozí hodnota: Zabezpečení události se zapisují do protokolu aplikací na Windows XP a do protokolu událostí na Windows Server 2003 a Windows Vista.<br />-Aplikace: Události auditu se zapisují do protokolu událostí aplikace.<br />-Zabezpečení: Události auditu se zapisují do protokolu událostí zabezpečení.<br /><br /> Výchozí hodnota je výchozí nastavení. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Logická hodnota, která určuje vlastnosti pro zamlčené chyby psaní do auditovacího protokolu.<br /><br /> Aplikace měli obdržet upozornění pro chyby psaní do auditovacího protokolu. Pokud vaše aplikace nebyla navržena pro zpracování chyb auditu, používejte tento atribut má potlačit chyby při psaní do auditovacího protokolu.<br /><br /> Pokud tento atribut je `true`, výjimky kromě OutOfMemoryException, StackOverflowException –, výjimka ThreadAbortException a ArgumentException, které jsou výsledkem pokusy o zápis událostí auditu, které jsou zpracovány systémem a nejsou šířeny do aplikace. Pokud tento atribut je `false`, všechny výjimky, které jsou výsledkem pokusy o zápis událostí auditu, které jsou předány do aplikace.<br /><br /> Výchozí hodnota je `true`.|  
|serviceAuthorizationAuditLevel|Určuje typy událostí autorizace, které jsou zaznamenány v protokolu auditu. Platné hodnoty patří:<br /><br /> -Žádný: Auditování událostí autorizace služby není provedeno.<br />– Úspěch: Pouze služba úspěšné autorizaci události se auditují.<br />– Selhání: Pouze chyby událostí autorizace služby budou auditovány.<br />-SuccessOrFailure: Úspěchy a chyby služby autorizace události se auditují.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Určuje typ zprávy ověřovacích událostí auditu přihlášení. Platné hodnoty patří:<br /><br /> -Žádný: Žádné události auditu jsou generovány.<br />– Úspěch: Pouze události (včetně ověřit podpis zprávy, šifrování a ověřování tokenů úplného ověření) úspěšná zabezpečení jsou protokolovány.<br />– Selhání: Pouze události chyby jsou protokolovány.<br />-SuccessOrFailure: Auditování úspěšných a neúspěšných události jsou protokolovány.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace umožňuje auditovat události ověřování Windows Communication Foundation (WCF). Když je povolené auditování, dají auditovat úspěšné nebo neúspěšné ověřování pokusů o zadání (nebo obojí). Události se zapisují do jedné ze tří protokolů událostí: aplikace, zabezpečení nebo v protokolu výchozí verze operačního systému. Protokoly událostí může vše zobrazit pomocí prohlížeče událostí Windows.  
  
 Podrobný příklad použití tento prvek konfigurace, najdete v části [chování auditování služby](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Ve výchozím nastavení Windows XP událostí auditu, které můžete zobrazit v protokolu aplikace; Když jste na Windows Server 2003 a Windows Vista, událostí auditu, které vidíte v protokolu zabezpečení. Umístění události auditu se dá nastavit tak, že nastavíte `auditLogLocation` atribut "Aplikace" nebo "Zabezpečení". Další informace najdete v tématu [jak: Auditování událostí zabezpečení](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Pokud události se zapisují do protokolu zabezpečení, LocalSecurityPolicy -> Povolit přístup k objektu je potřeba nastavit u "Success" a "Selhání".  
  
 Při hledání v protokolu událostí, je zdrojem událostí auditu "ServiceModel auditu 3.0.0.0". Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication" záznamy auditu autorizace služby mají kategorii "ServiceAuthorization".  
  
 Zprávy ověřovacích událostí auditu pokrytí, zda zpráva je porušené, určuje, zda vypršela platnost zprávy a jestli se klient může ověřit ve službě. Poskytují informace o tom, jestli ověření úspěšné nebo neúspěšné spolu s identitou klienta a koncového bodu zpráva byla odeslána spolu s akce spojený se zprávou.  
  
 Události auditu autorizace služby zahrnují rozhodnutí o autorizaci, které správce autorizace služby. Poskytují informace o tom, jestli byla úspěšná autorizace nebo se nepodařilo spolu s identitou klienta, koncový bod zprávy odeslané do akce spojený se zprávou, identifikátor autorizační kontext, který byl vytvořen příchozí zpráva a typ správce autorizace, který vytvořil rozhodnutí přístupu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Auditování](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Postupy: Auditování událostí zabezpečení](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Chování při auditování služby](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
