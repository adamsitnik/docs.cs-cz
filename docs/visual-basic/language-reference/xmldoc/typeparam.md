---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 014623be84f9d7eb8a25ac4aadcce450f158c154
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827234"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="40d95-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d95-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="40d95-103">Definuje typu parametru názvu a popisu.</span><span class="sxs-lookup"><span data-stu-id="40d95-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40d95-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="40d95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40d95-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="40d95-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="40d95-106">The name of the type parameter.</span></span> <span data-ttu-id="40d95-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="40d95-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="40d95-108">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="40d95-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40d95-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40d95-109">Remarks</span></span>  
 <span data-ttu-id="40d95-110">Použití `<typeparam>` značku komentář pro obecný typ nebo deklarace obecného člena, popisující jeden z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="40d95-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="40d95-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="40d95-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d95-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="40d95-112">Example</span></span>  
 <span data-ttu-id="40d95-113">V tomto příkladu `<typeparam>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="40d95-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="40d95-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40d95-114">See also</span></span>

- [<span data-ttu-id="40d95-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="40d95-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
