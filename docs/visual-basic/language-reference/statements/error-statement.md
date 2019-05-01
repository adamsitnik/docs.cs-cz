---
title: Error – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982394"
---
# <a name="error-statement"></a><span data-ttu-id="e7953-102">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="e7953-102">Error Statement</span></span>
<span data-ttu-id="e7953-103">Simuluje výskyt chyby.</span><span class="sxs-lookup"><span data-stu-id="e7953-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7953-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7953-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="e7953-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e7953-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="e7953-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e7953-106">Required.</span></span> <span data-ttu-id="e7953-107">Může být libovolné platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="e7953-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7953-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7953-108">Remarks</span></span>  
 <span data-ttu-id="e7953-109">`Error` Příkaz je podporován z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="e7953-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="e7953-110">V novém kódu, zejména při vytváření objektů, použijte `Err` objektu `Raise` metoda vygeneruje chyby za běhu.</span><span class="sxs-lookup"><span data-stu-id="e7953-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="e7953-111">Pokud `errornumber` je definován `Error` příkaz volá obslužná rutina chyb po vlastnosti `Err` objektu jsou přiřazeny následující výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e7953-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="e7953-112">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e7953-112">Property</span></span>|<span data-ttu-id="e7953-113">Value</span><span class="sxs-lookup"><span data-stu-id="e7953-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="e7953-114">Hodnota zadaná jako argument `Error` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e7953-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="e7953-115">Může být libovolné platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="e7953-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="e7953-116">Název aktuálního projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e7953-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="e7953-117">Výraz odpovídající návratovou hodnotu z řetězce `Error` funkce pro zadaný rozbočovač `Number`, pokud existuje tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="e7953-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="e7953-118">Pokud řetězec neexistuje, `Description` obsahuje řetězec nulové délky ("").</span><span class="sxs-lookup"><span data-stu-id="e7953-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="e7953-119">Plně kvalifikovaný jednotky, cestu a název souboru odpovídající souboru nápovědy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e7953-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="e7953-120">Odpovídající Nápověda jazyka Visual Basic ID kontextu pro příslušné chyby do souboru `Number` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e7953-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="e7953-121">Nula.</span><span class="sxs-lookup"><span data-stu-id="e7953-121">Zero.</span></span>|  
  
 <span data-ttu-id="e7953-122">Pokud neexistuje žádná obslužná rutina chyby, nebo pokud je zapnuta žádná chybová zpráva se vytvoří a zobrazí z `Err` vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="e7953-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7953-123">Některé hostování aplikací Visual Basic nelze vytvořit objekty.</span><span class="sxs-lookup"><span data-stu-id="e7953-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="e7953-124">V dokumentaci k hostitelské aplikace k určení, zda je možné vytvořit tříd a objektů.</span><span class="sxs-lookup"><span data-stu-id="e7953-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7953-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7953-125">Example</span></span>  
 <span data-ttu-id="e7953-126">V tomto příkladu `Error` příkaz k vygenerování číslo chyby 11.</span><span class="sxs-lookup"><span data-stu-id="e7953-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="e7953-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7953-127">Requirements</span></span>  
 <span data-ttu-id="e7953-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="e7953-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="e7953-129">**Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="e7953-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7953-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7953-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="e7953-131">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="e7953-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="e7953-132">Příkaz Resume</span><span class="sxs-lookup"><span data-stu-id="e7953-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="e7953-133">Chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="e7953-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
