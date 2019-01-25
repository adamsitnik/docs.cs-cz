---
title: '-target: library (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0bdf8d95004ca11e3d6b9b27568f7310a802a28b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542441"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: library (možnosti kompilátoru C#)
**-Target: library** možnost způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelný soubor (EXE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří se knihovna DLL s příponou .dll.  
  
 Pokud není stanoveno jinak pomocí [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá názvu prvního vstupního souboru.  
  
 Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** slouží k vytvoření souboru .dll.  
  
 Při vytváření souboru .dll [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda se nevyžaduje.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **aplikace** stránku vlastností.  
  
3.  Upravit **typ výstupu** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs`, vytváření `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
