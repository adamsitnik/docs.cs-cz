---
title: Doladění aplikace s modifikátorem Async (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 82402b7ad7b05424881c5d671d1f810c65abb8b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582884"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="d8d79-102">Doladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d79-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="d8d79-103">Přidáte přesnost a flexibilitu asynchronním aplikací pomocí metody a vlastnosti, která <xref:System.Threading.Tasks.Task> typu bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d8d79-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="d8d79-104">Témata v této části obsahují příklady používající <xref:System.Threading.CancellationToken> a důležité `Task` metody jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8d79-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d8d79-105">S použitím `WhenAny` a `WhenAll`, můžete snadněji spustit více úkolů a Vyčkávat na jejich dokončení při sledování jednoho úkolu.</span><span class="sxs-lookup"><span data-stu-id="d8d79-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="d8d79-106">`WhenAny` Vrátí úlohu, která se dokončí při dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d8d79-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="d8d79-107">Příklady, které používají `WhenAny`, naleznete v tématu [zrušení zbývajících asynchronních úloh po jeden je úplná (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění více úloh s modifikátorem Async a proces je jako jejich dokončení (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="d8d79-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="d8d79-108">`WhenAll` Vrátí úlohu, která se dokončí po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d8d79-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="d8d79-109">Další informace a příklad použití `WhenAll`, naleznete v tématu [jak: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d8d79-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="d8d79-110">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="d8d79-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="d8d79-111">[Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="d8d79-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="d8d79-112">Zrušení asynchronních úloh po určitou dobu (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d79-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="d8d79-113">Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich</span><span class="sxs-lookup"><span data-stu-id="d8d79-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="d8d79-114">Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d79-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="d8d79-115">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="d8d79-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="d8d79-116">Projekty vytvářejí uživatelské rozhraní, která obsahuje tlačítko, které zahájí proces a tlačítko, které ho ruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="d8d79-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="d8d79-117">Tlačítka jsou pojmenována `startButton` a `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="d8d79-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="d8d79-118">![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "dialogové okno s tlačítkem spouštění a zastavování")</span><span class="sxs-lookup"><span data-stu-id="d8d79-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="d8d79-119">Můžete si stáhnout kompletní projektů Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="d8d79-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d79-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8d79-120">See also</span></span>

- [<span data-ttu-id="d8d79-121">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d79-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
