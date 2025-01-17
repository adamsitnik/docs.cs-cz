---
title: 'Postupy: Povolit přístup k datové službě (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: cbe25dcb62adf82921b24623cc4930c3076dd1fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790660"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Postupy: Povolit přístup k datové službě (WCF Data Services)
V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroji musíte explicitně udělit přístup k prostředkům, které jsou zpřístupněny datovou službou. To znamená, že po vytvoření nové datové služby musíte explicitně poskytnout přístup k jednotlivým prostředkům jako sady entit. V tomto tématu se dozvíte, jak povolit přístup pro čtení a zápis do pěti sad entit v datové službě Northwind, která se vytvoří po dokončení [rychlého](quickstart-wcf-data-services.md)startu. Vzhledem k tomu <xref:System.FlagsAttribute>, že je výčetdefinovánpomocí,lzepomocílogickéhooperátoruORzadatvíceoprávněníprojednusaduentit.<xref:System.Data.Services.EntitySetRights>  
  
> [!NOTE]
> Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou. Pokud chcete zabránit neoprávněnému přístupu k prostředkům, měli byste ve službě produkčních dat také zabezpečit samotnou aplikaci. Další informace najdete v tématu [zabezpečení ASP.NET webů](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Povolení přístupu k datové službě  
  
- V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Díky tomu mají klienti přístup pro čtení a zápis k `Orders` sadám entit a `Order_Details` a přístup k `Customers` sadám entit jen pro čtení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj datové služby WCF běžící ve službě IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Konfigurace datové služby](configuring-the-data-service-wcf-data-services.md)
