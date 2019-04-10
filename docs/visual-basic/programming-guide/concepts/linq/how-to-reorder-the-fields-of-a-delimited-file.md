---
title: 'Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 6f41a8e38812cf9d3c652fa605febf2511f07a27
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339083"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (Visual Basic)
Soubor hodnot oddělených čárkami (CSV) je textový soubor, který se často používá k ukládání dat tabulky nebo jiné tabulková data, která je reprezentována řádků a sloupců. S použitím <xref:System.String.Split%2A> metoda oddělují pole, je velmi snadné dotazování a zpracování souborů CSV pomocí jazyka LINQ. Ve skutečnosti stejným způsobem umožňuje změnit uspořádání částí jakéhokoli strukturovaných řádku textu. není omezený na souborů CSV.  
  
 V následujícím příkladu se předpokládá, že tři sloupce představují studentů "příjmení," "jméno" a "ID". Pole jsou v abecedním pořadí podle příjmení na studentů. Dotaz vyprodukuje nové pořadí, ve kterém sloupci ID se zobrazí první, za nímž následuje druhý sloupec, který kombinuje student získal křestní jméno a příjmení. Řádky přeuspořádají podle pole ID. Výsledky jsou uloženy do nového souboru a se nezmění původní data.  
  
### <a name="to-create-the-data-file"></a>Vytvoření datového souboru  
  
1. Zkopírujte následující řádky do souboru ve formátu prostého textu, který je pojmenován spreadsheet1.csv. Uložte soubor do složky projektu.  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a>Příklad  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Postupy: Generování XML ze souborů CSV](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
