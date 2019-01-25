---
title: 'Postupy: Implementace formuláře, který používá operaci na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: a472226103f077975c9c6ddc744d419cfcc390cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532133"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="8f9ce-102">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="8f9ce-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="8f9ce-103">Následující ukázkový program vytvoří formulář, který vypočítá Fibonacciho čísla.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="8f9ce-104">Výpočet běží na vlákně, které je oddělené od vlákně uživatelského rozhraní, takže uživatelské rozhraní i nadále běžel bez zpoždění při výpočtu pokračuje.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="8f9ce-105">Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="8f9ce-106">Viz také [názorný postup: Implementace formuláře, který používá operaci na pozadí](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8f9ce-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f9ce-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f9ce-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f9ce-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8f9ce-108">Compiling the Code</span></span>  
 <span data-ttu-id="8f9ce-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8f9ce-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8f9ce-110">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8f9ce-111">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8f9ce-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8f9ce-112">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="8f9ce-113">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8f9ce-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8f9ce-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8f9ce-114">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8f9ce-115">Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-115">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="8f9ce-116">Poraďte [spravovaných vláken osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreading.</span><span class="sxs-lookup"><span data-stu-id="8f9ce-116">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9ce-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f9ce-117">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="8f9ce-118">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="8f9ce-118">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="8f9ce-119">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="8f9ce-119">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
