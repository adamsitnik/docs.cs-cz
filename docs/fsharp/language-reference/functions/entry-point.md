---
title: Vstupní bod
description: Zjistěte, jak nastavit vstupní bod F# program zkompilovaný jako spustitelný soubor, ve kterém formálně spuštění.
ms.date: 05/16/2016
ms.openlocfilehash: 915ab17b9a4fc7fd4d0ae344cb273b1d348a02f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996824"
---
# <a name="entry-point"></a><span data-ttu-id="bf863-103">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="bf863-103">Entry Point</span></span>

<span data-ttu-id="bf863-104">Toto téma popisuje metody, která se používá k nastavení vstupní bod F# programu.</span><span class="sxs-lookup"><span data-stu-id="bf863-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf863-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf863-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="bf863-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf863-106">Remarks</span></span>

<span data-ttu-id="bf863-107">V předchozí syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="bf863-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="bf863-108">Vstupní bod programu, který je zkompilován je spustitelný soubor, ve kterém formálně spuštění.</span><span class="sxs-lookup"><span data-stu-id="bf863-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="bf863-109">Zadejte vstupní bod do F# aplikace s použitím `EntryPoint` atribut programu `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="bf863-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="bf863-110">Tato funkce (vytvořené využitím `let` vazby) musí být poslední funkci v poslední zkompilovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="bf863-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="bf863-111">Poslední zkompilovaný soubor je poslední soubor v projektu nebo poslední soubor, který je předán do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="bf863-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="bf863-112">Funkci vstupního bodu má typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="bf863-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="bf863-113">Argumenty příkazového řádku k dispozici jsou předány `main` funkce v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="bf863-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="bf863-114">Prvním prvkem pole je první argument; název spustitelného souboru, který není zahrnutý v poli, je to v některých jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="bf863-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="bf863-115">Návratová hodnota se používá jako ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="bf863-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="bf863-116">Nula obvykle znamená úspěšné nenulové hodnoty udávající chybu.</span><span class="sxs-lookup"><span data-stu-id="bf863-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="bf863-117">Neexistuje žádné vytváření názvů pro zvláštní význam nenulové návratové kódy; význam návratové kódy jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bf863-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="bf863-118">Následující příklad ukazuje jednoduchý `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="bf863-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="bf863-119">Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bf863-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="bf863-120">Implicitní vstupní bod</span><span class="sxs-lookup"><span data-stu-id="bf863-120">Implicit Entry Point</span></span>

<span data-ttu-id="bf863-121">Pokud program nemá žádné **EntryPoint** atribut, který explicitně určuje vstupní bod vazeb nejvyšší úrovně v posledním souboru ke kompilaci se používají jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="bf863-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf863-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf863-122">See also</span></span>

- [<span data-ttu-id="bf863-123">Funkce</span><span class="sxs-lookup"><span data-stu-id="bf863-123">Functions</span></span>](index.md)
- [<span data-ttu-id="bf863-124">Vazby let</span><span class="sxs-lookup"><span data-stu-id="bf863-124">let Bindings</span></span>](let-bindings.md)