---
title: globální kontextová klíčová slova – C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 9a8c7b5134cc29668aae53e8a3f86ddae4c8263a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627679"
---
# <a name="global-c-reference"></a><span data-ttu-id="25281-102">global (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="25281-102">global (C# Reference)</span></span>

<span data-ttu-id="25281-103">Klíčové slovo C# kontextové, pokud je uvedeno před [operátorem::](../operators/namespace-alias-qualifier.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro všechny programy a je jinak bez názvu. `global`</span><span class="sxs-lookup"><span data-stu-id="25281-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifier.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="25281-104">Další informace najdete v tématu [jak: Použijte globální alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="25281-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="25281-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="25281-105">Example</span></span>

<span data-ttu-id="25281-106">Následující příklad ukazuje, jak použít `global` klíčové slovo kontextu k určení toho, že třída `TestApp` je definována v globálním oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="25281-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="25281-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25281-107">See also</span></span>

- [<span data-ttu-id="25281-108">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="25281-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
