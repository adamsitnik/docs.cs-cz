---
title: Obor výchozích názvových prostorů v jazyce C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253037"
---
# <a name="scope-of-default-namespaces-in-c"></a>Rozsah výchozích oborů názvů v jazyce C\#
Výchozí obory názvů jako reprezentované ve stromu XML nejsou v oboru pro dotazy. Pokud máte XML, které je ve výchozím oboru názvů, je stále nutné deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat ji s místním názvem, aby bylo možné použít kvalifikovaný název v dotazu.  
  
 Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů, ale dotaz je nesprávně zadán.  
  
 Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.  
  
### <a name="code"></a>Kód  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výsledek:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.  
  
 Na rozdíl od nesprávně uvedeného kódovaného příkladu je správný přístup při použití příkazu C# pro deklaraci a inicializaci <xref:System.Xml.Linq.XNamespace> objektu a jeho použití při určení <xref:System.Xml.Linq.XName> objektů. V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody <xref:System.Xml.Linq.XName> je objekt.  
  
### <a name="code"></a>Kód  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výsledek:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML)C#()](namespaces-overview-linq-to-xml.md)
