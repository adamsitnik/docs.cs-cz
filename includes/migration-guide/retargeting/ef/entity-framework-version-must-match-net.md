---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774341"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="867f0-101">Entity Framework verze musí odpovídat verzi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="867f0-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="867f0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="867f0-102">Details</span></span>|<span data-ttu-id="867f0-103">S verzí rozhraní .NET framework by si měly odpovídat verzi rozhraní entity framework.</span><span class="sxs-lookup"><span data-stu-id="867f0-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="867f0-104">Entity Framework 5 se doporučuje pro rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="867f0-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="867f0-105">Existují některé známé problémy s platformou EF s 4.x v projektu rozhraní .NET Framework 4.5 kolem <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="867f0-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="867f0-106">V rozhraní .NET 4.5 tyto se přesunuly na jiné sestavení, takže dojde k problémům určující, které poznámky k použití.</span><span class="sxs-lookup"><span data-stu-id="867f0-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="867f0-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="867f0-107">Suggestion</span></span>|<span data-ttu-id="867f0-108">Upgrade na rozhraní Entity Framework 5 pro rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="867f0-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="867f0-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="867f0-109">Scope</span></span>|<span data-ttu-id="867f0-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="867f0-110">Major</span></span>|
|<span data-ttu-id="867f0-111">Version</span><span class="sxs-lookup"><span data-stu-id="867f0-111">Version</span></span>|<span data-ttu-id="867f0-112">4.5</span><span class="sxs-lookup"><span data-stu-id="867f0-112">4.5</span></span>|
|<span data-ttu-id="867f0-113">Type</span><span class="sxs-lookup"><span data-stu-id="867f0-113">Type</span></span>|<span data-ttu-id="867f0-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="867f0-114">Retargeting</span></span>|
