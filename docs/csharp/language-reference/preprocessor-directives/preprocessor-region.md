---
title: '#oblast – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: adaa58fc47da557a31270e99ff8a1dae3d0731bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659979"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [sbalování](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio. V souborech kódu delší dobu je vhodné sbalit nebo skrýt jedné nebo více oblastí, aby vám umožní soustředit se u souboru, který jste právě pracujete. Následující příklad ukazuje, jak definovat oblasti:  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Poznámky  
 A `#region` bloku musí být ukončen direktivou [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) směrnice.  
  
 A `#region` bloku se nesmí překrývat s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku. Ale `#region` bloku může být vnořena v `#if` bloku a `#if` bloku může být vnořena v `#region` bloku.  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
