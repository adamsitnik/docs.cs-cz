---
ms.openlocfilehash: 023b7d8c5aa9d435d3493935b4439ae4262c85bb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65669595"
---
> [!CAUTION]
>  <span data-ttu-id="f94cc-101">Zabezpečení přístupu kódu a částečně důvěryhodný kód</span><span class="sxs-lookup"><span data-stu-id="f94cc-101">Code Access Security and Partially Trusted Code</span></span>  
>   
>  <span data-ttu-id="f94cc-102">Rozhraní .NET Framework poskytuje mechanismus pro vynucení různých úrovní důvěryhodnosti pro různý kód spuštěný ve stejné aplikaci, který se označuje jako zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="f94cc-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="f94cc-103">Zabezpečení přístupu kódu v rozhraní .NET Framework by se nemělo používat jako mechanismus pro vynucení hranic zabezpečení na základě původu kódu nebo jiného aspektu identity.</span><span class="sxs-lookup"><span data-stu-id="f94cc-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="f94cc-104">Naše doprovodné materiály aktualizujeme tak, aby odrážely skutečnost, že zabezpečení přístupu kódu a kód transparentní z hlediska zabezpečení se nebudou podporovat jako hranice zabezpečení s částečně důvěryhodným kódem, zejména s kódem neznámého původu.</span><span class="sxs-lookup"><span data-stu-id="f94cc-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="f94cc-105">Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="f94cc-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>  
>   
>  <span data-ttu-id="f94cc-106">Tyto zásady se vztahují na všechny verze rozhraní .NET Framework, ale nevztahují se na rozhraní .NET, které je součástí Silverlightu.</span><span class="sxs-lookup"><span data-stu-id="f94cc-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
