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
# <a name="exception-c-programming-guide"></a>\<Výjimka > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace. Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML. `member` musí být uvedena v uvozovkách ("").  
  
 Další informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Popis výjimky.  
  
## <a name="remarks"></a>Poznámky  
 \<Výjimky > značky umožňuje určit, jaké výjimky mohou být vyvolány. Toto klíčové slovo lze použít pro definice pro metody, vlastnosti, události a indexery.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
 Další informace o zpracování výjimek naleznete v tématu [výjimek a zpracování výjimek](../../../csharp/programming-guide/exceptions/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
