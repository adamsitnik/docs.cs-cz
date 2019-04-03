---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 0fbe07884f55b7e6f460929e54520de5f718e1af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815001"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="7b19a-102">\<Souhrn > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b19a-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="7b19a-103">Určuje souhrn člena.</span><span class="sxs-lookup"><span data-stu-id="7b19a-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b19a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b19a-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b19a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b19a-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="7b19a-106">Přehled objektu.</span><span class="sxs-lookup"><span data-stu-id="7b19a-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b19a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b19a-107">Remarks</span></span>  
 <span data-ttu-id="7b19a-108">Použití `<summary>` značka, které popisují typ nebo člen typu.</span><span class="sxs-lookup"><span data-stu-id="7b19a-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="7b19a-109">Použití [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) přidat doplňující informace pro popis typu.</span><span class="sxs-lookup"><span data-stu-id="7b19a-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="7b19a-110">Text `<summary>` značka je jediný zdroj informací o typu v IntelliSense a také se zobrazí v prohlížeči objektů.</span><span class="sxs-lookup"><span data-stu-id="7b19a-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="7b19a-111">Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="7b19a-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="7b19a-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="7b19a-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b19a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b19a-113">Example</span></span>  
 <span data-ttu-id="7b19a-114">V tomto příkladu `<summary>` značka, které popisují `ResetCounter` metoda a `Counter` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7b19a-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7b19a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b19a-115">See also</span></span>

- [<span data-ttu-id="7b19a-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="7b19a-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
