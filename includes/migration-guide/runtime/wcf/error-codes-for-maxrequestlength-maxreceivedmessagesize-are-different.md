---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235279"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="8c5ea-101">Kódy chyb pro maxRequestLength nebo maxReceivedMessageSize se liší</span><span class="sxs-lookup"><span data-stu-id="8c5ea-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8c5ea-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8c5ea-102">Details</span></span>|<span data-ttu-id="8c5ea-103">Zprávy ve službě WCF web služby hostované v Internetové informační služby (IIS) nebo vývojový Server ASP.NET, které překračují maxRequestLength (v technologii ASP.NET) nebo maxReceivedMessageSize (v WCF) mají různé chybové codeThe HTTP stavový kód byl změněn z 400 (Chybný požadavek ) na 413 (příliš velký požadavek Entity) a zprávy, které překračují buď nastavení maxReceivedMessageSize nebo maxRequestLength vyvolat <xref:System.ServiceModel.ProtocolException?displayProperty=name> výjimky.</span><span class="sxs-lookup"><span data-stu-id="8c5ea-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=name> exception.</span></span> <span data-ttu-id="8c5ea-104">To zahrnuje případy, ve kterých je režim přenosu nedochází.</span><span class="sxs-lookup"><span data-stu-id="8c5ea-104">This includes cases in which the transfer mode is Streamed.</span></span>|
|<span data-ttu-id="8c5ea-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="8c5ea-105">Suggestion</span></span>|<span data-ttu-id="8c5ea-106">Tato změna usnadňuje ladění v případech, kde délka zprávy překročí limity povolené rozhraním ASP.NET nebo WCF. Je třeba upravit jakýkoli kód, který provádí zpracování založené na stavovém kódu HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="8c5ea-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>|
|<span data-ttu-id="8c5ea-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8c5ea-107">Scope</span></span>|<span data-ttu-id="8c5ea-108">Edge</span><span class="sxs-lookup"><span data-stu-id="8c5ea-108">Edge</span></span>|
|<span data-ttu-id="8c5ea-109">Version</span><span class="sxs-lookup"><span data-stu-id="8c5ea-109">Version</span></span>|<span data-ttu-id="8c5ea-110">4.5</span><span class="sxs-lookup"><span data-stu-id="8c5ea-110">4.5</span></span>|
|<span data-ttu-id="8c5ea-111">Type</span><span class="sxs-lookup"><span data-stu-id="8c5ea-111">Type</span></span>|<span data-ttu-id="8c5ea-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8c5ea-112">Runtime</span></span>|
