---
title: Klíčová slova jako názvy elementu v kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 2e3613bd4a74da51cf7dbb63e52eddca811ca8e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947667"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Klíčová slova jako názvy elementu v kódu (Visual Basic)
Libovolný prvek programu, například proměnná, třída nebo člen – může mít stejný název jako klíčové slovo s omezením. Můžete například vytvořit proměnnou s názvem `Loop`. Chcete-li však odkazovat na svou verzi, která má stejný název jako klíčové slovo s omezeným přístupem `Loop` , je nutné před něj přednést úplný řetězec kvalifikace nebo jej uzavřít do hranatých závorek (`[ ]`), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Pokud to neuděláte, Visual Basic předpokládá použití klíčového slova vnitřní `Loop` a vytvoří chybu, jako v následujícím příkladu:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Můžete použít hranaté závorky při odkazování na formuláře a ovládací prvky a při deklaraci proměnné nebo definování procedury se stejným názvem jako klíčové slovo s omezením. Může být snadné zapomenout názvy nebo zahrnovat hranaté závorky a tím do kódu začlenit chyby a ztížit jeho čtení. Z tohoto důvodu doporučujeme, abyste nepoužívali omezená klíčová slova jako názvy prvků programu. Nicméně pokud budoucí verze Visual Basic definuje nové klíčové slovo, které je v konfliktu s existujícím formulářem nebo názvem ovládacího prvku, můžete použít tuto techniku při aktualizaci kódu pro práci s novou verzí.  
  
> [!NOTE]
> Program může také obsahovat názvy elementů, které jsou k dispozici v jiných odkazovaných sestaveních. Pokud tyto názvy jsou v konfliktu s omezenými klíčovými slovy, pak při jejich umístění hranaté závorky způsobí, Visual Basic je interpretovat jako definované prvky.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic konvence pojmenování](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
