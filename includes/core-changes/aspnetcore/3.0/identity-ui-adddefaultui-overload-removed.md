---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522646"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="062bd-101">Identita: přetížení metody AddDefaultUI bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="062bd-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="062bd-102">Počínaje ASP.NET Core 3,0 <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> přetížení metody již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="062bd-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="062bd-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="062bd-103">Version introduced</span></span>

<span data-ttu-id="062bd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="062bd-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="062bd-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="062bd-105">Reason for change</span></span>

<span data-ttu-id="062bd-106">Tato změna byla výsledkem přijetí funkce statických webových prostředků.</span><span class="sxs-lookup"><span data-stu-id="062bd-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="062bd-107">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="062bd-107">Recommended action</span></span>

<span data-ttu-id="062bd-108">Místo přetížení volejte <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="062bd-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="062bd-109">Pokud používáte Bootstrap 3, přidejte také následující řádek do prvku `<PropertyGroup>` v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="062bd-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="062bd-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="062bd-110">Category</span></span>

<span data-ttu-id="062bd-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="062bd-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="062bd-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="062bd-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
