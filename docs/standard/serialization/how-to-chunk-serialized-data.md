---
title: 'Postupy: bloku dat serializovaná data'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 65e332d229da8fe51ad9c3e9850603471b1dfb12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018096"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="7e018-102">Postupy: bloku dat serializovaná data</span><span class="sxs-lookup"><span data-stu-id="7e018-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="7e018-103">Jsou dva problémy, k nimž došlo při odesílání velkých sad dat do webové služby zpráv:</span><span class="sxs-lookup"><span data-stu-id="7e018-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="7e018-104">Velké pracovní sada (paměť) z důvodu ukládání do vyrovnávací paměti modul serializace.</span><span class="sxs-lookup"><span data-stu-id="7e018-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="7e018-105">Nadměrné využití šířky pásma vzhledem k inflaci 33 procent po kódování Base64.</span><span class="sxs-lookup"><span data-stu-id="7e018-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="7e018-106">Chcete-li tyto problémy vyřešit, implementovat <xref:System.Xml.Serialization.IXmlSerializable> rozhraní pro řízení serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="7e018-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="7e018-107">Konkrétně implementovat <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody k bloku dat data.</span><span class="sxs-lookup"><span data-stu-id="7e018-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="7e018-108">K implementaci bloků na straně serveru</span><span class="sxs-lookup"><span data-stu-id="7e018-108">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="7e018-109">V počítači serveru musí vypnout ukládání do vyrovnávací paměti technologie ASP.NET a návratový typ, který implementuje metodu webové <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="7e018-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="7e018-110">Typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> chunks data v <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7e018-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="7e018-111">K implementaci zpracování na straně klienta</span><span class="sxs-lookup"><span data-stu-id="7e018-111">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="7e018-112">Změnit metodu webové na proxy serveru klienta má být vrácen typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="7e018-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="7e018-113">Můžete použít <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> k provést automaticky, ale není to zde uvedeny.</span><span class="sxs-lookup"><span data-stu-id="7e018-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="7e018-114">Implementace <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodu za účelem čtení blokového data datového proudu a zápis na disk bajtů.</span><span class="sxs-lookup"><span data-stu-id="7e018-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="7e018-115">Tato implementace také vyvolává průběh události, které mohou být využívána grafického ovládacího prvku, jako je například indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="7e018-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e018-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e018-116">Example</span></span>  
<span data-ttu-id="7e018-117">Následující příklad kódu ukazuje metodu webové na straně klienta, který vypne ukládání do vyrovnávací paměti technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7e018-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="7e018-118">Profil také ukazuje na straně klienta provádění <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které chunks data v <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7e018-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e018-119">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="7e018-119">Compiling the code</span></span>  
  
- <span data-ttu-id="7e018-120">Kód používá následující obory názvů: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, a <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="7e018-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e018-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e018-121">See also</span></span>

- [<span data-ttu-id="7e018-122">Vlastní serializace</span><span class="sxs-lookup"><span data-stu-id="7e018-122">Custom Serialization</span></span>](custom-serialization.md)
