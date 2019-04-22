---
title: Přehled standardních operátorů dotazu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841469"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Přehled standardních operátorů dotazu (Visual Basic)
*Standardních operátorů pro dotazování* jsou metody, které tvoří LINQ vzoru. Většina z těchto metod pracovat v pořadí, ve kterém sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Operátory standardního dotazu zadejte možnosti dotazu, jako je filtrování, projekce, agregace, řazení a další.  
  
 Existují dvě sady operátory standardního dotazu LINQ, ten, který funguje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který funguje na objektech typu <xref:System.Linq.IQueryable%601>. Statické členy třídy jsou metody, které tvoří každou sadu <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí. Jsou definovány jako *rozšiřující metody* typu, který funguje na. To znamená, že lze volat pomocí syntaxe statickou metodu nebo pomocí syntaxe metody instance.  
  
 Kromě toho několik standardní metody operátoru dotazu pracovat s typy než ty, které na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definuje tyto dvě metody jak pracovat s objekty typu <xref:System.Collections.IEnumerable>. Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci neparametrizované nebo neobecnou, aby se dalo dotazovat v LINQ vzoru. Je to tak, že vytvoříte kolekci silně typovaných objektů. <xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objektech typu <xref:System.Linq.Queryable>.  
  
 Operátory standardního dotazu se liší v časování jejich spuštění, v závislosti na tom, zda vrátit hodnotu singleton nebo posloupnost hodnot. Tyto metody, které vracejí hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě. Metody, které vracejí sekvenci odloží provedení dotazu a vrátí vyčíslitelný objekt.  
  
 V případě metody, které pracují na kolekce v paměti, to znamená, že tyto metody, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zachycuje argumenty, které byly předány metodě. Když tento objekt je vypočten, použijí logiky – operátor dotazu a jsou vráceny výsledky dotazu.  
  
 Naproti tomu jsou metody, které rozšiřují <xref:System.Linq.IQueryable%601> neimplementují všechna dotazování chování, ale sestavení strom výrazu, který představuje dotaz, který má být provedena. Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.  
  
 Volání metody dotazu je možné zřetězit v jednom dotazu, který umožňuje dotazům stát libovolně složité.  
  
 Následující příklad kódu ukazuje, jak lze získat informace o posloupnosti standardních operátorů pro dotazování.  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Některé častěji používané operátory standardního dotazu mít vyhrazené syntaxi jazyka – klíčové slovo jazyka C# a Visual Basic, která je volána v rámci umožňuje *dotazu* *výraz*. Další informace o standardních operátorů dotazu, které mají vyhrazená klíčová slova a jejich odpovídající syntaxe, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozšíření standardních operátorů pro dotazování  
 Metodami vytváření specifického pro doménu, které jsou vhodné pro cílovou doménu nebo technologii lze rozšířit sadu standardních operátorů pro dotazování. Operátory standardního dotazu můžete také nahradit vlastní implementace, které poskytují další služby, jako je vzdálené testování, překladu dotazu a optimalizace. Zobrazit <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.  
  
## <a name="related-sections"></a>Související oddíly  
 Pomocí následujících odkazů můžete na témata, která poskytují další informace o různých standardních operátorů pro dotazování závislosti na funkcích.  
  
 [Řazení dat](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Množinové operace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrování dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Dělení dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Připojte se k operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Seskupování dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Generování operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operace rovnosti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operace s elementy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Převádění datových typů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operace sřetězení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Aggregation Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Úvod do LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [Klasifikace standardních operátorů dotazu podle metody provedení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [Rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
