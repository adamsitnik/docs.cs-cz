---
ms.openlocfilehash: 9bf6972812bdf4a385b99fe34d2cd3cd8a91c8cf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761015"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="85d3c-101">ClickOnce podporuje SHA-256 na 4.0 cílové aplikace</span><span class="sxs-lookup"><span data-stu-id="85d3c-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="85d3c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="85d3c-102">Details</span></span>|<span data-ttu-id="85d3c-103">Dříve by aplikace ClickOnce s certifikátem podepsané pomocí algoritmu SHA-256 vyžaduje rozhraní .NET Framework 4.5 nebo novější bude k dispozici, i v případě, že aplikace cílené 4.0.</span><span class="sxs-lookup"><span data-stu-id="85d3c-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="85d3c-104">Nyní aplikace ClickOnce cílové rozhraní .NET Framework 4.0 lze spustit v rozhraní .NET Framework 4.0, i v případě, že podepsané pomocí algoritmu SHA-256.</span><span class="sxs-lookup"><span data-stu-id="85d3c-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="85d3c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="85d3c-105">Suggestion</span></span>|<span data-ttu-id="85d3c-106">Tato změna odebere dané závislosti a umožňuje certifikáty SHA-256 k podepisování aplikací ClickOnce, určených pro rozhraní .NET Framework 4 a dřívějších verzích.</span><span class="sxs-lookup"><span data-stu-id="85d3c-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="85d3c-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="85d3c-107">Scope</span></span>|<span data-ttu-id="85d3c-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="85d3c-108">Minor</span></span>|
|<span data-ttu-id="85d3c-109">Version</span><span class="sxs-lookup"><span data-stu-id="85d3c-109">Version</span></span>|<span data-ttu-id="85d3c-110">4.6</span><span class="sxs-lookup"><span data-stu-id="85d3c-110">4.6</span></span>|
|<span data-ttu-id="85d3c-111">Type</span><span class="sxs-lookup"><span data-stu-id="85d3c-111">Type</span></span>|<span data-ttu-id="85d3c-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="85d3c-112">Retargeting</span></span>|

