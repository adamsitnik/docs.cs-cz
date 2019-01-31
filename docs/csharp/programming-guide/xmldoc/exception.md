---
title: <exception> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fe304b9c6631591cf7a3d62fcecd2ed3ca05db9c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257288"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="b2262-102">\<Výjimka > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b2262-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b2262-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2262-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2262-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2262-104">Parameters</span></span>  
 <span data-ttu-id="b2262-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="b2262-105">cref = " `member`"</span></span>  
 <span data-ttu-id="b2262-106">Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="b2262-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="b2262-107">Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="b2262-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="b2262-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="b2262-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="b2262-109">Další informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="b2262-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="b2262-110">Popis výjimky.</span><span class="sxs-lookup"><span data-stu-id="b2262-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2262-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2262-111">Remarks</span></span>  
 <span data-ttu-id="b2262-112">\<Výjimky > značky umožňuje určit, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="b2262-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="b2262-113">Toto klíčové slovo lze použít pro definice pro metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="b2262-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="b2262-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="b2262-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="b2262-115">Další informace o zpracování výjimek naleznete v tématu [výjimek a zpracování výjimek](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2262-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2262-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2262-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b2262-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2262-117">See also</span></span>

- [<span data-ttu-id="b2262-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2262-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b2262-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="b2262-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
