---
title: Přidání odkazu na službu do řešení pracovního postupu
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 8f1fa4604f1a1873c7063ec3c9dccf08bd0aa0ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549038"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Přidání odkazu na službu do řešení pracovního postupu

Přidání odkazu do služby pracovního postupu aplikace funguje trochu jinak, než aplikace v jazyce regulárních WCF. Když vyberete **Přidat > odkaz na službu** a zadejte adresu URL ve službě, se stáhne metadata a vlastní aktivity se vygenerují, které vám umožní volat služby WCF nebo přidat odkaz na služby pracovního postupu WCF. Po přidání odkazu na službu znovu sestavte řešení, jsou integrované generované aktivity. Zobrazí se pak na panelu nástrojů Návrháře pracovního postupu. Všimněte si však, že to bude fungovat jenom v případě přidáte odkaz na službu do řešení pracovního postupu. Následující přetypování webové ukazuje, jak přidat odkaz na službu v ostatních typů projektů: [Volání z pracovního postupu v projektu webové služby WCF](https://go.microsoft.com/fwlink/?LinkId=207725).

Přidání dvou nebo více odkazů na služby pro služby, které obsahují stejný název operace způsobí, že k potížím. Generované aktivity bude volat pouze první operaci služby. Chcete-li vyřešit tento problém přejmenování operací služby tak, aby se liší nebo změňte název konfigurace koncového bodu v rámci každé vygenerované aktivity.

## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Volání z pracovního postupu v projektu webové služby WCF](https://go.microsoft.com/fwlink/?LinkId=207725)
