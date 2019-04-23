---
title: Vytváření interoperabilních služeb WS-I Basic Profile 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: b9cacee9a69695b0001b94b74648d5154b8a52b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123913"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="66a08-102">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="66a08-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="66a08-103">Chcete-li nakonfigurovat koncový bod služby WCF, aby vzájemná spolupráce s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům:</span><span class="sxs-lookup"><span data-stu-id="66a08-103">To configure a WCF service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="66a08-104">Použití <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro vaše koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="66a08-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="66a08-105">Nepoužívejte zpětné volání a funkce smlouvy relace nebo chování transakce na váš koncový bod služby</span><span class="sxs-lookup"><span data-stu-id="66a08-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="66a08-106">Volitelně můžete povolit podporu protokolu HTTPS a ověřování klientů na úrovni přenosu na vazbu.</span><span class="sxs-lookup"><span data-stu-id="66a08-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="66a08-107">Následující funkce <xref:System.ServiceModel.BasicHttpBinding> třídy vyžadují funkce nad rámec WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="66a08-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="66a08-108">Kódování zpráv přenosu optimalizace mechanismus (MTOM) zpráva řídí <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="66a08-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="66a08-109">Ponechte výchozí hodnotu, která je tato vlastnost <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nechcete použít MTOM.</span><span class="sxs-lookup"><span data-stu-id="66a08-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="66a08-110">Řídí zabezpečení zpráv <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnota podporuje WS-Security kompatibilní s WS-I základní 1.0 profil zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="66a08-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="66a08-111">Ponechte výchozí hodnotu, která je tato vlastnost <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nechcete použít WS-Security.</span><span class="sxs-lookup"><span data-stu-id="66a08-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="66a08-112">Aby metadata pro služby WCF k dispozici [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], použijte nástroje pro generování klienta služby Web: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [nástroj zjišťování webové služby (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a `Add Web Reference` funkce v sadě Visual Studio; je nutné povolit publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="66a08-112">To make the metadata for a WCF service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="66a08-113">Další informace najdete v tématu [publikování kocových bodů metadat](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="66a08-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a08-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="66a08-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="66a08-115">Popis</span><span class="sxs-lookup"><span data-stu-id="66a08-115">Description</span></span>  
 <span data-ttu-id="66a08-116">Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových klientů služby v kódu a také v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="66a08-116">The following example code demonstrates how to add a WCF endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="66a08-117">Kód</span><span class="sxs-lookup"><span data-stu-id="66a08-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="66a08-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66a08-118">See also</span></span>

- [<span data-ttu-id="66a08-119">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a08-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
