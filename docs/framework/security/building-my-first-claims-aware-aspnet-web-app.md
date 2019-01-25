---
title: Vytváření Moje první aplikace s deklaracemi identity v prostředí ASP.NET
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 67489b2bb93719d8182159fbc91703399d5e8bc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588961"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="756fc-102">Vytváření Moje první aplikace s deklaracemi identity v prostředí ASP.NET</span><span class="sxs-lookup"><span data-stu-id="756fc-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="756fc-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="756fc-103">Applies To</span></span>  
  
-   <span data-ttu-id="756fc-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="756fc-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="756fc-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="756fc-105">ASP.NET</span></span>  
  
 <span data-ttu-id="756fc-106">Toto téma popisuje, jak pomocí technologie WIF vytvářet webové aplikace ASP.NET pracující s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="756fc-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="756fc-107">Scénář aplikací pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná aplikace, koncový uživatel a služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="756fc-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="756fc-108">Tento scénář zachycuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="756fc-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="756fc-109">![Technologie WIF základní webovou aplikaci](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="756fc-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="756fc-110">Aplikace pracující s deklaracemi zjišťují pomocí technologie WIF neověřené žádosti a směrují je na službu STS.</span><span class="sxs-lookup"><span data-stu-id="756fc-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="756fc-111">Koncový uživatel poskytne službě STS své přihlašovací údaje a po úspěšném ověření uživatele vystaví služba STS token.</span><span class="sxs-lookup"><span data-stu-id="756fc-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="756fc-112">Uživatel je přesměrován ze služby STS na aplikaci pracující s deklaracemi a token vystavený službou STS je přitom obsažen v žádosti.</span><span class="sxs-lookup"><span data-stu-id="756fc-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="756fc-113">Aplikace pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="756fc-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="756fc-114">Aplikace pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="756fc-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="756fc-115">Vývojáři používají příslušná rozhraní API technologie WIF a typy, například **Claimsprincipal** pro potřeby aplikace, jako je například implementace autorizace.</span><span class="sxs-lookup"><span data-stu-id="756fc-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="756fc-116">Počínaje .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="756fc-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="756fc-117">V rozhraní .NET, což usnadňuje používání deklarací tříd WIF přímo k dispozici v rozhraní umožňuje mnohem hlubší integraci deklarovaných identit.</span><span class="sxs-lookup"><span data-stu-id="756fc-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="756fc-118">Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti.</span><span class="sxs-lookup"><span data-stu-id="756fc-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="756fc-119">Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="756fc-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="756fc-120">STS je služba, která vystavuje tokeny po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="756fc-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="756fc-121">Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:</span><span class="sxs-lookup"><span data-stu-id="756fc-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   [<span data-ttu-id="756fc-122">Active Directory Federation Services (AD FS) 2.0</span><span class="sxs-lookup"><span data-stu-id="756fc-122">Active Directory Federation Services (AD FS) 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [<span data-ttu-id="756fc-123">Windows Azure Access Control Service (ACS)</span><span class="sxs-lookup"><span data-stu-id="756fc-123">Windows Azure Access Control Service (ACS)</span></span>](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 <span data-ttu-id="756fc-124">Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře.</span><span class="sxs-lookup"><span data-stu-id="756fc-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="756fc-125">Služba ACS je cloudová služba, nabízená v rámci platformy Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="756fc-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="756fc-126">Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS.</span><span class="sxs-lookup"><span data-stu-id="756fc-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="756fc-127">Například můžete použít místní službu STS, která je součástí [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) což je volně k dispozici online.</span><span class="sxs-lookup"><span data-stu-id="756fc-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="756fc-128">Pokud chcete pomocí technologie WIF vytvořit svou první aplikaci ASP.NET pracující s deklaracemi, postupujte podle pokynů v jednom z následujících témat:</span><span class="sxs-lookup"><span data-stu-id="756fc-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="756fc-129">Postupy: Vytvoření webové aplikace ASP.NET MVC s deklaracemi identity pomocí technologie WIF</span><span class="sxs-lookup"><span data-stu-id="756fc-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="756fc-130">Postupy: Sestavení s deklaracemi identity aplikace webových formulářů ASP.NET pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="756fc-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="756fc-131">Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="756fc-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="756fc-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="756fc-132">See also</span></span>
- [<span data-ttu-id="756fc-133">Začínáme s WIF</span><span class="sxs-lookup"><span data-stu-id="756fc-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
