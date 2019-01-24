---
title: Serializace grafů objektů, které obsahují objekty XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: db7354598fc84c6fa3f8ec4e5b53799030459387
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569138"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="34a51-102">Serializace grafů objektů, které obsahují objekty XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="34a51-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="34a51-103">Toto téma představuje možnost serializace grafů objektů, které obsahují odkazy na objekty typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="34a51-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="34a51-104">Na zařízení tento typ serializace, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34a51-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="34a51-105">Poznámka: pouze <xref:System.Xml.Linq.XElement> třída implementuje serializace.</span><span class="sxs-lookup"><span data-stu-id="34a51-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34a51-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="34a51-106">In This Section</span></span>  
  
|<span data-ttu-id="34a51-107">Téma</span><span class="sxs-lookup"><span data-stu-id="34a51-107">Topic</span></span>|<span data-ttu-id="34a51-108">Popis</span><span class="sxs-lookup"><span data-stu-id="34a51-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="34a51-109">Postupy: Serializace pomocí třídy XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="34a51-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="34a51-110">Ukazuje, jak lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="34a51-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="34a51-111">Postupy: Serializace pomocí třídy DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="34a51-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="34a51-112">Ukazuje, jak lze serializovat pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="34a51-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34a51-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34a51-113">See also</span></span>

- [<span data-ttu-id="34a51-114">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="34a51-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
