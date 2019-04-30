---
title: Zpracování mezer a významných mezer při načítání modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799330"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="9e4ef-102">Zpracování mezer a významných mezer při načítání modelu DOM</span><span class="sxs-lookup"><span data-stu-id="9e4ef-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="9e4ef-103">Při načítání dokumentu, můžete nastavit možnost zachovat mezer a vytvořit **XmlWhitespace** uzlů ve stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="9e4ef-104">Chcete-li vytvořit prázdné znaky uzly, nastavte **PreserveWhitespace** vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="9e4ef-105">Pokud je nastavena na **false**, což je výchozí, nejsou vytvořeny uzly mezer.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="9e4ef-106">Významné prázdné znaky uzly se vždy zachovají, a **XmlSignificantWhitespace** v paměti, která bude představovat tato data, bez ohledu na nastavení se vždy vytvářejí uzly **PreserveWhitespace** příznak.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="9e4ef-107">Pokud dokument je načtena z čtečky, potom nastavení z **PreserveWhitespace** příznaku vlastnost **XmlDocument** třída má vliv na vytváření **XmlWhitespace** uzly pouze tehdy, když **WhitespaceHandling** vlastnost **XmlTextReader** není nastavená na **: WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="9e4ef-108">Je hodnota **WhitespaceHandling** vlastnost čtecího zařízení, která má přednost před nastavením tohoto příznaku na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="9e4ef-109">Další informace o **XmlSignificantWhitespace**, naleznete v tématu <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="9e4ef-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4ef-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e4ef-110">See also</span></span>

- [<span data-ttu-id="9e4ef-111">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9e4ef-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
