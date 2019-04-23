---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219002"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="e8a7f-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="e8a7f-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="e8a7f-103">Bezpečnostní ověření typu handshake s potenciální souseda nebyla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e8a7f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e8a7f-104">Description</span></span>  
 <span data-ttu-id="e8a7f-105">Vyvolá se při pokusu o navázání připojení k sousedovi zabezpečené tohoto trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="e8a7f-106">K tomu může dojít z důvodu nedostatečné nebo nesprávné přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="e8a7f-107">Kanál PeerChannel rozpozná jeden typ tokenu pro silné identifikaci certifikáty X.509, které poskytují model využívá silné identity na základě typu ověřování a autorizaci, které je možné implementovat.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="e8a7f-108">Kanál PeerChannel také poskytuje podporu pro jednoduché aplikace pomocí hesla.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="e8a7f-109">Hesla je možné pouze do relace; položku Povolit nelze použít k provedení ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="e8a7f-110">Je to proto, že symetrický token, které sdílejí skupiny partnerských uzlů je obtížné a nevhodný pro účely ověření zdroje.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e8a7f-111">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="e8a7f-111">Troubleshooting</span></span>  
 <span data-ttu-id="e8a7f-112">Ujistěte se, že všechny sousední mají příslušná zabezpečovací přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e8a7f-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a7f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8a7f-113">See also</span></span>

- [<span data-ttu-id="e8a7f-114">Zabezpečení protokolem Peer Channel</span><span class="sxs-lookup"><span data-stu-id="e8a7f-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [<span data-ttu-id="e8a7f-115">Trasování</span><span class="sxs-lookup"><span data-stu-id="e8a7f-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e8a7f-116">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e8a7f-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e8a7f-117">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e8a7f-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
