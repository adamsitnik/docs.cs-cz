---
title: Prostředky pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: KrzysztofCwalina
ms.openlocfilehash: 44627aafd9ec779625413a0862412a8f6c408109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497598"
---
# <a name="naming-resources"></a><span data-ttu-id="16423-102">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="16423-102">Naming Resources</span></span>
<span data-ttu-id="16423-103">Protože lokalizovatelné prostředky může být odkazováno prostřednictvím určitých objektů, jako kdyby byly vlastnosti, pokyny pro pojmenování prostředků jsou podobné pokyny pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16423-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="16423-104">**✓ DO** použít PascalCasing v klíčů prostředku.</span><span class="sxs-lookup"><span data-stu-id="16423-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="16423-105">**✓ DO** zadat popisný místo krátké identifikátory.</span><span class="sxs-lookup"><span data-stu-id="16423-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="16423-106">**X DO NOT** používat klíčová slova jazyka hlavní jazyky CLR.</span><span class="sxs-lookup"><span data-stu-id="16423-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="16423-107">**✓ DO** použijte pouze alfanumerické znaky a podtržítka v pojmenování prostředky.</span><span class="sxs-lookup"><span data-stu-id="16423-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="16423-108">**✓ DO** použít následující konvence pro prostředků zprávy výjimek.</span><span class="sxs-lookup"><span data-stu-id="16423-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="16423-109">Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:</span><span class="sxs-lookup"><span data-stu-id="16423-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="16423-110">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="16423-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="16423-111">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="16423-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16423-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16423-112">See also</span></span>

- [<span data-ttu-id="16423-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="16423-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="16423-114">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="16423-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
