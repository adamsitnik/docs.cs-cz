---
title: Serializace do souborů, tříd a XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: bfbb0376823159c2026140c4382f321a563d92de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711821"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="96933-102">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="96933-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="96933-103">Může serializovat stromů XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="96933-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="96933-104">Může serializovat libovolné součásti XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, na řetězec pomocí `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="96933-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="96933-105">Pokud chcete potlačit formátování při serializaci do řetězce, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="96933-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="96933-106">Výchozí chování při serializaci do souboru se má formátovat dokument (odsazení) výsledného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="96933-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="96933-107">Při odsazení, není zachována nevýznamné prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="96933-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="96933-108">K serializaci formátování, použijte jednu z přetížení z následujících metod, které nepřebírají <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="96933-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="96933-109">Pokud chcete možnost odsazení a nevýznamné mezeru ve stromové struktuře XML, použijte jednu z přetížených z následujících metod, které provede <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="96933-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="96933-110">Příklady naleznete v tématu příslušný odkaz.</span><span class="sxs-lookup"><span data-stu-id="96933-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="96933-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96933-111">See also</span></span>

- [<span data-ttu-id="96933-112">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="96933-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
