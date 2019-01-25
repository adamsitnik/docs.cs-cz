---
title: Implicitní převod z &#39; &lt;NázevTypu1&gt; &#39; k &#39; &lt;NázevTypu2&gt; &#39; při kopírování hodnoty z &#39;ByRef&#39; parametr &#39; &lt; Název parametru&gt; &#39; zpět do odpovídajícího argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 9f05a5fbcbef828b4ffa920d8cade475cedb64d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537231"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Implicitní převod z &#39; &lt;NázevTypu1&gt; &#39; k &#39; &lt;NázevTypu2&gt; &#39; při kopírování hodnoty z &#39;ByRef&#39; parametr &#39; &lt; Název parametru&gt; &#39; zpět do odpovídajícího argumentu.
Postup se nazývá se [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument jiného typu než jeho odpovídající parametr.  
  
 Pokud předáte argument `ByRef`, Visual Basic někdy kopíruje hodnotu argumentu do místní proměnné v postupu namísto předávání odkazem. V takovém případě se po návratu podle postupu Visual Basic musí potom zkopírujte hodnotu lokální proměnné zpět do argumentu ve volajícím kódu.  
  
 Pokud `ByRef` hodnota argumentu je zkopírován do procedury a argumentu a parametru jsou stejného typu, je nezbytné žádný převod. Ale pokud se typy liší, musíte převést jazyka Visual Basic v obou směrech. Protože nemůžete použít `CType` nebo některý z další klíčová slova převodu na argumentu procedury nebo parametr, takový převod je vždy implicitní.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC41999  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné použijte volání argument stejného typu jako parametr procedury, proto není nutné provádět jakýkoli převod jazyka Visual Basic.  
  
-   Pokud je potřeba volání procedury s argumentem typu liší od typu parametru, ale není nutné vrátit hodnotu do volání argument, definujte parametr bude [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
## <a name="see-also"></a>Viz také:
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
