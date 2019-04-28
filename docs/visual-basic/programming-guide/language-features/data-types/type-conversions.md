---
title: Převody typů v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: 026b2a250abfac0782feb0946bc50a94f504f7ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663281"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="bfe0d-102">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfe0d-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="bfe0d-103">Proces změny hodnotu z jednoho datového typu na jiný typ se nazývá *převod*.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="bfe0d-104">Převody jsou buď *rozšiřující* nebo *zúžení*, v závislosti na datové kapacity zahrnuté typů.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="bfe0d-105">Jsou také *implicitní* nebo *explicitní*, v závislosti na syntaxi ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfe0d-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bfe0d-106">In This Section</span></span>  
 [<span data-ttu-id="bfe0d-107">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="bfe0d-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="bfe0d-108">Vysvětluje převody klasifikuje Určuje, zda cílový typ může obsahovat data.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="bfe0d-109">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="bfe0d-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="bfe0d-110">Tento článek popisuje klasifikuje Určuje, zda jazyka Visual Basic je automaticky provádí převody.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="bfe0d-111">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="bfe0d-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="bfe0d-112">Převod mezi řetězci a číselné literály, ukazuje `Boolean`, nebo hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="bfe0d-113">Postupy: Převést objekt na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfe0d-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="bfe0d-114">Ukazuje, jak převést `Object` proměnné k jakýmkoli jiným datovým typem.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="bfe0d-115">Převody polí</span><span class="sxs-lookup"><span data-stu-id="bfe0d-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="bfe0d-116">Vás provede jednotlivými kroky procesu převodu mezi pole různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bfe0d-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bfe0d-117">Related Sections</span></span>  
 [<span data-ttu-id="bfe0d-118">Datové typy</span><span class="sxs-lookup"><span data-stu-id="bfe0d-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="bfe0d-119">Představuje datové typy jazyka Visual Basic a popisuje, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="bfe0d-120">Datové typy</span><span class="sxs-lookup"><span data-stu-id="bfe0d-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="bfe0d-121">Seznam základních datových typů poskytnutých jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="bfe0d-122">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="bfe0d-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="bfe0d-123">Tento článek popisuje některé běžné problémy, které mohou vzniknout při práci s datovými typy.</span><span class="sxs-lookup"><span data-stu-id="bfe0d-123">Discusses some common problems that can arise when working with data types.</span></span>
