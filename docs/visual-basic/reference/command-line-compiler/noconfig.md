---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819428"
---
# <a name="-noconfig"></a>-noconfig
Určuje, že kompilátor by neměl odkazovat automaticky běžně používaných [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení nebo import `System` a `Microsoft.VisualBasic` obory názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 `-noconfig` Přikáže kompilátoru, aby kompilovat s soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe. Odkazuje na soubor Vbc.rsp běžně používaných [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importuje `System` a `Microsoft.VisualBasic` obory názvů. Kompilátor implicitně odkazuje na sestavení System.dll, není-li `-nostdlib` je zadána možnost. `-nostdlib` Přikáže kompilátoru, aby kompilovat s Vbc.rsp nebo automaticky odkazují na toto sestavení System.dll.  
  
> [!NOTE]
>  Vždy je odkazováno na sestavení Mscorlib.dll a Microsoft.VisualBasic.dll.  
  
 Můžete upravit soubor Vbc.rsp zadat další možnosti kompilátoru, které by měl být součástí každé Vbc.exe kompilaci (s výjimkou při zadávání `-noconfig` možnost). Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilátor zpracovává možnosti předané `vbc` poslední příkaz. Proto všechny možnost na příkazovém řádku přepíše nastavení stejná možnost v soubor Vbc.rsp.  
  
> [!NOTE]
>  `-noconfig` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
