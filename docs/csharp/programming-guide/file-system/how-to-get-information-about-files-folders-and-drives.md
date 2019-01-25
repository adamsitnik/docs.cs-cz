---
title: 'Postupy: Získání informací o souborech, složkách a jednotkách - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 7c122f0d342acb3708072be89e08c7465a654815
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660382"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="789e4-102">Postupy: Získání informací o souborech, složkách a jednotkách (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="789e4-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="789e4-103">Informace o systému souborů v rozhraní .NET Framework, přístupné pomocí následující třídy:</span><span class="sxs-lookup"><span data-stu-id="789e4-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="789e4-104"><xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy představují soubor nebo adresář a obsahovat vlastnosti, které vystavit hodně atributů souborů, které jsou podporovány v systému souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="789e4-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="789e4-105">Také obsahují metody pro otevření, zavření, přesunutí nebo odstranění souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="789e4-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="789e4-106">Instance těchto tříd můžete vytvořit tím, že předáte řetězec představující název souboru, složce nebo jednotce v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="789e4-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="789e4-107">Názvy souborů, složek nebo jednotky můžete také získat pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="789e4-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="789e4-108"><xref:System.IO.Directory?displayProperty=nameWithType> a <xref:System.IO.File?displayProperty=nameWithType> třídy poskytují statické metody pro načtení informací o adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="789e4-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="789e4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="789e4-109">Example</span></span>  
 <span data-ttu-id="789e4-110">Následující příklad ukazuje různé způsoby, jak získat přístup k informacím o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="789e4-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="789e4-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="789e4-111">Robust Programming</span></span>  
 <span data-ttu-id="789e4-112">Při zpracování řetězce zadaného uživatelem cesty by měl také zpracování výjimek byly splněny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="789e4-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="789e4-113">Název souboru je poškozený.</span><span class="sxs-lookup"><span data-stu-id="789e4-113">The file name is malformed.</span></span> <span data-ttu-id="789e4-114">Například obsahuje neplatné znaky nebo pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="789e4-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="789e4-115">Název souboru má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="789e4-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="789e4-116">Název souboru je delší než maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="789e4-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="789e4-117">Název souboru obsahuje dvojtečku (:).</span><span class="sxs-lookup"><span data-stu-id="789e4-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="789e4-118">Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru `Exists` vrátí metoda `false` bez ohledu na to, zda cesta existuje, metoda nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="789e4-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789e4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="789e4-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="789e4-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="789e4-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="789e4-121">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="789e4-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
