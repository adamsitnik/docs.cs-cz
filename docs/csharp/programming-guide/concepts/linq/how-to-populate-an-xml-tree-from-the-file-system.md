---
title: 'Postupy: Naplnění stromu XML ze systému souborů (C#)'
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: dc3850c943ebac8980abbff0933413538823d21d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485168"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="c4a24-102">Postupy: Naplnění stromu XML ze systému souborů (C#)</span><span class="sxs-lookup"><span data-stu-id="c4a24-102">How to: Populate an XML Tree from the File System (C#)</span></span>
<span data-ttu-id="c4a24-103">Je běžné použití užitečné stromů XML jako úložiště dat hierarchické název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="c4a24-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="c4a24-104">Můžete naplnění stromu XML s hierarchickými daty a pak ji dotazovat, transformují je a v případě potřeby ho serializovat.</span><span class="sxs-lookup"><span data-stu-id="c4a24-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="c4a24-105">V tomto scénáři použití mnoha specifické sémantiku XML, například obory názvů a chování mezer, nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="c4a24-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="c4a24-106">Místo toho používají stromu XML jako malé, v paměti, hierarchické databázi jednoho uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4a24-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a24-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4a24-107">Example</span></span>  
 <span data-ttu-id="c4a24-108">V následujícím příkladu se naplní stromu XML z místního systému souborů pomocí rekurze.</span><span class="sxs-lookup"><span data-stu-id="c4a24-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="c4a24-109">Následně se dotazuje stromu výpočtu celkové velikosti všech souborů ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="c4a24-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="c4a24-110">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="c4a24-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
