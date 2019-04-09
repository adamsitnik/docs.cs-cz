---
title: TCP-UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: e074a487c39dfaf1c4704f9dadf7ed8e430fb630
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172546"
---
# <a name="tcp-udp"></a><span data-ttu-id="afd38-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="afd38-102">TCP-UDP</span></span>
<span data-ttu-id="afd38-103">Protokolu TCP (Transmission Control) a protokolu UDP (User Datagram) služby se může používat aplikace <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, a <xref:System.Net.Sockets.UdpClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="afd38-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="afd38-104">Tyto třídy protokolu jsou zabudovány nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy a aby se postaral o podrobnosti přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="afd38-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="afd38-105">Protokol třídy použijte synchronní metody **soketu** třídy poskytují jednoduché a nekomplikované přístup k síťovým službám bez režie zachování informací o stavu nebo znát podrobnosti o nastavení konkrétní sokety.</span><span class="sxs-lookup"><span data-stu-id="afd38-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="afd38-106">Použití asynchronního **soketu** metody, můžete použít asynchronní metody poskytnuté <xref:System.Net.Sockets.NetworkStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="afd38-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="afd38-107">Pro přístup k funkcím nástroje **soketu** tříd nejsou viditelné v rámci protokolu tříd je nutné použít **soketu** třídy.</span><span class="sxs-lookup"><span data-stu-id="afd38-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="afd38-108">**TcpClient** a **TcpListener** představují síť používání **NetworkStream** třídy.</span><span class="sxs-lookup"><span data-stu-id="afd38-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="afd38-109">Můžete použít <xref:System.Net.Sockets.TcpClient.GetStream%2A> má metoda vrátit datový proud sítě a poté zavolejte datový proud <xref:System.Net.Sockets.NetworkStream.Read%2A> a <xref:System.Net.Sockets.NetworkStream.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="afd38-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="afd38-110">**NetworkStream** není vlastníkem soketu základní třídy protokol, tak jeho uzavřením nemá vliv na soketu.</span><span class="sxs-lookup"><span data-stu-id="afd38-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="afd38-111">**UdpClient** třída používá pole bajtů pro uložení datagramů UDP.</span><span class="sxs-lookup"><span data-stu-id="afd38-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="afd38-112">Můžete použít <xref:System.Net.Sockets.UdpClient.Send%2A> metoda k odesílání dat do sítě a <xref:System.Net.Sockets.UdpClient.Receive%2A> metoda přijímat příchozí datagram.</span><span class="sxs-lookup"><span data-stu-id="afd38-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd38-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afd38-113">See also</span></span>

- [<span data-ttu-id="afd38-114">Použití služeb TCP</span><span class="sxs-lookup"><span data-stu-id="afd38-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)
- [<span data-ttu-id="afd38-115">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="afd38-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)
- [<span data-ttu-id="afd38-116">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="afd38-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)
- [<span data-ttu-id="afd38-117">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="afd38-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="afd38-118">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="afd38-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="afd38-119">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="afd38-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
