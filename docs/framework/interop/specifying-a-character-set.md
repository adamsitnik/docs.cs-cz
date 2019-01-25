---
title: Určení sady znaků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45810390ced8584ea7b37908a9e4af8d3da73f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549847"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="465b8-102">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="465b8-102">Specifying a Character Set</span></span>
<span data-ttu-id="465b8-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězce a určuje, jak vyvolání platformy najde názvy funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="465b8-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="465b8-104">Toto téma popisuje, jak chování.</span><span class="sxs-lookup"><span data-stu-id="465b8-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="465b8-105">Některá rozhraní API exportovat dvě verze funkcí, které přijímají řetězcové argumenty: úzký (ANSI) a celý (Unicode).</span><span class="sxs-lookup"><span data-stu-id="465b8-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="465b8-106">Rozhraní API systému Win32, zahrnuje následující názvy vstupní bod **MessageBox** funkce:</span><span class="sxs-lookup"><span data-stu-id="465b8-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="465b8-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="465b8-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="465b8-108">Poskytuje 1bajtový ANSI formátování, odlišené "A" připojenou k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="465b8-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="465b8-109">Volání **MessageBoxA** vždy zařazování řetězců v ANSI formátování, což je běžné na platformách Windows 95 a Windows 98.</span><span class="sxs-lookup"><span data-stu-id="465b8-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="465b8-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="465b8-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="465b8-111">Obsahuje formátování 2bajtových znaků Unicode, odlišené "W" připojenou k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="465b8-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="465b8-112">Volání **funkce** vždy zařazovat řetězce ve formátu Unicode, což je běžné na platformách Windows NT, Windows 2000 a Windows XP.</span><span class="sxs-lookup"><span data-stu-id="465b8-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="465b8-113">Zařazování řetězců a shoda názvu</span><span class="sxs-lookup"><span data-stu-id="465b8-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="465b8-114">**CharSet** pole přijímá následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="465b8-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="465b8-115">**CharSet.Ansi** (výchozí hodnota)</span><span class="sxs-lookup"><span data-stu-id="465b8-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="465b8-116">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="465b8-116">String marshaling</span></span>  
  
     <span data-ttu-id="465b8-117">Vyvolání platformy marshals řetězců z jejich spravovaných formátu (Unicode) na ANSI formát.</span><span class="sxs-lookup"><span data-stu-id="465b8-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="465b8-118">Shoda názvu</span><span class="sxs-lookup"><span data-stu-id="465b8-118">Name matching</span></span>  
  
     <span data-ttu-id="465b8-119">Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="465b8-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="465b8-120">Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="465b8-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="465b8-121">Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá unmangled alias vyvolání platformy (**MessageBox**), pak bude rozdělený název (**MessageBoxA**) Pokud se nenajde unmangled alias.</span><span class="sxs-lookup"><span data-stu-id="465b8-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="465b8-122">Všimněte si, že ANSI shoda názvu chování se liší od chování porovnávání název kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="465b8-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="465b8-123">**CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="465b8-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="465b8-124">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="465b8-124">String marshaling</span></span>  
  
     <span data-ttu-id="465b8-125">Kopie řetězce z jejich spravovaných formátu (Unicode) do Unicode formátu vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="465b8-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="465b8-126">Shoda názvu</span><span class="sxs-lookup"><span data-stu-id="465b8-126">Name matching</span></span>  
  
     <span data-ttu-id="465b8-127">Když **ExactSpelling** pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="465b8-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="465b8-128">Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="465b8-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="465b8-129">Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá pozměněný název vyvolání platformy (**funkce**), pak bude unmangled alias (**MessageBox**) Pokud se nenajde pozměnění názvu.</span><span class="sxs-lookup"><span data-stu-id="465b8-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="465b8-130">Všimněte si, že Unicode shoda názvu chování se liší od chování porovnávání název ANSI.</span><span class="sxs-lookup"><span data-stu-id="465b8-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="465b8-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="465b8-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="465b8-132">Vyvolání platformy zvolí mezi formáty ANSI a Unicode v době běhu, založené na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="465b8-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="465b8-133">Určení znakové sady v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b8-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="465b8-134">Následující příklad deklaruje **MessageBox** funkce tři vícekrát, pokaždé, když s jinou znakovou sadu chování.</span><span class="sxs-lookup"><span data-stu-id="465b8-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="465b8-135">Znakové sady chování v jazyce Visual Basic můžete zadat tak, že přidáte **Ansi**, **Unicode**, nebo **automaticky** – klíčové slovo do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="465b8-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="465b8-136">Pokud vynecháte – klíčové slovo znakové sady, jak je tomu v prvním příkazu deklarace, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole výchozí znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="465b8-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="465b8-137">Druhý a třetí příkazy v příkladu explicitně zadat znakovou sadu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="465b8-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="465b8-138">Určení znakové sady v C# a C++</span><span class="sxs-lookup"><span data-stu-id="465b8-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="465b8-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identifikuje základní znakovou sadu ANSI nebo Unicode.</span><span class="sxs-lookup"><span data-stu-id="465b8-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="465b8-140">Znakové sady, které řídí, jak by měly být zařazeny řetězcové argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="465b8-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="465b8-141">Použijte jednu z následujících forem udávajících znakové sady:</span><span class="sxs-lookup"><span data-stu-id="465b8-141">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 <span data-ttu-id="465b8-142">Následující příklad ukazuje tři spravované definice **MessageBox** funkce s atributy k určení sady znaků.</span><span class="sxs-lookup"><span data-stu-id="465b8-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="465b8-143">V první definici podle jeho vynechání **CharSet** pole výchozí znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="465b8-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="465b8-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="465b8-144">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="465b8-145">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="465b8-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="465b8-146">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="465b8-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="465b8-147">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="465b8-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
