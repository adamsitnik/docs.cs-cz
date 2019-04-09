---
title: Oprávnění pro web a sokety
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: 78ad06107155408b2aca854a8251c21a24c6577a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166852"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="9298a-102">Oprávnění pro web a sokety</span><span class="sxs-lookup"><span data-stu-id="9298a-102">Web and Socket Permissions</span></span>
<span data-ttu-id="9298a-103">Internetové zabezpečení pro aplikace využívající <xref:System.Net> obor názvů poskytuje <xref:System.Net.WebPermission> a <xref:System.Net.SocketPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="9298a-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="9298a-104">**Oprávnění WebPermission** třídy ovládací prvky aplikace přímo do data žádosti z identifikátoru URI nebo identifikátor URI neslouží k Internetu.</span><span class="sxs-lookup"><span data-stu-id="9298a-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="9298a-105">**SocketPermission** třídy aplikaci prvku správné použití ovládacích prvků <xref:System.Net.Sockets.Socket> tak, aby přijímal data na jiný místní port nebo se obrátit na vzdálené zařízení pomocí protokolu přenosu na jiné adrese založené na hostiteli, číslo portu, a Přenosový protokol soketu.</span><span class="sxs-lookup"><span data-stu-id="9298a-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="9298a-106">Která oprávnění třída použijete, závisí na váš typ aplikace.</span><span class="sxs-lookup"><span data-stu-id="9298a-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="9298a-107">Aplikace, které používají <xref:System.Net.WebRequest> a jejích potomků, používejte **oprávnění WebPermission** třídy pro správu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9298a-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="9298a-108">Používejte aplikace, které používají přístup na úrovni soketu **SocketPermission** třídy pro správu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9298a-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="9298a-109">**Oprávnění WebPermission** a **SocketPermission** definovat dvě oprávnění: přijmout a připojit.</span><span class="sxs-lookup"><span data-stu-id="9298a-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="9298a-110">Přijměte uděluje právo k zodpovězení příchozí připojení z jiného aplikace.</span><span class="sxs-lookup"><span data-stu-id="9298a-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="9298a-111">Připojte se uděluje právo k navázání připojení k jiné strany aplikace.</span><span class="sxs-lookup"><span data-stu-id="9298a-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="9298a-112">Pro **SocketPermission** instancí, přijměte znamená, že aplikace může přijmout příchozí spojení na místní adresu přenosu; připojení znamená, že aplikace může připojit k adrese některé přenos vzdálený (nebo místní).</span><span class="sxs-lookup"><span data-stu-id="9298a-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="9298a-113">Pro **oprávnění WebPermission** instancí, přijměte znamená, že aplikace můžete exportovat identifikátor URI, řídí **oprávnění WebPermission** ve světě; připojení znamená, že aplikace může použít tento identifikátor URI (ať už jde vzdálené nebo místní).</span><span class="sxs-lookup"><span data-stu-id="9298a-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9298a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9298a-114">See also</span></span>

- [<span data-ttu-id="9298a-115">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9298a-115">Security</span></span>](../../../docs/standard/security/index.md)
- [<span data-ttu-id="9298a-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="9298a-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
