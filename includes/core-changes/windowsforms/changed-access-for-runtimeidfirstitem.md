---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003020"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="b87f1-101">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="b87f1-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="b87f1-102">Od verze .NET Core 3,0 RC1 se dostupnost `AccessibleObject.RuntimeIDFirstItem` změnila z `protected` na `internal`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b87f1-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="b87f1-103">Change description</span></span>

<span data-ttu-id="b87f1-104">Od verze .NET Core 3,0 Preview 4 bylo pole `AccessibleObject.RuntimeIDFirstItem` `protected`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="b87f1-105">Od verze .NET Core 3,0 RC1 se změnila z `protected` na `internal`, aby se zarovnala přístupnosti pole v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b87f1-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b87f1-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b87f1-106">Version introduced</span></span>

<span data-ttu-id="b87f1-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="b87f1-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b87f1-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b87f1-108">Recommended action</span></span>

<span data-ttu-id="b87f1-109">Tato změna může mít vliv na to, jestli jste vyvinuli aplikaci .NET Core s typem, který je odvozený od <xref:System.Windows.Forms.AccessibleObject> a přistupuje k poli `RuntimeIDFirstItem`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="b87f1-110">V takovém případě můžete definovat místní konstantu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b87f1-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="b87f1-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b87f1-111">Category</span></span>

<span data-ttu-id="b87f1-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b87f1-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b87f1-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b87f1-113">Affected APIs</span></span>

- <span data-ttu-id="b87f1-114">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b87f1-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->