---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: abbb02b7bd22c4b301c5565037f55aa1019fc3ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642487"
---
# <a name="http"></a><span data-ttu-id="90b18-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="90b18-102">HTTP</span></span>
<span data-ttu-id="90b18-103">Rozhraní .NET Framework poskytuje komplexní podporu pro protokol HTTP, které tvoří většinou všechny přenosy z Internetu, se <xref:System.Net.HttpWebRequest> a <xref:System.Net.HttpWebResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="90b18-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="90b18-104">Tyto třídy odvozené z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, jsou vráceny ve výchozím nastavení pokaždé, když se statickou metodu <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> zaznamená identifikátor URI začínající řetězcem "http" nebo "https".</span><span class="sxs-lookup"><span data-stu-id="90b18-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="90b18-105">Ve většině případů **WebRequest** a **WebResponse** třídy poskytují všechny možnosti, které je nezbytné k odeslání požadavku, ale pokud potřebujete přístup k funkcím specifickým pro HTTP jako vlastnosti, můžete přetypovat Tyto třídy **HttpWebRequest** nebo **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="90b18-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="90b18-106">**HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakce požadavku a odpovědi HTTP a poskytují přístup k společné hlavičky HTTP.</span><span class="sxs-lookup"><span data-stu-id="90b18-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="90b18-107">Tyto třídy také podporují většinu funkcí protokolu HTTP 1.1, včetně paralelní zpracování, odesílání a přijímání dat do bloků dat, ověřování, předběžné ověření, šifrování, podpora proxy, ověření certifikátu serveru a připojení správy.</span><span class="sxs-lookup"><span data-stu-id="90b18-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="90b18-108">Vlastní hlavičky a není k dispozici prostřednictvím vlastností můžete uložené v a získat přístup prostřednictvím **záhlaví** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90b18-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="90b18-109">**HttpWebRequest** je výchozí třídou používané **WebRequest** a nemusí být před předáním identifikátor URI pro zaregistrovaný **WebRequest.Create** metoda.</span><span class="sxs-lookup"><span data-stu-id="90b18-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="90b18-110">Provedete aplikace následovat i přesměrování HTTP automaticky tak, že nastavíte <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> vlastnost **true** (výchozí).</span><span class="sxs-lookup"><span data-stu-id="90b18-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="90b18-111">Aplikace bude přesměrovávat žádosti a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečná webového prostředku, který odpověděl na požadavek.</span><span class="sxs-lookup"><span data-stu-id="90b18-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="90b18-112">Pokud nastavíte **AllowAutoRedirect** k **false**, vaše aplikace musí být schopný zvládnout přesměrování jako chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="90b18-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="90b18-113">Aplikace zobrazí chyby protokolu HTTP pomocí zachycování <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> nastavena na <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="90b18-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="90b18-114"><xref:System.Net.WebException.Response%2A> Obsahuje vlastnost **WebResponse** odeslané serverem a označuje skutečné došlo k chybě protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="90b18-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b18-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90b18-115">See also</span></span>

- [<span data-ttu-id="90b18-116">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="90b18-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="90b18-117">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="90b18-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="90b18-118">Postupy: Přístup k vlastnostem specifickým pro HTTP</span><span class="sxs-lookup"><span data-stu-id="90b18-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
