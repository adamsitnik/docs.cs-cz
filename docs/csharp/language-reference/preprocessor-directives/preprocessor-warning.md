---
title: '#Upozornění: C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659953"
---
# <a name="warning-c-reference"></a>#warning (referenční dokumentace jazyka C#)
`#warning` Umožňuje generovat [CS1030](../../misc/cs1030.md) úroveň jedno upozornění kompilátoru z určitého umístění ve vašem kódu. Příklad:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky
 Běžně `#warning` v podmíněnou direktivu. Je také možné vytvořit uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
## <a name="example"></a>Příklad  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
