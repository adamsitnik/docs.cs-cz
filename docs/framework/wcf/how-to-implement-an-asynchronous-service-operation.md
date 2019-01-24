---
title: 'Postupy: Implementace operace asynchronní služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 56b82b44b56ab336ae9a460c328b76aa6974fcd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559759"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Postupy: Implementace operace asynchronní služby
V aplikacích Windows Communication Foundation (WCF) operace služby lze provést synchronní nebo asynchronní bez diktování klientovi jejich volání. Například operace asynchronní služby můžete volat synchronně, a synchronní servisní operace může být volána asynchronně. Příklad, který ukazuje, jak volat operace asynchronně v klientské aplikaci, najdete v části [jak: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o synchronní a asynchronní operace, najdete v části [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md) a [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Toto téma popisuje základní struktura operace asynchronní služby, není kompletní kód. Úplný příklad služby a klientské strany najdete v části [asynchronní](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implementace operace služby asynchronně  
  
1.  V servisní smlouvě deklaraci páru asynchronní metoda podle pokynů návrhu asynchronních rozhraní .NET. `Begin` Metoda přijímá parametr, objekt zpětného volání a stavu objektu a vrátí <xref:System.IAsyncResult?displayProperty=nameWithType> a odpovídající `End` metodu, která přebírá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrátí návratovou hodnotu. Další informace o asynchronní volání najdete v tématu [Asynchronous Programming Patterns návrhu](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Mark `Begin` metody, které odpovídá páru asynchronní metody s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atribut a nastavit <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost `true`. Například následující kód provede kroky 1 a 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implementace `Begin/End` dvojice metody ve třídě služby podle pokynů asynchronní návrh. Například následující příklad kódu ukazuje implementaci, ve kterém je napsán řetězec do konzoly v obou `Begin` a `End` části operace asynchronní služby a návratová hodnota `End` operace vrácen do klienta. Příklad úplného kódu naleznete v části příklad.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují kód:  
  
1.  Rozhraní kontraktu služby se:  
  
    1.  Synchronního `SampleMethod` operace.  
  
    2.  Asynchronní `BeginSampleMethod` operace.  
  
    3.  Asynchronní `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pár operace.  
  
2.  Implementace služby pomocí <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)
- [Synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
