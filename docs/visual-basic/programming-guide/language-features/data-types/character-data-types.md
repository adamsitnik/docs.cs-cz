---
title: Datové typy znaků (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907228"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="94a73-102">Datové typy znaků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a73-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="94a73-103">Visual Basic poskytuje *znakové datové typy* řešit tisknutelný a zobrazitelný znaků.</span><span class="sxs-lookup"><span data-stu-id="94a73-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="94a73-104">Přestože oba vypořádat se znaky Unicode, `Char` obsahuje jeden znak, zatímco `String` obsahuje nekonečný počet znaků.</span><span class="sxs-lookup"><span data-stu-id="94a73-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="94a73-105">Tabulka, která zobrazuje vedle sebe porovnání datových typů jazyka Visual Basic, naleznete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="94a73-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="94a73-106">Znakový typ</span><span class="sxs-lookup"><span data-stu-id="94a73-106">Char Type</span></span>  
 <span data-ttu-id="94a73-107">`Char` Datový typ je jeden znak Unicode (16-bit) dva bajty.</span><span class="sxs-lookup"><span data-stu-id="94a73-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="94a73-108">Pokud proměnná uchovává vždy přesně jeden znak, deklarujte ho jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="94a73-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="94a73-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="94a73-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="94a73-110">Jednotlivé možné vlastnosti v `Char` nebo `String` proměnná je *kódu bodu*, nebo kód znaku ve znakové sadě Unicode.</span><span class="sxs-lookup"><span data-stu-id="94a73-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="94a73-111">Znaky Unicode obsahovat základní znakové sadě ASCII, různé jiné písmena abecedy, zvýraznění, symboly měny, zlomky, diakritiku a technické a matematické symboly.</span><span class="sxs-lookup"><span data-stu-id="94a73-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94a73-112">Znaková sada Unicode rezervy kód odkazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradní páry*, které vyžadují dvě hodnoty 16bitové představuje bod jeden kód.</span><span class="sxs-lookup"><span data-stu-id="94a73-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="94a73-113">A `Char` proměnná nemůže obsahovat náhradní pár a `String` používá dvě místa k uložení těchto pár.</span><span class="sxs-lookup"><span data-stu-id="94a73-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="94a73-114">Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="94a73-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="94a73-115">String – typ</span><span class="sxs-lookup"><span data-stu-id="94a73-115">String Type</span></span>  
 <span data-ttu-id="94a73-116">`String` Datový typ je posloupnost nula nebo více znaků Unicode (16-bit) dva bajty.</span><span class="sxs-lookup"><span data-stu-id="94a73-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="94a73-117">Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ho jako `String`.</span><span class="sxs-lookup"><span data-stu-id="94a73-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="94a73-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="94a73-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="94a73-119">Další informace najdete v tématu [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="94a73-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a73-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94a73-120">See also</span></span>

- [<span data-ttu-id="94a73-121">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="94a73-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="94a73-122">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="94a73-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="94a73-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94a73-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="94a73-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="94a73-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="94a73-125">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94a73-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="94a73-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="94a73-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="94a73-127">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="94a73-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
