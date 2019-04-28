---
title: Systém souborů a registru – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 64c852e6fcc034cb56651ffc2d22fa5323bbb54f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680061"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="cdb70-102">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cdb70-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="cdb70-103">Následující témata ukazují, jak provádět různé základní operace u souborů, složek a registru pomocí C# a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdb70-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdb70-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cdb70-104">In This Section</span></span>  
  
|<span data-ttu-id="cdb70-105">**Název**</span><span class="sxs-lookup"><span data-stu-id="cdb70-105">**Title**</span></span>|<span data-ttu-id="cdb70-106">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cdb70-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="cdb70-107">Postupy: Iterace v adresářovém stromě</span><span class="sxs-lookup"><span data-stu-id="cdb70-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="cdb70-108">Ukazuje, jak ručně iterace v adresářovém stromu.</span><span class="sxs-lookup"><span data-stu-id="cdb70-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="cdb70-109">Postupy: Získání informací o souborech, složkách a jednotkách</span><span class="sxs-lookup"><span data-stu-id="cdb70-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="cdb70-110">Ukazuje, jak načíst informace, jako je vytváření časy a velikost, o souborech, složkách a jednotkách.</span><span class="sxs-lookup"><span data-stu-id="cdb70-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="cdb70-111">Postupy: Vytvoření souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="cdb70-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="cdb70-112">Ukazuje, jak vytvořit nový soubor nebo složku.</span><span class="sxs-lookup"><span data-stu-id="cdb70-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="cdb70-113">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="cdb70-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="cdb70-114">Ukazuje, jak zkopírovat, odstranění a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="cdb70-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="cdb70-115">Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="cdb70-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="cdb70-116">Ukazuje, jak zobrazit standardní dialogové okno průběhu Windows pro určité operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="cdb70-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="cdb70-117">Postupy: Zápis do textového souboru</span><span class="sxs-lookup"><span data-stu-id="cdb70-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="cdb70-118">Ukazuje, jak zapisovat do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="cdb70-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="cdb70-119">Postupy: Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="cdb70-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="cdb70-120">Znázorňuje způsob čtení z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="cdb70-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="cdb70-121">Postupy: Přečtěte si jeden řádek textu souboru v čase</span><span class="sxs-lookup"><span data-stu-id="cdb70-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="cdb70-122">Ukazuje, jak načtení textu ze souboru v čase.</span><span class="sxs-lookup"><span data-stu-id="cdb70-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="cdb70-123">Postupy: Vytvoření klíče v registru</span><span class="sxs-lookup"><span data-stu-id="cdb70-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="cdb70-124">Ukazuje, jak zapsat klíč registru systému.</span><span class="sxs-lookup"><span data-stu-id="cdb70-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="cdb70-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cdb70-125">Related Sections</span></span>  
 [<span data-ttu-id="cdb70-126">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="cdb70-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="cdb70-127">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="cdb70-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="cdb70-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cdb70-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="cdb70-129">Souborech, složkách a jednotkách</span><span class="sxs-lookup"><span data-stu-id="cdb70-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
