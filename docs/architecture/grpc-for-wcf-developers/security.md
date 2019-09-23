---
title: Zabezpečení v gRPC aplikacích – gRPC pro vývojáře WCF
description: Přehled ověřování volání a kanálu a autorizaci v gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184139"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="70f65-103">Zabezpečení v aplikacích gRPC</span><span class="sxs-lookup"><span data-stu-id="70f65-103">Security in gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="70f65-104">V jakémkoli scénáři reálného světa je zabezpečení aplikací a služeb zásadní.</span><span class="sxs-lookup"><span data-stu-id="70f65-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="70f65-105">Zabezpečení pokrývá tři klíčové oblasti: šifrování síťového provozu, aby se zabránilo jeho zachycení nesprávnými aktéry. ověřování klientů a serverů za účelem vytvoření identity a vztahu důvěryhodnosti; a autorizace klientů pro řízení přístupu k systémům a uplatnění oprávnění na základě identity.</span><span class="sxs-lookup"><span data-stu-id="70f65-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="70f65-106">**Ověřování** se týká vytvoření identity klienta nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="70f65-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="70f65-107">K určení toho, jestli má klient oprávnění pro přístup k prostředku nebo k vystavení příkazu, se jedná o **autorizaci** .</span><span class="sxs-lookup"><span data-stu-id="70f65-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="70f65-108">Tato kapitola se zabývá zařízeními pro ověřování a autorizaci v gRPC pro ASP.NET Core a zabývá se zabezpečením sítě pomocí šifrovaných připojení TLS.</span><span class="sxs-lookup"><span data-stu-id="70f65-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="70f65-109">Ověřování a autorizace WCF</span><span class="sxs-lookup"><span data-stu-id="70f65-109">WCF authentication and authorization</span></span>

<span data-ttu-id="70f65-110">Ověřování a autorizace ve službě WCF byly zpracovávány různými způsoby v závislosti na používaných přenosech a vazbách.</span><span class="sxs-lookup"><span data-stu-id="70f65-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="70f65-111">Služba WCF podporuje různé standardy\* protokolu WS-Security a ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo NetTcp Services mezi systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="70f65-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="70f65-112">ověřování a autorizace gRPC</span><span class="sxs-lookup"><span data-stu-id="70f65-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="70f65-113">ověřování a autorizace gRPC funguje na dvou úrovních.</span><span class="sxs-lookup"><span data-stu-id="70f65-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="70f65-114">Ověřování/autorizace na úrovni volání je obvykle zpracováváno pomocí tokenů, které jsou použity v metadatech, když je provedeno volání.</span><span class="sxs-lookup"><span data-stu-id="70f65-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="70f65-115">Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení, a může také zahrnovat ověřování na úrovni volání/přihlašovací údaje autorizace pro automatické použití na každé volání kanálu.</span><span class="sxs-lookup"><span data-stu-id="70f65-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="70f65-116">K zabezpečení služby můžete použít jeden nebo oba tyto mechanismy.</span><span class="sxs-lookup"><span data-stu-id="70f65-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="70f65-117">ASP.NET Core implementace gRPC podporuje ověřování a autorizaci pomocí většiny standardních ASP.NET Core mechanismů:</span><span class="sxs-lookup"><span data-stu-id="70f65-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="70f65-118">Volání ověřování</span><span class="sxs-lookup"><span data-stu-id="70f65-118">Call authentication</span></span>
  - <span data-ttu-id="70f65-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="70f65-119">Azure Active Directory</span></span>
  - <span data-ttu-id="70f65-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="70f65-120">IdentityServer</span></span>
  - <span data-ttu-id="70f65-121">Nosný token JWT</span><span class="sxs-lookup"><span data-stu-id="70f65-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="70f65-122">OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="70f65-122">OAuth 2.0</span></span>
  - <span data-ttu-id="70f65-123">OpenID připojit</span><span class="sxs-lookup"><span data-stu-id="70f65-123">OpenID Connect</span></span>
  - <span data-ttu-id="70f65-124">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="70f65-124">WS-Federation</span></span>
- <span data-ttu-id="70f65-125">Ověřování kanálu</span><span class="sxs-lookup"><span data-stu-id="70f65-125">Channel authentication</span></span>
  - <span data-ttu-id="70f65-126">Certifikát klienta</span><span class="sxs-lookup"><span data-stu-id="70f65-126">Client Certificate</span></span>

<span data-ttu-id="70f65-127">Metody ověřování volání jsou všechny založené na *tokenech*.</span><span class="sxs-lookup"><span data-stu-id="70f65-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="70f65-128">Jediným skutečným rozdílem je způsob, jakým se generuje token, a knihovny, které slouží k ověření tokenů ve službě ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="70f65-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="70f65-129">Další informace najdete v [dokumentaci k ověřování a autorizaci na Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="70f65-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="70f65-130">Při použití gRPC prostřednictvím připojení HTTP/2 zašifrovaného protokolem TLS bude veškerý provoz mezi klienty a servery zašifrovaný i v případě, že nepoužíváte ověřování na úrovni kanálu.</span><span class="sxs-lookup"><span data-stu-id="70f65-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="70f65-131">V této kapitole se dozvíte, jak použít přihlašovací údaje pro volání a přihlašovací údaje kanálu ke službě gRPC a jak pomocí přihlašovacích údajů z klienta .NET Core gRPC ověřit pomocí služby.</span><span class="sxs-lookup"><span data-stu-id="70f65-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="70f65-132">[Předchozí](client-libraries.md)
>[Další](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="70f65-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>