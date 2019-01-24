---
title: 'Postupy: Zápis znaků do řetězce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740980"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="6fad2-102">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="6fad2-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="6fad2-103">Následující příklady kódu zápis znaků synchronního a asynchronního z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="6fad2-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fad2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fad2-104">Example</span></span>  
 <span data-ttu-id="6fad2-105">Následující příklad zapíše 5 znaků synchronně z pole na řetězec.</span><span class="sxs-lookup"><span data-stu-id="6fad2-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="6fad2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fad2-106">Example</span></span>  
 <span data-ttu-id="6fad2-107">Následující příklad načte všechny znaky asynchronně z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli.</span><span class="sxs-lookup"><span data-stu-id="6fad2-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="6fad2-108">Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku, za nímž následuje koncem řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6fad2-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6fad2-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fad2-109">See also</span></span>

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="6fad2-110">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="6fad2-110">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="6fad2-111">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="6fad2-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="6fad2-112">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="6fad2-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="6fad2-113">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="6fad2-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="6fad2-114">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="6fad2-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="6fad2-115">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="6fad2-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="6fad2-116">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="6fad2-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="6fad2-117">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="6fad2-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
