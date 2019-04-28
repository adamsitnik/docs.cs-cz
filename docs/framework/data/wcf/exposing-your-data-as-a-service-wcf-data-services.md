---
title: Vystavení dat jako služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 3c0763f21940831f401194356dc25b0d99c8d6f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765632"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Vystavení dat jako služby (WCF Data Services)

Služby WCF Data Services se integruje se sadou Visual Studio umožňuje snadno definovat služby k vystavení dat jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanály. Vytvoření datové služby, která vystavuje kanál OData zahrnuje následující základní kroky:

1. **Definování datového modelu.** Služby WCF Data Services nativně podporuje datové modely, které jsou založeny na [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Další informace najdete v tématu [jak: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).

     Služby WCF Data Services také podporuje datové modely, které jsou založené na common language runtime (CLR) objekty, které vracet instanci <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje nasazení datových služeb, které jsou založeny na seznam, pole a kolekce v rozhraní .NET Framework. Umožňuje vytvářet, aktualizovat a odstraňovat operace nad tyto datové struktury, musí také implementovat <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [jak: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).

     Pro pokročilejší scénáře služeb WCF Data Services obsahuje sadu zprostředkovatelů, které vám umožňují definovat datový model na základě typu dat s pozdní vazbou. Další informace najdete v tématu [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).

2. **Vytvoření datové služby.** Nejzákladnější datová služba zpřístupní třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy s typem `T` , který je kvalifikovaný v oboru názvů názvu kontejneru entity. Další informace najdete v tématu [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3. **Konfigurace datové služby.** Ve výchozím nastavení služby WCF Data Services zakáže přístup k prostředkům, které jsou vystaveny kontejnerem entity. <xref:System.Data.Services.DataServiceConfiguration> Rozhraní umožňuje konfigurovat přístup k prostředkům a operacím služby, zadat podporovanou verzi protokolu OData a definovat další chování v rámci služeb, například chování dávek nebo maximální počet entit, které mohou být vráceny. v jednu odpověď. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Příklad toho, jak vytvořit jednoduchou datovou službu, která je založena na ukázkové databáze Northwind, naleznete v tématu [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)