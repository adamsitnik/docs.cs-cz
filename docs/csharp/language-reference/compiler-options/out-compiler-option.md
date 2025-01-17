---
title: -out (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970383"
---
# <a name="-out-c-compiler-options"></a>-out (C# možnosti kompilátoru)
Možnost **-out** Určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název výstupního souboru vytvořeného kompilátorem.  
  
## <a name="remarks"></a>Poznámky  
 Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci. Kompilátor očekává najít jeden nebo více souborů zdrojového kódu za možností **-out** . Pak všechny soubory se zdrojovým kódem budou zkompilovány do výstupního souboru **určeného parametrem** .  
  
 Zadejte úplný název a příponu souboru, který chcete vytvořit.  
  
 Pokud nezadáte název výstupního souboru:  
  
- Soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje metodu **Main** .  
  
- Soubor. dll nebo. netmodule převezme svůj název z prvního souboru zdrojového kódu.  
  
 Soubor zdrojového kódu, který se používá k kompilování jednoho výstupního souboru, nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.  
  
 Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor (implicitně nebo explicitně s parametrem **-out**) může být sestavení.  
  
 Všechny moduly, které jsou vytvořeny jako součást kompilace, se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci. K zobrazení přidružených souborů použijte [Ildasm. exe](../../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení manifestu sestavení.  
  
 Možnost kompilátoru-out je povinná, aby byl spustitelný soubor cílem sestavení typu Friend. Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **název sestavení** .  
  
     Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> : je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a názvu sestavení. Úpravou jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `t.cs` a vytvořte výstupní soubor `t.exe`a také `t2.cs` vytvořte a vytvořte výstupní soubor `mymodule.netmodule`modulu:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Přátelská sestavení](../../../standard/assembly/friend.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
