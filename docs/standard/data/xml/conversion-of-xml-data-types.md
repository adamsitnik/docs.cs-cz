---
title: Převod datových typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56b5b51848858b7f1240059ca30eb48474650b73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555125"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="1b8af-102">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="1b8af-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="1b8af-103">Většina metod součástí **XmlConvert** třída slouží k převedení dat mezi řetězci a formáty silného typu.</span><span class="sxs-lookup"><span data-stu-id="1b8af-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="1b8af-104">Metody jsou nezávislé národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="1b8af-104">Methods are locale independent.</span></span> <span data-ttu-id="1b8af-105">To znamená, že není berou v úvahu žádné nastavení národního prostředí při provádění převodu.</span><span class="sxs-lookup"><span data-stu-id="1b8af-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="1b8af-106">Čtení řetězce jako typy</span><span class="sxs-lookup"><span data-stu-id="1b8af-106">Reading String as types</span></span>  
 <span data-ttu-id="1b8af-107">Následující příklad přečte řetězce a převede jej na **data a času** typu.</span><span class="sxs-lookup"><span data-stu-id="1b8af-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="1b8af-108">Daný následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="1b8af-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1b8af-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="1b8af-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="1b8af-110">Převede řetězec na tento kód **data a času** formátu:</span><span class="sxs-lookup"><span data-stu-id="1b8af-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="1b8af-111">Psaní řetězců jako typy</span><span class="sxs-lookup"><span data-stu-id="1b8af-111">Writing Strings as types</span></span>  
 <span data-ttu-id="1b8af-112">Následující ukázkový čtení **Int32** a převede ho na řetězec.</span><span class="sxs-lookup"><span data-stu-id="1b8af-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="1b8af-113">Daný následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="1b8af-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1b8af-114">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="1b8af-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="1b8af-115">Tento kód převede **Int32** do **řetězec**:</span><span class="sxs-lookup"><span data-stu-id="1b8af-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b8af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b8af-116">See also</span></span>

- [<span data-ttu-id="1b8af-117">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b8af-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="1b8af-118">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="1b8af-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
