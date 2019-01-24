---
title: 'Postupy: Čtení textu ze souboru'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f667b0a757a676788b693691504512dfc227a7e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646669"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="fc352-102">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="fc352-102">How to: Read Text from a File</span></span>
<span data-ttu-id="fc352-103">Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="fc352-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="fc352-104">V obou příkladech je při vytváření instance třídy <xref:System.IO.StreamReader> třídu, zadejte relativní nebo absolutní cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="fc352-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="fc352-105">Následující příklady předpokládají, že soubor s názvem TestFile.txt je uložen ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc352-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="fc352-106">Tyto příklady kódu se nevztahují na vývoj pro Windows Store Apps, protože modul Windows Runtime poskytuje různé stream typy pro čtení a zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="fc352-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="fc352-107">Příklad, který znázorňuje způsob čtení textu ze souboru v aplikaci Windows Store, naleznete v tématu [rychlý start: Čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="fc352-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="fc352-108">Příklady, které ukazují, jak k převodu mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows runtime naleznete v tématu [jak: Převádění mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="fc352-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc352-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc352-109">Example</span></span>  
 <span data-ttu-id="fc352-110">Následující příklad ukazuje operaci synchronního čtení v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc352-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="fc352-111">V tomto příkladu textový soubor se otevře pomocí čtečku datového proudu obsahu se zkopírují do řetězce a řetězce je výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc352-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="fc352-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc352-112">Example</span></span>  
 <span data-ttu-id="fc352-113">Následující příklad ukazuje operaci asynchronního čtení v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="fc352-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fc352-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc352-114">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fc352-115">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="fc352-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="fc352-116">NIB: Postupy: Vytváření adresářů</span><span class="sxs-lookup"><span data-stu-id="fc352-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [<span data-ttu-id="fc352-117">Rychlý start: Čtení a zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="fc352-117">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)
- [<span data-ttu-id="fc352-118">Postupy: Převod mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="fc352-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
- [<span data-ttu-id="fc352-119">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="fc352-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="fc352-120">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="fc352-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="fc352-121">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="fc352-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="fc352-122">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="fc352-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
- [<span data-ttu-id="fc352-123">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="fc352-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="fc352-124">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="fc352-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
