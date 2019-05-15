---
title: 'Postupy: Kombinace dotazů LINQ s regulárními výrazy (C#)'
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: 21c05b0134fda5011ecaf14f296e5a5172cf3bf5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585921"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="a0d28-102">Postupy: Kombinace dotazů LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="a0d28-102">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>
<span data-ttu-id="a0d28-103">Tento příklad ukazuje způsob použití <xref:System.Text.RegularExpressions.Regex> třídy za účelem vytvoření regulárního výrazu pro složitější porovnávání v textových řetězců.</span><span class="sxs-lookup"><span data-stu-id="a0d28-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="a0d28-104">Dotaz LINQ umožňuje snadno můžete filtrovat podle přesně soubory, které chcete hledat s regulárním výrazem a obrazce výsledky.</span><span class="sxs-lookup"><span data-stu-id="a0d28-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0d28-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0d28-105">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a   
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write   
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery   
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="a0d28-106">Všimněte si, že můžete také zadávat dotazy <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácen `RegEx` vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="a0d28-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="a0d28-107">V tomto příkladu je vytvořen pouze hodnotu jednotlivé shody ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="a0d28-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="a0d28-108">Je však také možné použít k provádění nejrůznějších filtrování, řazení a seskupování v dané kolekci LINQ.</span><span class="sxs-lookup"><span data-stu-id="a0d28-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="a0d28-109">Protože <xref:System.Text.RegularExpressions.MatchCollection> není obecná <xref:System.Collections.IEnumerable> kolekce, je nutné explicitně uvést typ rozsahu proměnných v dotazu.</span><span class="sxs-lookup"><span data-stu-id="a0d28-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0d28-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a0d28-110">Compiling the Code</span></span>  
 <span data-ttu-id="a0d28-111">Vytvoření C# projekt konzolové aplikace s `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="a0d28-111">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d28-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0d28-112">See also</span></span>

- [<span data-ttu-id="a0d28-113">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="a0d28-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="a0d28-114">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="a0d28-114">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
