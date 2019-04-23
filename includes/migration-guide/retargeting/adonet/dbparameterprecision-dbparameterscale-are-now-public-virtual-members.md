---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234652"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="7eb8e-101">DbParameter.Precision a DbParameter.Scale jsou teď virtuální veřejné členy</span><span class="sxs-lookup"><span data-stu-id="7eb8e-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7eb8e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7eb8e-102">Details</span></span>|<span data-ttu-id="7eb8e-103"><xref:System.Data.Common.DbParameter.Precision> a <xref:System.Data.Common.DbParameter.Scale> jsou implementovány jako virtuální veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="7eb8e-104">Nahrazují odpovídající implementace explicitního rozhraní <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="7eb8e-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7eb8e-105">Suggestion</span></span>|<span data-ttu-id="7eb8e-106">Při opětovné sestavování databáze poskytovatele ADO.NET, bude vyžadovat tyto rozdíly – klíčové slovo 'override' má použít u vlastnosti hodnot Precision a Scale.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="7eb8e-107">To je jenom nutné, když znovu sestavení součástí; existující binární soubory budou nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="7eb8e-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="7eb8e-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7eb8e-108">Scope</span></span>|<span data-ttu-id="7eb8e-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="7eb8e-109">Minor</span></span>|
|<span data-ttu-id="7eb8e-110">Version</span><span class="sxs-lookup"><span data-stu-id="7eb8e-110">Version</span></span>|<span data-ttu-id="7eb8e-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7eb8e-111">4.5.1</span></span>|
|<span data-ttu-id="7eb8e-112">Type</span><span class="sxs-lookup"><span data-stu-id="7eb8e-112">Type</span></span>|<span data-ttu-id="7eb8e-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="7eb8e-113">Retargeting</span></span>|
|<span data-ttu-id="7eb8e-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7eb8e-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
