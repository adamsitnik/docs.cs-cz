---
title: 'Postupy: Naplnění stromu XML ze systému souborů (C#)'
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 664994dad75871a5b70f2c132df67d1658808c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705807"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a>Postupy: Naplnění stromu XML ze systému souborů (C#)
Je běžné použití užitečné stromů XML jako úložiště dat hierarchické název/hodnota. Můžete naplnění stromu XML s hierarchickými daty a pak ji dotazovat, transformují je a v případě potřeby ho serializovat. V tomto scénáři použití mnoha specifické sémantiku XML, například obory názvů a chování mezer, nejsou důležité. Místo toho používají stromu XML jako malé, v paměti, hierarchické databázi jednoho uživatele.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se naplní stromu XML z místního systému souborů pomocí rekurze. Následně se dotazuje stromu výpočtu celkové velikosti všech souborů ve stromové struktuře.  
  
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
  
 Tento příklad vytvoří výstup podobný následujícímu:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pokročilé techniky dotazování (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
