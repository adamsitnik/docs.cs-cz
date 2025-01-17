---
title: <list> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 0df6653171aa0366f555c39e4644f13b2b7384f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523427"
---
# <a name="list-c-programming-guide"></a>> \<list (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametry  
 `term`  
 Pojem, který definuje, který bude definován v `description`.  
  
 `description`  
 Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 Blok > \<listheader slouží k definování řádku záhlaví seznamu tabulek nebo definic. Při definování tabulky stačí zadat položku pro termín v záhlaví.  
  
 Každá položka v seznamu je určena pomocí \<item > bloku. Při vytváření seznamu definic bude nutné zadat jak `term`, tak `description`. U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít tolik \<item > bloky podle potřeby.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
