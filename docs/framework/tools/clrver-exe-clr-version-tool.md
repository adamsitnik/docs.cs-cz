---
title: Clrver.exe (nástroj verze CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5543e49ea44c20a536a7097277b246d4041522a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735432"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="3ef4c-102">Clrver.exe (nástroj verze CLR)</span><span class="sxs-lookup"><span data-stu-id="3ef4c-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="3ef4c-103">Nástroj CLR Version (Clrver.exe) vypíše všechny verze modulu Common Language Runtime (CLR) nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="3ef4c-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="3ef4c-105">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="3ef4c-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="3ef4c-106">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3ef4c-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="3ef4c-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="3ef4c-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef4c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ef4c-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="3ef4c-109">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3ef4c-109">Options</span></span>  
  
|<span data-ttu-id="3ef4c-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="3ef4c-110">Option</span></span>|<span data-ttu-id="3ef4c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3ef4c-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="3ef4c-112">Zobrazí všechny procesy v počítači využívající modul CLR.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="3ef4c-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="3ef4c-113">*pid*</span></span>|<span data-ttu-id="3ef4c-114">Zobrazí verze modulu CLR využívané procesem se zadaným identifikátorem ID procesu (PID).</span><span class="sxs-lookup"><span data-stu-id="3ef4c-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="3ef4c-115">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ef4c-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ef4c-116">Remarks</span></span>  
 <span data-ttu-id="3ef4c-117">Při volání nástroje Clrver.exe bez použití možností se zobrazí všechny nainstalované verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="3ef4c-118">Pokud zadáte identifikátor PID pro jiného uživatele, musíte mít oprávnění správce, chcete-li získat informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ef4c-119">Nástroj Řízení uživatelských účtů (UAC) v systému Windows Vista a novějším určuje oprávnění uživatele.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="3ef4c-120">Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="3ef4c-121">Ve výchozím nastavení máte roli standardního uživatele.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="3ef4c-122">Chcete-li spustit kód vyžadující oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="3ef4c-123">Můžete tak učinit při spouštění příkazového řádku kliknutím pravým tlačítkem myši na ikonu příkazového řádku a označením, že chcete nástroj spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="3ef4c-124">Při pokusu o určení verze modulu CLR pro procesy SYSTEM, LOCAL SERVICE a NETWORK SERVICE dojde k zobrazení zprávy, že PID neexistuje.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3ef4c-125">Příklady</span><span class="sxs-lookup"><span data-stu-id="3ef4c-125">Examples</span></span>  
 <span data-ttu-id="3ef4c-126">Následující příkaz zobrazí všechny verze modulu CLR nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="3ef4c-127">Následující příkaz zobrazí verzi modulu CLR používanou procesem 128.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="3ef4c-128">Následující příkaz zobrazí všechny spravované procesy a verzi modulu CLR, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="3ef4c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ef4c-129">See also</span></span>
- [<span data-ttu-id="3ef4c-130">Nástroje</span><span class="sxs-lookup"><span data-stu-id="3ef4c-130">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="3ef4c-131">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="3ef4c-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
