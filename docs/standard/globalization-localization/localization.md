---
title: Lokalizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbe7a2c4e920021c925a13ae8873124bfdb6fd67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683142"
---
# <a name="localization"></a><span data-ttu-id="35db1-102">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="35db1-102">Localization</span></span>

<span data-ttu-id="35db1-103">Lokalizace je proces převodu aplikační prostředky do lokalizované verze pro každou jazykovou verzi, která bude podporovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="35db1-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="35db1-104">By měl pokračujte krokem lokalizace až po dokončení [přezkoumání lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md) kroku ověřte, že globalizovaná aplikace je připravena k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="35db1-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="35db1-105">Aplikace, která jsou připravená pro lokalizaci rozdělen do dvou bloků koncepční: blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="35db1-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="35db1-106">Bloky uživatelského rozhraní obsahuje pouze lokalizovatelné uživatelského rozhraní prvky, jako jsou řetězce, chybové zprávy, dialogová okna, nabídek, prostředky vložených objektů a podobně pro neutrální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="35db1-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="35db1-107">Blok kódu obsahuje pouze kód aplikace, které bude využívat všechny podporované jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="35db1-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="35db1-108">Modul common language runtime podporuje model prostředků satelitních sestavení, oddělující spustitelného kódu vaší aplikace z jejích prostředků.</span><span class="sxs-lookup"><span data-stu-id="35db1-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="35db1-109">Další informace o implementaci tohoto modelu najdete v tématu [prostředky v prostředí .NET](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="35db1-109">For more information about implementing this model, see [Resources in .NET](../../../docs/framework/resources/index.md).</span></span>

<span data-ttu-id="35db1-110">Pro každou lokalizovanou verzi vaší aplikace přidáte nové satelitní sestavení, který obsahuje blok lokalizovaná uživatelská rozhraní přeložit na příslušný jazyk cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="35db1-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="35db1-111">Blok kódu pro všechny jazykové verze by měla zůstat stejná.</span><span class="sxs-lookup"><span data-stu-id="35db1-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="35db1-112">Kombinace lokalizovanou verzi bloku uživatelského rozhraní s blok kódu vytvoří lokalizovanou verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="35db1-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="35db1-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje nástroj Windows Forms Resource Editor (Winres.exe), umožňující rychle lokalizovat formuláře Windows pro cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="35db1-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="35db1-114">Informace o použití tohoto nástroje najdete v tématu [Winres.exe (Editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="35db1-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35db1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35db1-115">See also</span></span>

- [<span data-ttu-id="35db1-116">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="35db1-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="35db1-117">Vyhodnocení lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="35db1-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)
- [<span data-ttu-id="35db1-118">Globalizace</span><span class="sxs-lookup"><span data-stu-id="35db1-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="35db1-119">Prostředky v desktopových aplikacích</span><span class="sxs-lookup"><span data-stu-id="35db1-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
