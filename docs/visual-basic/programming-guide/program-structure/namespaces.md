---
title: Obory názvů v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 792741dc4df7b65ddef124615032c06a7ff1bcb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050455"
---
# <a name="namespaces-in-visual-basic"></a>Obory názvů v jazyce Visual Basic
Obory názvů uspořádávají objekty definované v sestavení. Sestavení může obsahovat více oborů názvů, který pak může obsahovat další obory názvů. Obory názvů zabránilo nejednoznačnosti a při použití velké skupiny objektů, jako je například knihovny tříd zjednodušení odkazy.  
  
 Například [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje <xref:System.Windows.Forms.ListBox> třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů. Následující fragment kódu ukazuje, jak deklarovat pomocí plně kvalifikovaného názvu pro tuto třídu:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Předcházení kolizi názvů  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obory názvů řešení problému říká se jim *znečištění oboru názvů*, ve které vývojář knihovny tříd komplikují užívání podobnými názvy v jiné knihovny. Tyto je v konfliktu s existující součásti jsou někdy označovány jako *byly kolize názvů*.  
  
 Například, pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít uvnitř projektu bez kvalifikace. Nicméně pokud chcete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> třídy ve stejném projektu, musíte použít plně kvalifikovaný odkaz aby odkaz na jedinečný. Pokud odkaz není jedinečný, Visual Basic vytvoří chybu s informacemi o tom, že název je nejednoznačný. Následující příklad kódu ukazuje, jak deklarovat tyto objekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Následující obrázek znázorňuje dvěma hierarchiemi obor názvů, obě obsahující objekt s názvem `ListBox`:  
  
 ![Snímek obrazovky zobrazující dvěma hierarchiemi oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Ve výchozím nastavení obsahuje každý spustitelného souboru, který vytvoříte pomocí jazyka Visual Basic obor názvů se stejným názvem jako váš projekt. Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, obsahuje obor názvů s názvem spustitelného souboru ListBoxProject.exe `ListBoxProject`.  
  
 Více sestavení můžete použít stejný obor názvů. Visual Basic je zpracovává jako jednu sadu názvů. Například můžete definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejný obor názvů ze sestavení s názvem `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Plně kvalifikované názvy jsou odkazy na objekty, které mají předponu názvu oboru názvů, ve kterém je definována objektu. Můžete použít objekty definované v jiných projektech, je-li vytvořit odkaz na třídu (výběrem **přidat odkaz** z **projektu** nabídky) a pak použít plně kvalifikovaný název pro objekt v kódu. Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z oboru názvů jiného projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Plně kvalifikované názvy zabránit pojmenování je v konfliktu vzhledem k tomu, že umožňují kompilátoru k určení, který objekt se používá. Nicméně názvy samy můžete získat dlouhé a těžkopádný proces. Chcete-li se tomuto problému vyhnout, můžete použít `Imports` příkaz k definování *alias*– zkrácený název použijete místo plně kvalifikovaný název. Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a pomocí těchto aliasů definuje dva objekty.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Pokud používáte `Imports` příkaz bez alias, můžete použít všechny názvy v tom, že obor názvů bez kvalifikace, k dispozici jsou jedinečné pro projekt. Pokud váš projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, plně musíte tento název použijete. Předpokládejme například, váš projekt obsahoval následující dva `Imports` příkazy:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Pokud se pokusíte použít `Class1` bez plně kvalifikovaného, Visual Basic vygeneruje chybu oznamující, že název `Class1` je nejednoznačný.  
  
## <a name="namespace-level-statements"></a>Příkazy Namespace úroveň  
 V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegátů, výčty, struktury a ostatní obory názvů. Nejde definovat položky, jako jsou vlastnosti, procedury, proměnné a události na úrovni oboru názvů. Tyto položky musí být deklarována v rámci kontejnery, jako jsou moduly, struktury nebo třídy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Global – klíčové slovo v plně kvalifikované názvy  
 Pokud jste definovali vnořené hierarchie oborů názvů, kód uvnitř této hierarchii mohou blokovat přístup k <xref:System?displayProperty=nameWithType> obor názvů rozhraní .NET Framework. Následující příklad ukazuje hierarchie, ve kterém `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 V důsledku toho kompilátor jazyka Visual Basic nelze úspěšně vyhodnotit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`. Můžete použít `Global` – klíčové slovo spustit kvalifikace řetězce na vnější úrovni v knihovně tříd rozhraní .NET Framework. Díky tomu můžete určit <xref:System?displayProperty=nameWithType> oboru názvů nebo jiný obor názvů v knihovně tříd. Toto dokládá následující příklad.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Můžete použít `Global` k jiných oborech názvů kořenové úrovně <xref:Microsoft.VisualBasic?displayProperty=nameWithType>a libovolný obor názvů související s projektem.  
  
## <a name="global-keyword-in-namespace-statements"></a>Global – klíčové slovo v příkazy Namespace  
 Můžete také použít `Global` – klíčové slovo v [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Tímto způsobem můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu.  
  
 Všechny obory názvů v projektu jsou založeny na kořenového oboru názvů pro projekt.  Jako výchozí obor názvů root pro veškerý kód v projektu sady Visual Studio přiřadí název vašeho projektu. Například, pokud je název vašeho projektu `ConsoleApplication1`, jeho programovací prvky patří do oboru názvů `ConsoleApplication1`. Pokud deklarujete `Namespace Magnetosphere`, odkazy na `Magnetosphere` v projektu bude mít přístup k `ConsoleApplication1.Magnetosphere`.  
  
 Následující příklady používají `Global` – klíčové slovo k deklarování oboru názvů mimo kořenový obor názvů pro projekt.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 V deklaraci oboru názvů `Global` nemůže být vnořená v jiném oboru názvů.  
  
 Můžete použít [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) zobrazovat a upravovat **kořenové Namespace** projektu.  Pro nové projekty **kořenové Namespace** výchozí hodnoty na název projektu. Způsobí `Global` na nejvyšší úrovni oboru názvů, zrušte **kořenové Namespace** položky tak, že je pole prázdné. Vymazání **kořenové Namespace** eliminuje potřebu `Global` – klíčové slovo v deklarace oboru názvů.  
  
 Pokud `Namespace` příkaz deklaruje název, který je taky obor názvů v rozhraní .NET Framework, obor názvů rozhraní .NET Framework přestane být k dispozici Pokud `Global` – klíčové slovo se nepoužívá v plně kvalifikovaném názvu. Umožňuje přístup na tento obor názvů rozhraní .NET Framework bez použití `Global` – klíčové slovo, můžete zahrnout `Global` – klíčové slovo v `Namespace` příkazu.  
  
 V následujícím příkladu má `Global` – klíčové slovo v `System.Text` deklarace oboru názvů.  
  
 Pokud `Global` – klíčové slovo nebyl k dispozici v deklaraci oboru názvů <xref:System.Text.StringBuilder> nelze získat přístup bez zadání `Global.System.Text.StringBuilder`. Pro projekt s názvem `ConsoleApplication1`, odkazy na `System.Text` byste přistupovali k `ConsoleApplication1.System.Text` Pokud `Global` – klíčové slovo se nepoužil.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Psaní kódu v řešeních pro systém Office](/visualstudio/vsto/writing-code-in-office-solutions)
