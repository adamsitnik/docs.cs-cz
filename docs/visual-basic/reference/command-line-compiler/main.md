---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337237"
---
# <a name="-main"></a>-main
Určuje třídu nebo modul, který obsahuje `Sub Main` postup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Povinný parametr. Název třídy nebo modul, který obsahuje `Sub Main` proceduru, která se má volat při spuštění programu. To může být ve tvaru **-main: modul** nebo **-main:namespace.module**.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte, když vytvoříte spustitelného souboru nebo spustitelný program Windows. Pokud **– hlavní** možnost vynecháte, kompilátor hledá platný sdílený `Sub Main` v všechny veřejné třídy a moduly.  
  
 Zobrazit [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) diskuzi o různých způsobech `Main` postup.  
  
 Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` proceduru, která spustí aplikaci, pokud třída nemá žádné `Main` postup. To umožňuje kompilaci kódu na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Chcete-li nastavit – hlavní v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2. Klikněte na tlačítko **aplikace** kartu.  
  
3. Ujistěte se, **Povolit aplikační framework** políčko není zaškrtnuté políčko.  
  
4. Upravte hodnotu v **spouštěcí objekt** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a `T3.vb`, určující, který `Sub Main` postup najdete v `Test2` třídy.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Viz také:

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
