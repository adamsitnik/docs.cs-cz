---
title: 'Postupy: Skrýt proměnnou se stejným názvem jako má vaše proměnná (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 487e0a15ba6b52f92ab39fe0bae4ab15fa92707f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629996"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Postupy: Skrýt proměnnou se stejným názvem jako má vaše proměnná (Visual Basic)

Proměnnou můžete *Skrýt tak,* že ji nakonfigurujete tak, že ji převedete pomocí proměnné se stejným názvem. Proměnnou, kterou chcete skrýt, můžete vystínovat dvěma způsoby:

- **Vytváření stínů prostřednictvím rozsahu.** Můžete ho vytvořit pomocí oboru tím, že ho znovu deklarujete v podoblasti oblasti, která obsahuje proměnnou, kterou chcete skrýt.

- **Stínování prostřednictvím dědičnosti.** Pokud je proměnná, kterou chcete skrýt, definovaná na úrovni třídy, můžete ji stínovat pomocí dědičnosti tím, že ji předeklarujete pomocí klíčového slova [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) v odvozené třídě.

## <a name="two-ways-to-hide-a-variable"></a>Dva způsoby, jak skrýt proměnnou

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Skrytí proměnné pomocí jejího stínového rozsahu

1. Určete oblast definující proměnnou, kterou chcete skrýt, a určete podoblast, ve které se má proměnná znovu definovat.

    |Oblast proměnné|Povolená podoblast pro předefinování|
    |-----------------------|-------------------------------------------|
    |Modul|Třída v modulu|
    |Třída|Podtřída v rámci třídy<br /><br /> Procedura v rámci třídy|

    Nelze předefinovat proměnnou procedury v bloku v rámci této procedury, například v `If`... `End If` konstrukce`For` nebo smyčka.

2. Pokud ještě neexistuje, vytvořte podoblast.

3. V rámci suboblasti napište [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) , který deklaruje proměnnou Shadow.

    Když kód v suboblasti odkazuje na název proměnné, kompilátor přeloží odkaz na stínovou proměnnou.

    Následující příklad znázorňuje stínování v oboru a také odkaz, který obchází stíning.

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    Předchozí příklad deklaruje proměnnou `num` na úrovni modulu i na úrovni procedury (v postupu `show`). Lokální proměnná `num` nastínuje proměnnou `num` na úrovni modulu v `show`, takže místní proměnná je nastavená na 2. V proceduře ale neexistuje žádná místní proměnná pro stín `num`. `useModuleLevelNum` `useModuleLevelNum` Proto nastaví hodnotu proměnné na úrovni modulu na 1.

    Volání uvnitř `show` obchází mechanismus stínování tím, že je kvalifikován `num` s názvem modulu. `MsgBox` Proto zobrazuje proměnnou na úrovni modulu namísto místní proměnné.

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Skrytí proměnné stínovou kopií prostřednictvím dědičnosti

1. Ujistěte se, že je proměnná, kterou chcete skrýt, deklarována ve třídě a na úrovni třídy (mimo jakýkoli postup). V opačném případě nelze stínové IT pomocí dědičnosti.

2. Definujte třídu odvozenou z třídy proměnné, pokud ještě neexistuje.

3. V odvozené třídě napište příkaz, který `Dim` deklaruje vaši proměnnou. Do deklarace [](../../../../visual-basic/language-reference/modifiers/shadows.md) zahrňte klíčové slovo Shadows.

    Pokud kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaši proměnnou.

    Následující příklad znázorňuje stínování prostřednictvím dědičnosti. Vytvoří dva odkazy, jeden, který přistupuje ke stínové proměnné a druhý, který obchází stín.

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a nastínuje ji v odvozené třídě. Procedura `showStrings` v odvozené třídě zobrazuje stínovou verzi řetězce, pokud název `shadowString` není kvalifikován. Pak zobrazí stínovou verzi, pokud `shadowString` je kvalifikován `MyBase` pomocí klíčového slova.

## <a name="robust-programming"></a>Robustní programování

Stíning zavádí více než jednu verzi proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, na kterou kompilátor vyřeší odkaz, závisí na faktorech, jako je například umístění příkazu kódu a přítomnost opravňujícího řetězce. To může zvýšit riziko odkazování na neúmyslnou verzi stínové proměnné. Toto riziko můžete snížit tím, že plně zadáte všechny odkazy na stínovou proměnnou.

## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínování v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
