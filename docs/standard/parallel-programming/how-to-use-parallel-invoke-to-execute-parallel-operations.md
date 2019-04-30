---
title: 'Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0192e12c86b21eb126293bbd220e093b334768b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797095"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="30012-102">Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací</span><span class="sxs-lookup"><span data-stu-id="30012-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="30012-103">Tento příklad ukazuje, jak pomocí paralelní zpracování operace <xref:System.Threading.Tasks.Parallel.Invoke%2A> v knihovně Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="30012-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="30012-104">Na sdílený zdroj dat provádějí tři operace.</span><span class="sxs-lookup"><span data-stu-id="30012-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="30012-105">Protože žádná z operací upraví zdroj, mohou být provedeny souběžně v přímočarým způsobem.</span><span class="sxs-lookup"><span data-stu-id="30012-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="30012-106">Tato dokumentace používá k definování delegátů v TPL lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="30012-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="30012-107">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="30012-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="30012-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="30012-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="30012-109">Všimněte si, že se <xref:System.Threading.Tasks.Parallel.Invoke%2A>, jednoduše express akce, které chcete spouštět souběžně a modul runtime zpracovává všechny podrobnosti, včetně automatické škálování počtu jader v hostitelském počítači plánování vláken.</span><span class="sxs-lookup"><span data-stu-id="30012-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="30012-110">V tomto příkladu parallelizes operace, ne data.</span><span class="sxs-lookup"><span data-stu-id="30012-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="30012-111">Jako alternativní přístup můžete pomocí PLINQ paralelizovat dotazů LINQ a dotazy spouští sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="30012-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="30012-112">Alternativně může paralelizovat data s využitím PLINQ.</span><span class="sxs-lookup"><span data-stu-id="30012-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="30012-113">Další možností je paralelní dotazy a úlohy.</span><span class="sxs-lookup"><span data-stu-id="30012-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="30012-114">Ačkoli výsledný režii může snížit výkon na hostitelském počítači s relativně malý počet procesorů, ho případném vertikálním mnohem lepší na počítačích s více procesory.</span><span class="sxs-lookup"><span data-stu-id="30012-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="30012-115">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="30012-115">Compile the Code</span></span>

<span data-ttu-id="30012-116">Zkopírujte a vložte do projektu sady Microsoft Visual Studio a stiskněte klávesu celý příklad **F5**.</span><span class="sxs-lookup"><span data-stu-id="30012-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="30012-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30012-117">See also</span></span>

- [<span data-ttu-id="30012-118">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="30012-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="30012-119">Postupy: Zrušení úlohy a jejích potomků</span><span class="sxs-lookup"><span data-stu-id="30012-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="30012-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="30012-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
