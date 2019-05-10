---
title: 'Koncový bod: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9e0192ea600bb52abd555f2f83cfe8e96d3fe203
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619343"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="107ca-102">Koncový bod: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="107ca-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="107ca-103">Název čítače: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="107ca-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="107ca-104">Popis</span><span class="sxs-lookup"><span data-stu-id="107ca-104">Description</span></span>  
 <span data-ttu-id="107ca-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="107ca-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="107ca-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="107ca-106">Such problems include:</span></span>  
  
- <span data-ttu-id="107ca-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="107ca-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="107ca-108">Token klienta se nezdařilo ověřování (špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="107ca-108">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="107ca-109">Ověření podpisu se nezdařilo (zprávě někdo nemanipuloval).</span><span class="sxs-lookup"><span data-stu-id="107ca-109">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="107ca-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="107ca-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="107ca-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="107ca-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="107ca-112">Zpráva chybí některé požadované prvky (chybějící časového razítka nebo šifrovaného datového bloku).</span><span class="sxs-lookup"><span data-stu-id="107ca-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="107ca-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="107ca-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
