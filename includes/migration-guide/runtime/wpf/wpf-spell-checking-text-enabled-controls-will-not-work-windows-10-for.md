---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234129"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="f81b8-101">WPF kontroly pravopisu v textu povoleno ovládací prvky nebudou fungovat ve Windows 10 pro jazyky, které nejsou v seznamu jazyk operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f81b8-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f81b8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f81b8-102">Details</span></span>|<span data-ttu-id="f81b8-103">Při spuštění ve Windows 10, nástroj pro kontrolu pravopisu nemusí fungovat pro ovládací prvky WPF textu povoleno, protože jsou k dispozici pouze pro jazyky, které jsou k dispozici v seznamu jazyků funkce platformy pro kontrolu pravopisu. Ve Windows 10 když jazyk se přidá do seznamu dostupných klávesnice, Windows automaticky stáhne a nainstaluje odpovídající funkce na vyžádání (zámořských) balíčku, které poskytuje funkce pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="f81b8-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="f81b8-104">Přidáním jazyk do seznamu jazyků bude podporovaný nástroj pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="f81b8-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="f81b8-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f81b8-105">Suggestion</span></span>|<span data-ttu-id="f81b8-106">Mějte na paměti, že jazyk nebo text, který má být kontrola pravopisu je nutné přidat jako jazyk pro kontrolu pravopisu pro práci ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f81b8-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="f81b8-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f81b8-107">Scope</span></span>|<span data-ttu-id="f81b8-108">Edge</span><span class="sxs-lookup"><span data-stu-id="f81b8-108">Edge</span></span>|
|<span data-ttu-id="f81b8-109">Version</span><span class="sxs-lookup"><span data-stu-id="f81b8-109">Version</span></span>|<span data-ttu-id="f81b8-110">4.6</span><span class="sxs-lookup"><span data-stu-id="f81b8-110">4.6</span></span>|
|<span data-ttu-id="f81b8-111">Type</span><span class="sxs-lookup"><span data-stu-id="f81b8-111">Type</span></span>|<span data-ttu-id="f81b8-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f81b8-112">Runtime</span></span>|
