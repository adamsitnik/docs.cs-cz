---
title: 'Postupy: Dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 134183da58b490635284699de2f1721dda5422dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597063"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Postupy: Dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)
Tento příklad ukazuje pět dotazů souvisejících s velikostí souboru v bajtech:  
  
- Jak načíst velikost v bajtech největší soubor.  
  
- Jak načíst velikost v bajtech nejmenší souboru.  
  
- Jak načíst <xref:System.IO.FileInfo> největší nebo nejmenší soubor objektu z jedné nebo více složek v rámci zadané kořenové složky.  
  
- Jak získávají pořadí, jako je například 10 největších souborů.  
  
- Způsob řazení souborů do skupiny založené na jejich velikost souboru v bajtech, soubory, které jsou menší než zadaná velikost se ignoruje.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje pět samostatné dotazy, které ukazují, jak zadávat dotazy na soubory a skupin, v závislosti na jejich velikost souboru v bajtech. Můžete snadno upravit tyto příklady na základní dotaz na některé jiné vlastnosti <xref:System.IO.FileInfo> objektu.  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 K vrácení jednoho nebo více dokončení <xref:System.IO.FileInfo> objekty, dotaz musí nejprve zkontrolujte každé z nich data zdroje a pak je můžete seřadit podle hodnoty jejich vlastnost Length. Potom může vrátit jeden nebo pořadí s největší délky. Použití <xref:System.Linq.Enumerable.First%2A> se vraťte první prvek v seznamu. Použití <xref:System.Linq.Enumerable.Take%2A> vrátit prvních n počet prvků. Zadejte sestupně umístit nejmenší prvky na začátek seznamu.  
  
 Dotaz, volá do samostatné metodě získat velikost souboru v bajtech, aby bylo možné využívat možné výjimku, která bude vyvolána v případě, kdy byl odstraněn soubor v jiném vlákně v období od <xref:System.IO.FileInfo> objekt byl vytvořen při volání funkce `GetFiles`. I přes <xref:System.IO.FileInfo> objekt již byl vytvořen, výjimce může dojít, protože <xref:System.IO.FileInfo> objekt se pokusí obnovit jeho <xref:System.IO.FileInfo.Length%2A> vlastnost pomocí aktuální velikost v bajtech při prvním přístupu k vlastnosti. Vložením této operace v bloku try-catch mimo dotazu, budeme postupovat podle pravidla vyloučení operací v dotazech, které může způsobit vedlejší účinky. Obecně platí musí být věnovat pozornost při využívání výjimky, abyste měli jistotu, že aplikace není ponechán v neznámém stavu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
