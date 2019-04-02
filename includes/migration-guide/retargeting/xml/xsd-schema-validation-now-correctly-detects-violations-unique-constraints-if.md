---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "50746287"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="d6ad1-101">Ověření schématu XSD nyní správně rozpozná porušení unikátních omezení, pokud složené klíče se používají a jeden klíč je prázdný</span><span class="sxs-lookup"><span data-stu-id="d6ad1-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d6ad1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d6ad1-102">Details</span></span>|<span data-ttu-id="d6ad1-103">Verze rozhraní .NET Framework 4.6 měl chybu, která způsobila ověření XSD není zjistit unikátních omezení na složených klíčích, pokud jeden z klíčů byla prázdná.</span><span class="sxs-lookup"><span data-stu-id="d6ad1-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="d6ad1-104">V rozhraní .NET Framework 4.6 je tento problém vyřešen.</span><span class="sxs-lookup"><span data-stu-id="d6ad1-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="d6ad1-105">Výsledkem bude více správné ověření, ale může také vést některé XML není ověřování, který už má.</span><span class="sxs-lookup"><span data-stu-id="d6ad1-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>|
|<span data-ttu-id="d6ad1-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d6ad1-106">Suggestion</span></span>|<span data-ttu-id="d6ad1-107">V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.5 (nebo starší) rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6ad1-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="d6ad1-108">Když mění se cílení na rozhraní .NET Framework 4.6, ale revize kódu se má počítat ujistit se, že duplicitní složených klíčů (jak je popsáno v popisu tento problém) se nepředpokládá ověření.</span><span class="sxs-lookup"><span data-stu-id="d6ad1-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>|
|<span data-ttu-id="d6ad1-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d6ad1-109">Scope</span></span>|<span data-ttu-id="d6ad1-110">Edge</span><span class="sxs-lookup"><span data-stu-id="d6ad1-110">Edge</span></span>|
|<span data-ttu-id="d6ad1-111">Version</span><span class="sxs-lookup"><span data-stu-id="d6ad1-111">Version</span></span>|<span data-ttu-id="d6ad1-112">4.6</span><span class="sxs-lookup"><span data-stu-id="d6ad1-112">4.6</span></span>|
|<span data-ttu-id="d6ad1-113">Type</span><span class="sxs-lookup"><span data-stu-id="d6ad1-113">Type</span></span>|<span data-ttu-id="d6ad1-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="d6ad1-114">Retargeting</span></span>|

